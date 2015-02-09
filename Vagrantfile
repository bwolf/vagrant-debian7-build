# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/debian-7.4"
  config.vm.box_check_update = false
  config.vm.network "forwarded_port", guest: 22, host: 22222
#  config.vm.network "private_network", ip: "192.168.33.10"
  config.ssh.forward_agent = true
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  $script = <<SCRIPT
printf "\n**** Bringing system up to date ****\n\n"
sudo apt-get update
sudo apt-get -y upgrade
printf "\n**** Installing build-essentials ****\n\n"
sudo apt-get -y install build-essential git subversion
SCRIPT

  config.vm.provision "shell", inline: $script
 end
