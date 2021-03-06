# -*- mode: ruby -*-
# # vi: set ft=ruby :

# Specify minimum Vagrant version and Vagrant API version
VAGRANTFILE_API_VERSION = "2"

# Create boxes
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.synced_folder ".", "/vagrant"
    config.hostmanager.enabled = true

    config.vm.define "kube1" do |srv|
        srv.vm.box = "bento/centos-7"
        srv.vm.network "private_network", ip: "192.168.100.55"
        srv.vm.hostname = "kube1"

        srv.vm.provider :virtualbox do |vb|
            vb.name = "kube1"
            vb.memory = "4096"
            vb.cpus = 2
            vb.gui = false
        end
    end

    config.vm.provision "shell", privileged: false, inline: <<-SHELL
        sudo yum install -y ansible
        sudo yum -y install epel-release --enablerepo=extras
        cd /vagrant
        ansible-playbook -i inventory main.yml
        sudo yum -y update
    SHELL
end
