+++
title = "Understanding RAID"
date = "2014-07-16T18:50:20-07:00"
+++
Although this is changing with the advent of solid-state drives, most hard drives are mechanical, which means they are often the first part of a standard computer system to fail. Data is everything these days, and its up to you to protect it. But in the case of a drive failing, you have no excuse for not having a backup with the ease of RAID.

Instead of waiting for a hard drive to fail, an easier approach can be taken. Through using a technology known as RAID (Redundant Array of Independent Drives), a system of hard drives based on redundancy can be achieved which uses multiple hard drives for increased reliability and performance. You can implement RAID through either software or hardware, however in this article, I’m only going to focus on hardware-based RAID. Software-based RAID is implemented at the operating system level and/or with third-party software, while hardware-based RAID requires a special controller card that is either on the motherboard, as an added-in daughter card, or on the array that holds the RAID drives.

Interesting tidbit: RAID used to stand for “Redundant Array of Inexpensive Disks.”

Originally there were five standard RAID configurations (called levels), but several additional levels have since been developed. These additional levels include “nested” levels and nonstandard levels that are proprietary to specific vendors. Nested RAIDs are usually described by combining the numbers indicating the RAID levels with a “+” between the numbers, such as ‘RAID Level 0+1′. While there are other levels of RAID, such as 2, 3, 4, and 6, I will only be discussing the most common in this article.

The most common levels of RAID are as follows:

RAID Level 0 (striped disk array without fault tolerance): RAID 0 technology is based on striping. “Striping” takes the data written to the hard drive and partitions the storage space of each hard drive into smaller sections (stripes), which can be as small as 512 bytes or as large as several megabytes. Data written to the stripes is alternated across each of the drives, as shown in the diagram.

<img src="/img/post_images/raid1.png" alt="RAID" />

Although RAID Level 0 uses multiple drives, it is not fault tolerant, which means that if one of the drive fails, all of the data on that drive is lost.

RAID Level 1 (mirroring): RAID Level 1 uses disk mirroring. Disk mirroring involves connecting multiple drives in the computer (or server) to the same disk controller card. When data has been requested to write data to the drive, the controller sends that same request to each drive. The same happens for a read request: the data is read twice, once from each drive. By “mirroring” the read/write actions on the primary drive, all the other drives become identical duplicates. If the primary hard drive fails, the other drives take over immediately, without losing any data. This is shown in the diagram below.

<img src="/img/post_images/raid2.png" alt="RAID" />

RAID 5 (independent disks with distributed parity): RAID Level 5 distributes parity data (a type of error checking) across all drives, instead of using a separate hard drive to hold the parity error-checking information. Data is always stored on one drive, while its parity information is stored on another drive, as you can see from the diagram below. Distributing parity across other disks simply provides a user with an additional layer of protection from data loss.

<img src="/img/post_images/raid3.png" alt="RAID" />

RAID 0 + 1 (high data transfer): RAID 0+1 is a nested-level RAID. It acts as a mirrored array whose segments are RAID 0 arrays. RAID 0+1 can achieve high data transfer rates because there are multiple strip segments. RAID 0+1 is shown below. With nested RAIDs, the elements can either be individual disks, or entire RAIDs. This is my preferred RAID configuration, as it provides redundancy for protection in case one of the drives fails, but it also increase read/write input/output. The only downside to this configuration is that you have to purchase four hard drives as a minimum. Start getting into solid-state drives, and you’re easily looking at $600.

<img src="/img/post_images/raid4.png" alt="RAID" />

<table>
  <tr>
    <th style="text-align: center;">
      Level
    </th>
    
    <th style="text-align: center;">
      Description
    </th>
    
    <th style="text-align: center;">
      Minimum # of drives needed
    </th>
    
    <th style="text-align: center;">
      Typical Usage
    </th>
    
    <th style="text-align: center;">
      Advantages
    </th>
    
    <th style="text-align: center;">
      Disadvantages
    </th>
  </tr>
  
  <tr>
    <td>
      RAID 0
    </td>
    
    <td>
      Â Uses a striped disk array so that data is broken down into blocks and each block is written to a separate drive.
    </td>
    
    <td>
      2
    </td>
    
    <td>
      Video Production/Editing
    </td>
    
    <td>
      Simple design and easy to implement
    </td>
    
    <td>
      Not fault tolerant
    </td>
  </tr>
  
  <tr>
    <td>
      RAID 1
    </td>
    
    <td>
      Data is written twice to separate drives.
    </td>
    
    <td>
      2
    </td>
    
    <td>
      Financial
    </td>
    
    <td>
      Easiest RAID to implement
    </td>
    
    <td>
      Can slow down system if RAID controlling software is used instead of hardware
    </td>
  </tr>
  
  <tr>
    <td>
      RAID 5
    </td>
    
    <td>
      Â Each entire data block is written on a data disk and parity for blocks in the same rank is generated and recorded on a separate disk.
    </td>
    
    <td>
      3
    </td>
    
    <td>
      Â Databases
    </td>
    
    <td>
      Most versatile RAID
    </td>
    
    <td>
      Can be difficult to rebuild in the event that a disk fails
    </td>
  </tr>
  
  <tr>
    <td>
      RAID 0+1
    </td>
    
    <td>
      A mirrored array whose segments are RAID 0 arrays
    </td>
    
    <td>
      4
    </td>
    
    <td>
      Imaging Applications
    </td>
    
    <td>
      High input/output rates
    </td>
    
    <td>
      Expensive
    </td>
  </tr>
</table>

&nbsp;