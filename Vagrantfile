# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/disco64"
  config.vm.network "forwarded_port", guest: 8888, host: 8888, host_ip: "127.0.0.1"
  config.vm.synced_folder "./assignments", "/assignments"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -yq --no-install-recommends \
      git \
      python3 \
      python3-pip
    apt-get clean
    echo "cd /assignments" >> "~/.bashrc"
  SHELL

  config.vm.provision "shell", inline: "pip3 install -r /assignments/requirements.txt", run: 'always'
end
