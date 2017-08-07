# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "aiag-inspection"

  config.vm.network :forwarded_port, guest: 8070, host: 8070
  config.vm.network :private_network, type: "dhcp"
  config.vm.network :public_network, bridge: 'en0: Wi-Fi (AirPort)'

  config.vm.synced_folder ".", "/home/vagrant/aiag_inspection"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.host_key_checking = "false"
    ansible.limit = "all"
    ansible.playbook = "deployment/vagrant/setup.yml"
  end

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
  end
end
