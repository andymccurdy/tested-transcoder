# tested-transcoder

## Prerequisites

* Virtualbox
* Vagrant

## Install the VM

1. Clone this repo
2. `vagrant up`
3. `vagrant ssh`
4. (optional) Install the VM on another machine, e.g., FreeNas
5. Create a folder on the host machine where you will copy source videos to
and collect transcoded videos from.
6. Use the VirtualBox UI on the host machine to share this new folder with the VM.
    1. Click the VM named "Tested Transcoder"
    2. Click shared folders
    3. Click the add button
    4. Find the folder you created in the "Folder Path" field
    5. The "Folder Name" *must* be named "transcoder"
    6. Check the "Make Permanent" checkbox. All the other checkboxes should be unchecked.
    7. Click OK and OK again to return to the VM selection screen.
7. Wait about a minute. Input, Output and Completed Input folders should be created in the folder.
