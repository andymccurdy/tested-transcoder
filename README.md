# tested-transcoder   --- THIS IS A BETA RELEASE -- Please leave feedback on Github or at http://www.tested.com/forums/general-discussion/495076-transcoder-feedback/

Thanks for helping us test this out! We'll have more refined instrucitons once we're sure the transcoder is ready for release.

This is a vagrant script that creates a Virtualbox virtual machine that serves as a black box for transcoding and repackaging Blu-rays and DVDs ripped using MakeMKV into iTunes quality video files suitable for streaming using Plex or XBMC. It uses Don Melton's video transcoder scripts (https://github.com/donmelton/video-transcoding-scripts) to transcode individual files, but handles a lot of the tedious stuff involved in movie transcoding for you, including adding all audio tracks, selecting the proper subtitle track for non-English dialogue in English language films (Think Greedo's conversation with Han in Star Wars), handling the movie crop, etc. 

To rip discs, first use MakeMKV to rip only the movie, audio tracks, and subtitles you'll need. I typically tell MakeMKV to grab all the English language subtitles and audio tracks. The process can take a long time, depending on your computer. (For reference, anything faster than 10fps is pretty good). 

If you need to log into the console on the VM, the username/password is vagrant/vagrant. Once you've configured anything, the VM shouldn't need access to the network.

## Prerequisites

* Virtualbox - https://www.virtualbox.org/
* Vagrant - https://www.vagrantup.com/
* Git - http://git-scm.com/downloads
* MakeMKV - http://www.makemkv.com
* 

## Install the VM

1. Install all the prerequisites. 
2. Rebooting is probably a good idea, especially on Windows.
2. Navigate to your Documents folder in the terminal/command line and type 'git clone https://github.com/andymccurdy/tested-transcoder/'
3. Switch to the tested-transcoder folder and run `vagrant up`
4. (optional) After the script runs and your VM is created, stop it in vagrant using 'vagrant halt'. Open the VM in Virtualbox. If the VM fails to start, rebooting usually fixes the problem.
5. Go to the VM and select settings while it isn't running. Adjust CPU and memory settings to suit. 
6. Create a folder on the host machine where you will copy source videos to
and collect transcoded videos from. 
7. Use the VirtualBox UI on the host machine to share this new folder with the VM.
    a. Click the VM named "Tested Transcoder"
    b. Click shared folders
    c. Click the add button
    d. Find the folder you created in the "Folder Path" field
    e. The "Folder Name" *must* be named "transcoder"
    f. Check the "Make Permanent" checkbox. All the other checkboxes should be unchecked. ("Make Permanent" may or may not be visible)
    7. Click OK and OK again to return to the VM selection screen.
8. Wait about a minute. Input, Output and Completed Input folders should be created in the folder.
9. Once the VM is running, starting your encodes is as easy as dragging a video from MakeMKV into the "Input" folder.
10. When the encode is in progress, you can check in on its progress by looking in the work folder and reading the end of the log. 
11. When the encodes are complete, the new, better compressed video will be in the Output folder and the original source MKV will be in the completed-originals folder. After you've confirmed subtitles and audio tracks are correct, you can safely delete the large original file.
12. Enjoy your new, much smaller MKV in Plex or whatever eles you like. 
13. Please post feedback at http://www.tested.com/forums/general-discussion/495076-transcoder-feedback/
