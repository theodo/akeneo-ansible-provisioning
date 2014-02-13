# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/ubuntu-server-12042-x64-vbox4210.box"
  config.vm.hostname = "akeneo"

  config.vm.network :private_network, ip: "10.0.0.30"
  config.ssh.forward_agent = true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.customize ["modifyvm", :id, "--cpus", "1"]
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "provisioning/hosts/development"
    ansible.sudo           = true
    ansible.playbook       = "provisioning/site.yml"
    #ansible.verbose        = 'vvv'
  end
end
