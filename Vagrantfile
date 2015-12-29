# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.define :toolchain do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.network :private_network, ip: "192.168.56.212", :adapter => 2
    config.vm.provider "virtualbox" do |vb|
      vb.name = "toolchain"
      vb.memory = 1024
      vb.cpus = 1
      vb.gui = false
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
    end
  config.vm.provision "file", source: "vagrant_files/ansible.cfg", destination: "~/ansible.cfg"
  config.vm.provision "file", source: "vagrant_files/hosts", destination: "~/hosts"
  config.vm.provision "shell", inline: $configure
  end 
end

$configure = <<SCRIPT
  sudo apt-get install -y software-properties-common
  sudo apt-add-repository ppa:ansible/ansible
  sudo apt-get update
  sudo apt-get install -y ansible
  ansible-playbook -vvv /vagrant/play.yml -c local
SCRIPT
