#tested-transcoder
##--- THIS IS A BETA RELEASE --
Please post feedback on github or at http://www.tested.com/forums/general-discussion/495076-transcoder-feedback/

Thanks for helping us test this out! We'll have more refined instructions once we're sure the transcoder is ready for release.

This is a vagrant script that creates a Virtualbox virtual machine that serves as a black box for transcoding and repackaging Blu-rays and DVDs ripped using MakeMKV into iTunes quality video files suitable for streaming using Plex or XBMC. It uses Don Melton's video transcoder scripts (https://github.com/donmelton/video-transcoding-scripts) to transcode individual files, but handles a lot of the tedious stuff involved in movie transcoding for you, including adding all audio tracks, selecting the proper subtitle track for non-English dialogue in English language films (Think Greedo's conversation with Han in Star Wars), handling the movie crop, etc. 

To rip discs, first use MakeMKV to rip only the movie, audio tracks, and subtitles you want. The title with the most chapters, and largest size is typically the one you want. I typically tell MakeMKV to grab all the English language subtitles and audio tracks, which is a generally a good strategy. You can set this as the default in View > Preferences > Language > Preferred Language. The process may take a long time, depending on your computer and the resources you give the black box.

## Prerequisites

* Virtualbox - https://www.virtualbox.org/wiki/Downloads
* Vagrant - http://www.vagrantup.com/downloads
* Git - http://git-scm.com/downloads
* MakeMKV - http://www.makemkv.com/download/

## Installation Instructions

1. Install the prerequisites.
2. Verify that CPU Virtualization is turned on in your BIOS. (See below for a simple test)
3. Create a folder on the host machine where you will copy source videos to and collect transcoded videos from.
4. Navigate to your Documents folder in the terminal/command line and type `git clone https://github.com/andymccurdy/tested-transcoder/`.
5. Go to the 'tested-transcoder' folder and copy `vagrant_config_example.txt` to `vagrant_config.txt`.
6. Edit the settings in `vagrant_config.txt` in your favorite text editor.
7. Open the command line / terminal and switch to the `tested-transcoder` folder.
8. Run `vagrant up`.
9. Wait for 'input', 'output', 'work', and 'completed-originals' folders to be created in the folder on your host machine.

## Usage

1. While the VM is running, starting your encodes is as easy as dragging a video from MakeMKV into the 'input' folder.
2. When the encode is in progress, you can check in on its progress by looking at the end of the log in the 'work' folder.
3. When the encodes are complete, the new, better compressed video will be in the 'output' folder and the original source MKV will be in the 'completed-originals' folder. After you've confirmed subtitles and audio tracks are correct, you can safely delete the large original file.
4. Enjoy your new, much smaller MKV in your favorite media player.

---
#### Verify CPU Virtualization is on
There may be better ways to do this, but this seems to be a reasonable way.

1. Open VitrualBox Manager.
2. Select New
3. Name: test
4. Next.
5. Next.
5. Do not add a virtual hard drive.
6. Create.
7. Click on the test VM and look under System for "Acceleration: VT-x/AMD-V, Nested Paging."
8. If you see this message you should be good, otherwise you will need to Google how to turn it on for your specific motherboard.
9. Once you are finished delete the test VM. (Right Click > Remove)
