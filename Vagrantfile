# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "netbox" do |netbox|
    netbox.vm.box = "netbox"

    netbox.ssh.username = "root"
    netbox.ssh.password = "root"
  

    netbox.vm.synced_folder ".", "/vagrant", disabled: true
    
    netbox.vm.network "private_network", ip: "192.168.56.103"
    netbox.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
  end

  config.vm.define "tower" do |tower|
    tower.vm.box = "tower"

    tower.ssh.username = "root"
    tower.ssh.password = "root"

    tower.vm.synced_folder ".", "/vagrant", disabled: true
    
    tower.vm.network "private_network", ip: "192.168.56.107"

    tower.vm.network "forwarded_port", guest: 443, host: 8443, auto_correct: true
  end

  config.vm.define "vyos" do |vyos|
    vyos.vm.box = "vyos"

    vyos.ssh.username = "vyos"
    vyos.ssh.password = "vyos"
  
    vyos.vm.synced_folder ".", "/vagrant", disabled: true

    vyos.vm.network "private_network", ip: "192.168.56.110"
    vyos.vm.network "private_network", ip: "192.168.51.30",
      auto_config: false
    vyos.vm.network "private_network", ip: "192.168.52.30",
      auto_config: false    
  end

end
