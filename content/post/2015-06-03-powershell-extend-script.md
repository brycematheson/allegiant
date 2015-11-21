+++
title = "VMware Disk Extend Powershell Script"
date = "2015-06-03T18:50:20-07:00"
+++
About a month ago, I began working at Intermountain Healthcare, here in Utah, as a Systems Administrator. We have a bunch of monitoring software, one of which is called &#8220;Spectrum&#8221;. It searches for hardware errors or any other faults and then reports them to us. One of the most common reports that we find is that &#8220;C: 90% usage&#8221;, or something similar. Because the majority of the servers that we run are virtual, with a thin disk setup, they have relatively small drives (some starting as small as 25GB). As applications are installed or the demands of the business unit increase, we find that these drives fill up rather quickly. Currently, the process to extend these drives is to log into vConsole (vSphere Client), find the drive, edit the settings, provision additional disk space, remote into the virtual machine, open diskpart.exe, rescan the drive, and then extend it.

Now, that's fine if you only have a couple of drives to extend each day. But with nearly 3500 servers that we're in charge of, we get quite a few, and it becomes rather monotonous. Hence, I began playing with powershell and wrote a simple script that both provisions additional disk space for you, as well as extends the drive in the Guest Operating System.

The following script requires the VMWare PowerCLI. I prefer to use the PowerCLI, but you can also use the Snap-in and run it from Powershell directly. This has been tested to work on Windows Server 2003, 2008, and 2012. Because Windows 2003 doesn't have the capability to extend a virtual disk from the OS natively, we use Dell's 3rd party software &#8220;extpart.exe&#8221; (extend partition).

You'll have to modify the script below to your needs by adding the VM host servers you want to connect to (indicated by &#8220;server1&#8221;, etc), as well as change the locations below for where to check for extpart.exe, as well as where to copy the program should it be found missing.

Cheers!

~~~powershell
#Import the PowerCLI module
#Add-PSSnapin VMware.VimAutomation.Core
Set-PowerCLIConfiguration -DisplayDeprecationWarnings $false -InvalidCertificateAction Ignore -Confirm:$false

function getDisk {
    $disk = Read-Host "Which disk would you like to extend (i.e., '1')?"
    Return $disk
}

function getDiskSize {
    $diskSize = Read-Host "Enter new (total) drive size (in GB)?"
    Return $diskSize
}

function setVMSize($vm, $disk, $diskSize) {
    Get-HardDisk -vm $vm | where {$_.Name -eq "$disk"} | Set-HardDisk -CapacityGB $diskSize -ResizeGuestPartition -confirm:$false -ErrorAction:SilentlyContinue
}

# Connect to vConsole servers
$authenticated = $false;
while (-not $authenticated) {
    Try {
        Connect-VIServer -Server server1,server2,server3 -ErrorAction Stop | Select-Object -Property Name,IsConnected
        $authenticated = $true
    }
    Catch {
        Write-Host "Invalid username or password." -foreground "red"
    }
}

# Check to make sure that the user inputs a valid VM
$validVM = $false
while (-not $validVM) {
    $vm = Read-Host "Enter VM name"
    Try {
        Get-VM -Name $vm | Select-Object -Property Name
        $validVM = $true
    }
    Catch {
        Write-Host "Invalid VM name. Try again." -foreground "red"
    }
}

# Get drive letter mappings and store them in the $diskArray array. Data from this
# array can be accessed like so: $diskArray[0].DiskName, or .DriveLetter, or .DiskSize
$diskArray = @()

if ($vm) {
    $VmView = Get-View -ViewType VirtualMachine -Filter @{"Name" = $vm}
    foreach ($VirtualSCSIController in ($VMView.Config.Hardware.Device | where {$_.DeviceInfo.Label -match "SCSI Controller"})) {
        foreach ($VirtualDiskDevice in ($VMView.Config.Hardware.Device | where {$_.ControllerKey -eq $VirtualSCSIController.Key})) {
            $VirtualDisk = "" | Select DiskName, DiskSize, DriveLetter
            $VirtualDisk.DiskName = $VirtualDiskDevice.DeviceInfo.Label
            $VirtualDisk.DiskSize = $VirtualDiskDevice.CapacityInKB * 1KB / 1GB

            $LogicalDisks = @()
            # Look up path for this disk using WMI.
            $thisVirtualDisk = get-wmiobject -class "Win32_DiskDrive" -namespace "root\CIMV2" -computername $vm | where {$_.SCSIBus -eq $VirtualSCSIController.BusNumber -and $_.SCSITargetID -eq $VirtualDiskDevice.UnitNumber}
            # Look up partition using WMI.
            $Disk2Part = Get-WmiObject Win32_DiskDriveToDiskPartition -computername $vm | Where {$_.Antecedent -eq $thisVirtualDisk.__Path}
            foreach ($thisPartition in $Disk2Part) {
                #Look up logical drives for that partition using WMI.
                $Part2Log = Get-WmiObject -Class Win32_LogicalDiskToPartition -computername $vm | Where {$_.Antecedent -eq $thisPartition.Dependent}
                foreach ($thisLogical in $Part2Log) {
                    if ($thisLogical.Dependent -match "[A-Z]:") {
                        $LogicalDisks += $matches[0]
                    }
                }
            }
            $VirtualDisk.DriveLetter = $LogicalDisks
            $diskArray += $VirtualDisk
            Write-Output $VirtualDisk
        }
    }
}

# Check which OS version -- If Server 2003, run extpart. Run diskpart for all others.
If ((Get-VMGuest $vm | Select-Object -Property OSFullName) -like '*2003*') {
    $disk = getDisk
    $diskSize = getDiskSize
    setVMSize $vm $diskArray[$disk - 1].DiskName $diskSize
        # If extpart exists, do nothing. Otherwise, copy to C:\UTILS folder on VM.
        if (Test-Path "\\$vm\c$\UTILS\extpart.exe"){
            # do nothing
        } else {
            Copy-Item -Path "S:\SA\PostInstallDoNotModify\Installs\UTILS\extpart.exe" -Destination "\\$vm\c$\UTILS"
            Write-Host "Successfully copied 'extpart.exe' to UTILS folder." -foreground "green"
       }
    $driveLetter = $diskArray[$disk - 1].DriveLetter
    $sizeInMB = ((($diskSize)-($diskArray[$disk - 1].DiskSize))*1024)
    $script = "C:\UTILS\extpart.exe $driveLetter $sizeInMB"
    Invoke-VMScript -vm $vm -ScriptText $script -ScriptType BAT
} else {
    $disk = getDisk
    $diskSize = getDiskSize
    $driveLetter = $diskArray[$disk - 1].DriveLetter
    setVMSize $vm $diskArray[$disk - 1].DiskName $diskSize
    $script = "echo select volume = $driveLetter > c:\diskpart.txt && echo rescan >> c:\diskpart.txt && echo extend >> c:\diskpart.txt && diskpart.exe /s c:\diskpart.txt"
    Invoke-VMScript -vm $vm -ScriptText $script -ScriptType BAT
}
~~~