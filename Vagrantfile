# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define :xubuntu do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.hostname = "xubuntu"
    config.vm.network :private_network, ip: "192.168.56.30", :adapter => 2
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 1
	    vb.gui = true
	    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
    end
    config.vm.provision "shell", inline: $configure_xubuntu
  end

  config.vm.define :trusty do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "trusty"
    config.vm.network :private_network, ip: "192.168.56.31", :adapter => 2
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.cpus = 1
    end
    config.vm.provision "shell", inline: $configure_trusty
  end

  config.vm.define :xenial do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.hostname = "xenial"
    config.vm.network :private_network, ip: "192.168.56.32", :adapter => 2
    config.vm.provider "virtualbox" do |vb|
      vb.name = "xenial"
      vb.memory = 512
      vb.cpus = 1
    end
    config.vm.provision "shell", inline: $configure_xenial
  end

  config.vm.define :fedora24 do |config|
    config.vm.box = "fedora/24-cloud-base"
    config.vm.hostname = "fedora24"
    config.vm.network :private_network, ip: "192.168.56.33", :adapter => 2
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.cpus = 1
    end
    config.vm.provision "shell", inline: $configure_fedora24
  end

  config.vm.define :centos7 do |config|
    config.vm.box = "centos/7"
    config.vm.hostname = "centos7"
    config.vm.network :private_network, ip: "192.168.56.34", :adapter => 2
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.cpus = 1
    end
    config.vm.provision "shell", inline: $configure_centos7
  end

  config.vm.define :atomic do |config|
    config.vm.box = "centos/atomic-host"
    config.vm.hostname = "atomic"
    config.vm.network :private_network, ip: "192.168.56.35", :adapter => 2
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.cpus = 1
    end
	  config.vm.provision "shell", inline: $configure_atomic
  end

end

$configure_xubuntu = <<SCRIPT
  echo "127.0.0.1       xubuntu" >> /etc/hosts
  sudo cp /vagrant/authorized_keys /root/.ssh/authorized_keys
  cat /vagrant/authorized_keys >> /home/ubuntu/.ssh/authorized_keys
  sudo apt-get install -y build-essential libssl-dev libffi-dev python-dev python-pip
  sudo pip install ansible
  cd /vagrant
  ansible-playbook play.yml
  ansible-playbook xubuntu.yml
SCRIPT

$configure_trusty = <<SCRIPT
  sudo cp /vagrant/authorized_keys /root/.ssh/authorized_keys
  cat /vagrant/authorized_keys >> /home/vagrant/.ssh/authorized_keys
  sudo apt-get install -y python-pip
  sudo pip install markupsafe
  sudo pip install ansible
  cd /vagrant
  ansible-playbook play.yml
SCRIPT

$configure_xenial = <<SCRIPT
  echo "127.0.0.1       xenial" >> /etc/hosts
  sudo cp /vagrant/authorized_keys /root/.ssh/authorized_keys
  cat /vagrant/authorized_keys >> /home/ubuntu/.ssh/authorized_keys
  sudo apt-get install -y build-essential libssl-dev libffi-dev python-dev python-pip
  sudo pip install ansible
  cd /vagrant
  ansible-playbook play.yml
SCRIPT

$configure_fedora24 = <<SCRIPT
  sudo cp /vagrant/authorized_keys /root/.ssh/authorized_keys
  cat /vagrant/authorized_keys >> /home/vagrant/.ssh/authorized_keys
  sudo dnf install -y gcc libffi libffi-devel openssl-devel python-devel python-pip redhat-rpm-config
  sudo pip install ansible
  cd /vagrant
  ansible-playbook play.yml
SCRIPT

$configure_centos7 = <<SCRIPT
  sudo mkdir /root/.ssh/
  sudo cp /vagrant/authorized_keys /root/.ssh/authorized_keys
  cat /vagrant/authorized_keys >> /home/vagrant/.ssh/authorized_keys
  sudo yum install -y epel-release
  sudo yum install -y gcc openssl-devel python-devel python-pip
  sudo pip install ansible
  cd /vagrant
  ansible-playbook play.yml
SCRIPT

$configure_atomic = <<SCRIPT
  sudo mkdir /root/.ssh/
  sudo cp /var/home/vagrant/sync/authorized_keys /root/.ssh/authorized_keys
  cat /var/home/vagrant/sync/authorized_keys >> /home/vagrant/.ssh/authorized_keys
SCRIPT
