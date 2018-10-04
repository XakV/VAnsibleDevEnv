# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "fedora/28-cloud-base"
  config.vm.box_check_update = true
  config.vm.box_version = "20180425"
  config.ssh.insert_key = false
  config.vm.define "fedev-supy"
  config.vm.provider :libvirt do |l|
    l.memory = 1024
  end

  config.vm.hostname = "fedev-supy"
  config.vm.network :public_network, 
      :ip => "10.10.10.0",
      :dev => "virbr0",
      :mode => "bridge",
      :type => "bridge"

  config.vm.provision "ansible" do | ansible |
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.become = true
  end
end
