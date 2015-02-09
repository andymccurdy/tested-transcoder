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
