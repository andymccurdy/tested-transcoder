# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'yaml'

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

settings = YAML.load_file 'vagrant_config.txt'

Vagrant.configure(2) do |config|
  # ubuntu 14.04 64bit image
  config.vm.box = "ubuntu/trusty64"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    vb.name = settings['vm_name']
    vb.memory = settings['vm_memory']
    vb.cpus = settings['vm_cpus']
  end

  # bootstrap the ubuntu machine
  config.vm.provision "shell", inline: <<-SHELL
    add-apt-repository -y ppa:stebbins/handbrake-releases
    add-apt-repository -y ppa:mc3man/trusty-media
    apt-get update
    apt-get install -y make git mkvtoolnix handbrake-cli mplayer ffmpeg mp4v2-utils linux-headers-generic build-essential dkms virtualbox-guest-utils virtualbox-guest-dkms supervisor

    git clone https://github.com/donmelton/video-transcoding-scripts
    mv video-transcoding-scripts/*.sh /usr/local/bin/
    rm -rf video-transcoding-scripts

    # transcoder root. this is where the transcoder directory will be mounted
    mkdir -p /media/transcoder

    # install the transcoder's supervisor config file and reload supervisor
    cp /vagrant/supervisor-config.conf /etc/supervisor/conf.d/transcoder.conf
    cp /vagrant/transcoder.py /usr/local/bin
    chmod +x /usr/local/bin/transcoder.py
    supervisorctl reload
  SHELL

  # copy the transcoder.py script in to place. always run this provisioner to
  # get the most recent copy of the script.
  config.vm.provision "shell", run: "always", inline: <<-SHELL
    cp /vagrant/transcoder.py /usr/local/bin
    chmod +x /usr/local/bin/transcoder.py
    supervisorctl reload
  SHELL

  config.vm.synced_folder settings['directory'], "/media/transcoder"
end
