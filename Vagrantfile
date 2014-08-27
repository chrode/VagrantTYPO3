# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

	# puppetlabs VM
	config.vm.box     = "puppetlabs/ubuntu-14.04-64-puppet"
    config.vm.box_url = "puppetlabs/ubuntu-14.04-64-puppet"

	# check for box updates on each up
	config.vm.box_check_update = true

	# configure network
	config.vm.hostname = "devops-#{rand(100000..999999)}"
    config.vm.network :public_network
    config.vm.network :private_network, ip: "192.168.50.50"

	# configure the VM via Puppet
    config.vm.provision "puppet" do |puppet|
        puppet.manifests_path = "puppet/manifests"
        puppet.manifest_file = "default.pp"
    end

	config.vm.provider "virtualbox" do |virtualbox, override|
        override.vm.synced_folder "vHosts/", "/var/www/", id: "vagrant-root", :nfs => true

        virtualbox.memory = "2048"
  		virtualbox.cpus = "2"
	end

	config.vm.provider "vmware_fusion" do |vmware_fusion, override|
        override.vm.synced_folder "vHosts/", "/var/www/", id: "vagrant-root", :nfs => true 

 		vmware_fusion.vmx["memsize"] = "2048"
  		vmware_fusion.vmx["numvcpus"] = "2"
	end

	config.vm.provider "vmware_workstation" do |vmware_workstation, override|
        override.vm.synced_folder "vHosts/", "/var/www/", owner: "www-data", group: "www-data" , type: "rsync"

 		vmware_workstation.vmx["memsize"] = "2048"
  		vmware_workstation.vmx["numvcpus"] = "2"
	end
end
