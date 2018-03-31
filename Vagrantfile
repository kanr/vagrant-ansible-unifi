# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/jessie64"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 8443, host: 8443
  config.vm.network "private_network", ip: "192.168.33.12"
  config.vm.network "public_network"

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.name = "unifi"
     vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  # Enable provisioning with a shell script.
 config.vm.provision "shell", inline: <<-SHELL
    apt-get install -y software-properties-common python-software-properties
 SHELL

#  config.vm.provision "shell", inline: <<-SHELL
#      add-apt-repository ppa:openjdk-r/ppa -y
#      apt-get update
#      echo "\n----- Installing Java 8 ------\n"
#      apt-get -y install openjdk-8-jre
#    SHELL

#   config.vm.provision "shell", inline: <<-SHELL
#     echo 'deb http://www.ubnt.com/downloads/unifi/debian stable ubiquiti' \
#     | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
#     sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 06E85760C0A52C50
#     apt-get update
#     apt-get install -y unifi
#   SHELL

# Enable provisioning with ansible playbook
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/hosts-vagrant"
    ansible.limit = 'all'
    ansible.host_key_checking = false
    ansible.verbose = true
  end

end
