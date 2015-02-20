# tested-transcoder   --- THIS IS A BETA RELEASE -- Please leave feedback on Github or at http://tested.com/forums

Thanks for helping us test this out! We'll have more refined instrucitons once we're sure the transcoder is ready for release.

This is a vagrant script that creates a Virtualbox virtual machine that serves as a black box for transcoding and repackaging Blu-rays and DVDs ripped using MakeMKV into iTunes quality video files suitable for streaming using Plex or XBMC. It uses Don Melton's video transcoder scripts (https://github.com/donmelton/video-transcoding-scripts) to transcode individual files, but handles a lot of the tedious stuff involved in movie transcoding for you, including adding all audio tracks, selecting the proper subtitle track for non-English dialogue in English language films (Think Greedo's conversation with Han in Star Wars), handling the movie crop, etc. 

To rip discs, first use MakeMKV to rip only the movie, audio tracks, and subtitles you'll need. I typically tell MakeMKV to grab all the English language subtitles and audio tracks, which is a generally a good strategy. The process can long time, depending on your computer. 

## Prerequisites

* Virtualbox - https://www.virtualbox.org/
* Vagrant - https://www.vagrantup.com/
* Git - http://git-scm.com/downloads
* MakeMKV - http://www.makemkv.com
* 

## Install the VM

1. Install all the prerequisites
2. Navigate to your Documents folder in the terminal/command line and type 'git clone https://github.com/andymccurdy/tested-transcoder/'
3. Switch to the tested-transcoder folder and run `vagrant up`
4. (optional) After the script runs and your VM is created, stop it in vagrant using 'vagrant halt'. Open the VM in Virtualbox. 
5. Go to the VM and select settings while it isn't running. Adjust CPU and memory settings to suit. 
6. Create a folder on the host machine where you will copy source videos to
and collect transcoded videos from. 
7. Use the VirtualBox UI on the host machine to share this new folder with the VM.
    1. Click the VM named "Tested Transcoder"
    2. Click shared folders
    3. Click the add button
    4. Find the folder you created in the "Folder Path" field
    5. The "Folder Name" *must* be named "transcoder"
    6. Check the "Make Permanent" checkbox. All the other checkboxes should be unchecked. ("Make Permanent" may or may not be visible)
    7. Click OK and OK again to return to the VM selection screen.
8. Wait about a minute. Input, Output and Completed Input folders should be created in the folder.
9. Once the VM is running, starting your encodes is as easy as dragging a video from MakeMKV into the "Input" folder.
10. When the encode is in progress, you can check in on its progress by looking in the work folder and reading the end of the log. 
