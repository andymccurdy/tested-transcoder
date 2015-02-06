# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # ubuntu 14.04 64bit image
  config.vm.box = "ubuntu/trusty64"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  config.vm.provision "shell", inline: <<-SHELL
    add-apt-repository -y ppa:stebbins/handbrake-releases
    add-apt-repository -y ppa:mc3man/trusty-media
    apt-get update
    apt-get install -y make git mkvtoolnix handbrake-cli mplayer ffmpeg mp4v2-utils linux-headers-generic build-essential dkms

    git clone https://github.com/donmelton/video-transcoding-scripts
    mv video-transcoding-scripts/*.sh /usr/local/bin/
    rm -rf video-transcoding-scripts
  SHELL


end
