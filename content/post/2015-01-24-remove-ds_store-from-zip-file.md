+++
title = "Remove .DS_Store from ZIP Files"
date = "2015-01-24T18:50:20-07:00"
+++
At work this week, I had to download a bunch of compressed XML files, delete some duplicate files contained therein, recompress the files, and then reupload them to a server. The problem, however, is that whenever I tried to upload the files, I got a strange server error. After some trial and error, and some deep examination, I found that the hidden file &#8220;.DS\_Store&#8221; was causing the server error issue. When I removed the hidden &#8220;.DS\_Store&#8221; file, I had no more issues.

If you're a Mac user, you've undoubtedly noticed these strange files that seem to creep into every directory. They've plagued the operating system for years, and there's still not a super great solution for removing them. And the files don't just stay on your machine. Ever plugged in a USB flash drive to take over to a Windows machine? These obnoxious files have most certainly hopped on for a ride. They're nothing more than metadata (data about data), but they've never been an issue for me until now.

So I navigated through the compressed folders again, deleted the hidden files, and then thought I was set. Upon recompressing the files once more and trying to upload them, I was still presented with the same error. Guess what happened when the folders were compressed again? Yep. The infamous .DS_Store file had once again shown up.

So how do you remove these files in a compressed directory? Unzipping the files to remove them doesn't work, as they'll just show up again as soon as you re-zip the file. Well, I've had to resort to the command line. Using the following command in the terminal, I was successfully able to remove the annoyance quickly.

<span class="smallcode">zip -r mynewzipfile.zip wherethefilesarecomingfrom -x "*.DS_Store"</span>

Just to break down the above command:  
<span class="smallcode">zip</span> &#8211; The terminal command  
<span class="smallcode">-r</span> &#8211; &#8220;Recursive.&#8221; This means to select all files and subfolders under the directory  
<span class="smallcode">mynewzipfile.zip</span> &#8211; Name this whatever you'd like the new ZIP file to be called  
<span class="smallcode">wherethefilesarecomingfrom</span> &#8211; The directory that contains the files to be zipped  
<span class="smallcode">-x</span> &#8211; &#8220;Exclude&#8221; flag.  
<span class="smallcode">"*.DS_Store"</span> &#8211; Selects all files that are named &#8220;.DS_Store&#8221;

Your new zip file will be created WITHOUT the .DS_Store file. Tah-dah!

Upon doing a quick search on the internet, I found the following program called <a href="http://asepsis.binaryage.com" target="_blank">Asepsis</a>. I haven't given it a try, but apparently it prevents the creation of any .DS_Store files. Might be worth giving it a try.