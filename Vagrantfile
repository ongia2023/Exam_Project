# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "Master" do |master|
    master.vm.box = "ubuntu/bionic64"
    master.vm.network "private_network", type: "dhcp"
    master.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end

    master.vm.provision "shell", path: "lamp-install.sh"
  end

  config.vm.define "Slave" do |slave|
    slave.vm.box = "ubuntu/bionic64"
    slave.vm.network "private_network", type: "dhcp"
    slave.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end

    # Execute Ansible playbook to run additional tasks
    slave.vm.provision "ansible" do |ansible|
      ansible.playbook = "provision.yml" # Replace with your playbook filename
    end
  end
end

