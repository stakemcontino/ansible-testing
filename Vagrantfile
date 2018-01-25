# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.ssh.forward_agent = true

  config.vm.provision "shell", inline: <<-SHELL
    sudo yum install epel-release python-setuptools python-devel python-tools gcc git vim-enhanced docker -y 
    sudo systemctl start docker
    sudo easy_install pip
    sudo pip install ansible docker molecule
  SHELL
end
