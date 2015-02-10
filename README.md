# tested-transcoder

## Prerequisites

* Virtualbox
* Vagrant

## Install the VM

1. Clone this repo
2. `vagrant up`
3. `vagrant ssh`


## Notes

There are three interesting paths inside the VM:

* `/home/vagrant/input` - The path being watched for new videos to be transcoded
* `/home/vagrant/output` - The path where transcoded videos are saved to
* `/home/vagrant/completed-originals` - The path where original video from
input is moved to after transcoding has completed.

It is expected that these paths will likely be network mounts from the host OS.
This could be accomplished in the Vagrantfile using Vagrant's synced folders or
by some other mechanism.


## Vagrant Synced Folters

It's quite easy to setup synced folders between your host OS and the Ubuntu
system Vagrant is provisioning. This example mounts the "/Users/andy/MyMovies"
directory on my Mac to "/home/vagrant/input" on the Ubuntu OS. Then when I copy
a file to /Users/andy/MyMovies on my Mac, the transcode process automatically
should start.

`config.vm.synced_folder "/Users/andy/MyMovies", "/home/vagrant/input"`

This line should be placed into the Vagrantfile just above the `end`.
