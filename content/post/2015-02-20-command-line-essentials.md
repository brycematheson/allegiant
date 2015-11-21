+++
title = "Command Line Essentials"
date = "2015-02-20T18:50:20-07:00"
+++

It wasn't too long ago that I was terrified of the terminal. It's pretty daunting to be staring at a blank screen with a blinking cursor taunting you. Want to know something? It's not as scary as you might think. It would take years to master the command line, so don't expect to know everything all at once. Everyday, try and find little ways to slowly blend the terminal with basic tasks. Slowly, you'll find that it makes a lot of things easier.

## Terminology

You may have heard words such as &#8220;terminal&#8221;, &#8220;command line&#8221;, &#8220;shell&#8221;, &#8220;bash&#8221;, etc. There are slight differences, but generally, they all refer to the same thing.

## Terminal vs iTerm

&#8216;iTerm' is a terminal replacement. It's simply a program that adds some features for developers and advanced users such as split panes, paste history, and a plethora of others. If you don't need any of these, you can use the basic terminal just as well. If you're looking for additional functionality, this might be worth looking into.

Honestly, I tried iTerm and didn't care too much for it. I prefer <a href="http://totalterminal.binaryage.com/" target="_blank">TotalTerminal</a>. I don't have a bunch of needs for extra fancy features, but one thing I do love is the &#8220;visor&#8221; functionality. From anywhere on my computer, I can have a terminal window slide down from the top of my screen, simply by pressing a keyboard shortcut. This is much easier than navigating to Finder, then Applications, then Utilities, then Terminal. Or even faster than searching for it through Spotlight. Many people use the standard  <span class="smallcode">Command/Ctrl + ~</span> shortcut, but I've customized mine to <span class="smallcode">Control + Control</span>.

Another nifty feature is being able to have multiple terminal windows running different processes. I generally have a Jekyll or Grunt server running in one window, and then I use the other window for navigating through folders or committing changes on Git. It works similar to using tabs in Chrome or any other browser.

## Basic Commands

Let's get started. Go ahead and open up a terminal window and play with the following commands. Each command should be entered on a single line, and then followed by the <span class="smallcode">[return/enter]</span> key.

<span class="smallcode">pwd</span> &#8211; stands for &#8220;print working directory&#8221;. It lists the folder that you're currently in (i.e. /Users/yourusername/Documents)

<span class="smallcode">cd</span> &#8211; stands for &#8220;change directory&#8221;. This lets you move in and out of folders. For example, if you're in the &#8220;Documents&#8221; directory and want to move to another directory underneath named &#8220;School&#8221;, you would type <span class="smallcode">cd School</span>.

<span class="smallcode">cd ..</span> &#8211; Move &#8220;back&#8221; or &#8220;up&#8221; a folder. In our previous example, this would move you out of the &#8220;School&#8221; directory and back into the &#8220;Documents&#8221; folder.

<span class="smallcode">cd ~</span> &#8211; Takes you back to your home directory. Let's say you're deep in a folder structure (i.e. /Users/yourusername/Documents/School/Senior/Thesis). Rather than having to type <span class="smallcode">cd ..</span> a billion times, you could type <span class="smallcode">cd ~</span> to take you back to &#8220;/Users/yourusername&#8221;.

<span class="smallcode">open .</span> &#8211; Opens the current working directory in finder. I use this one ALL the time and love it.

<span class="smallcode">clear</span> &#8211; Clears the screen of all text. Sometimes the output of all previous commands can make me claustrophobic. This gives me a fresh, blank screen.

<span class="smallcode">rm [filename]</span> &#8211; Deletes a file.

<span class="smallcode">mkdir [directoryname]</span> &#8211; Stands for &#8220;make directory&#8221;. Creates a new folder.

<span class="smallcode">ls</span> &#8211; Stands for &#8220;list&#8221;. Shows a listing of all the files/folders in a directory. Often, I find myself adding an <span class="smallcode">-al</span> flag. <span class="smallcode">-a</span> shows &#8220;all files&#8221; (hidden files included), and <span class="smallcode">-l</span> shows a long listing of files, rather than in a three-column short listing. This to me, is easier to read. You can combine the two flags together with the ls command by typing <span class="smallcode">ls -al</span>.

<span class="smallcode">sudo [command]</span> &#8211; Stands for &#8220;super user do&#8221;. Sometimes you need elevated privileges to run a certain command. Typing <span class="smallcode">sudo</span> before the command will prompt for your password, and will then run the command. Be careful when using this command. If you don't know what you're doing, you can make some unwanted changes. If at all possible, run the command first *without* sudo, and only add it in if needed.

<span class="smallcode">control + c</span> &#8211; Cancels a current process. For example, if you're running a script, you can kill (cancel) it.

<span class="smallcode">[Up arrow]</span> &#8211; You can see a list of all the previous commands you've entered by pressing the up arrow key. This saves time rather than having to type in a command over and over again.

<span class="smallcode">[tab]</span> &#8211; Autocomplete. Let's say I have a long folder name such &#8220;Discertation&#8221;. Start typing the first few letters of the file/folder to distinguish it from other files, and then press the &#8220;tab&#8221; key. It will autocomplete the filename for you.

## Give it a try!

Well, there are a few commands to get you started and make you just dangerous enough. Practice makes perfect! I use most all of these commands on a daily basis, but there are thousands of additional commands that you can learn. Baby steps.

## Comments

Did I miss any of your favorites? Let me know, and I'll list them here.