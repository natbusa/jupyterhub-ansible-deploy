
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "datalab"
    v.memory = 4096
    v.cpus = 4
  end

  config.vm.hostname = "datalab"
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  
  # Set the name of the VM in virtualbox. 
  # See: http://stackoverflow.com/a/17864388/100134
  config.vm.define :datalab do |datalab|
  end

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.verbose = "v"
    ansible.sudo = true
  end

end
