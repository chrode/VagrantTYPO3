# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

	# check for box updates on each up
	config.vm.box_check_update = true

	# configure network
	config.vm.network "private_network", ip: "192.168.50.50"

	# configure the VM via Puppet
	config.vm.provision :puppet

	config.vm.provider "virtualbox" do |virtualbox, override|
		override.vm.box     = "chef/ubuntu-14.04"
        override.vm.box_url = "chef/ubuntu-14.04"

        # override.vm.synced_folder "vHosts/", "/var/www/", id: "vagrant-root", :nfs => true, nfs_export: true, nfs_udp: true, nfs_version: 4
         override.vm.synced_folder "vHosts/", "/var/www/", type: "rsync"

        virtualbox.memory = "2048"
  		virtualbox.cpus = "2"
	end

	config.vm.provider "vmware_fusion" do |vmware_fusion, override|
		override.vm.box     = "CorbanRaun/trusty64"
        override.vm.box_url = "CorbanRaun/trusty64"

        override.vm.synced_folder "vHosts/", "/var/www/", id: "vagrant-root", :nfs => true , nfs_export: true, nfs_udp: true, nfs_version: 4

 		vmware_fusion.vmx["memsize"] = "2048"
  		vmware_fusion.vmx["numvcpus"] = "2"
	end

	config.vm.provider "vmware_workstation" do |vmware_workstation, override|
		override.vm.box     = "chef/ubuntu-14.04"
        override.vm.box_url = "chef/ubuntu-14.04"
        override.vm.synced_folder "vHosts/", "/var/www/", owner: "www-data", group: "www-data" , type: "rsync"

 		vmware_workstation.vmx["memsize"] = "2048"
  		vmware_workstation.vmx["numvcpus"] = "2"
	end
end
