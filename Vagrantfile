# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define :centos60 do |centos60|
    centos60.vm.box = "centos6"
    centos60.vm.box_url = "http://spectrum.werus.be/vagrant/centos-6.4-x86_64.box"
    centos60.vm.hostname = "centos60"
    centos60.vm.network :private_network, ip: "192.168.131.100"
  end

  config.vm.define :centos61 do |centos61|
    centos61.vm.box = "centos6"
    centos61.vm.box_url = "http://spectrum.werus.be/vagrant/centos-6.4-x86_64.box"
    centos61.vm.hostname = "centos61"
    centos61.vm.network :private_network, ip: "192.168.131.101"
    centos61.vm.network :forwarded_port, guest: 80, host: 8080
  end

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "hosts_vagrant"
    ansible.playbook = "opennebula/one_core.yml"
    ansible.sudo = "true"
    ansible.host_key_checking = "false"
  end
end

