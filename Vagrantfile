# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/disco64"
  config.vm.network "forwarded_port", guest: 8888, host: 8888, host_ip: "127.0.0.1"
  config.vm.synced_folder "./assignments", "/home/vagrant/assignments"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
  end

  # From: https://stefanwrobel.com/how-to-make-vagrant-performance-not-suck
  # This uses 1/4 of your system memory for VirtualBox
  config.vm.provider "virtualbox" do |v|
    host = RbConfig::CONFIG['host_os']

    # Give VM 1/4 system memory
    if host =~ /darwin/
      # sysctl returns Bytes and we need to convert to MB
      mem = `sysctl -n hw.memsize`.to_i / 1024
    elsif host =~ /linux/
      # meminfo shows KB and we need to convert to MB
      mem = `grep 'MemTotal' /proc/meminfo | sed -e 's/MemTotal://' -e 's/ kB//'`.to_i
    elsif host =~ /mswin|mingw|cygwin/
      # Windows code via https://github.com/rdsubhas/vagrant-faster
      mem = `wmic computersystem Get TotalPhysicalMemory`.split[1].to_i / 1024
    end

    mem = mem / 1024 / 4
    v.customize ["modifyvm", :id, "--memory", mem]
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade -yq
    apt-get install -yq --no-install-recommends \
      git \
      python3 \
      python3-pip
    apt-get clean
    cd /home/vagrant
    mkdir .jupyter
    echo "c.NotebookApp.ip = '*'" > .jupyter/jupyter_notebook_config.py
  SHELL

  config.vm.provision "shell", inline: "pip3 install setuptools wheel", run: 'always'
  config.vm.provision "shell", inline: "pip3 install -r /home/vagrant/assignments/requirements.txt", run: 'always'
end
