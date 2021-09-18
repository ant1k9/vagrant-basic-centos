# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/8"

  config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
  config.vm.network "forwarded_port", guest: 443, host: 8443, auto_correct: true

  config.vm.synced_folder ".", "/home/vagrant", type: "rsync",
    rsync__exclude: ".git/"

  config.vm.provision "shell", inline: <<-SHELL
    yum update -y
    yum install -y \
      curl telnet wget \
      vim \
      git
      # gcc gcc-c++ make cmake
      # python3 python3-pip
      # golang
    echo 'alias python="python3"' >> /home/vagrant/.bashrc
  SHELL
end
