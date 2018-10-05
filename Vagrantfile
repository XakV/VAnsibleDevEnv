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
  
  config.vm.define :Flimnoria do |devel|
    devel.vm.hostname = "Flimnoria"
    devel.vm.provision "ansible" do | ansible |
      ansible.verbose = true
      ansible.playbook = "provisioning/playbook.yml"
      ansible.become = true
      ansible.raw_arguments = ["-e 'ansible_python_interpreter=/usr/bin/python3'"]
      ansible.host_vars = { 
        "Flimnoria" => {"ansible_python_interpreter" => "/usr/bin/python3"}
      }
    end
  end
end
