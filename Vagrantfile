# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
	config.disksize.size = "40GB"
	# The most common configuration options are documented and commented below.
	# For a complete reference, please see the online documentation at
	# https://docs.vagrantup.com.

	# Every Vagrant development environment requires a box. You can search for
	# boxes at https://atlas.hashicorp.com/search.
    config.vm.box = "centos/8"
    config.vm.box_version = "1905.1"
	# Disable automatic box update checking. If you disable this, then
	# boxes will only be checked for updates when the user runs
	# `vagrant box outdated`. This is not recommended.
	# config.vm.box_check_update = false

	# Create a forwarded port mapping which allows access to a specific port
	# within the machine from a port on the host machine. In the example below,
	# accessing "localhost:8080" will access port 80 on the guest machine.
	# Change this or add more ports as needed
	config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true

	# Create a private network, which allows host-only access to the machine
	# using a specific IP.
	# config.vm.network "private_network", ip: "192.168.33.10"

	# Create a public network, which generally matched to bridged network.
	# Bridged networks make the machine appear as another physical device on
	# your network.
	config.vm.network "public_network"

	# Share an additional folder to the guest VM. The first argument is
	# the path on the host to the actual folder. The second argument is
	# the path on the guest to mount the folder. And the optional third
	# argument is a set of non-required options.
	# config.vm.synced_folder "../data", "/vagrant_data"

	# Provider-specific configuration so you can fine-tune various
	# backing providers for Vagrant. These expose provider-specific options.
	# Example for VirtualBox:
	#
	config.vm.provider "virtualbox" do |vb|
			vb.name = "vagrant-docker"
	#   # Display the VirtualBox GUI when booting the machine
	#   vb.gui = true
	#
	#   # Customize the amount of memory on the VM:
	   vb.memory = "10240"
       vb.cpus = "4"
	end
	#
	# View the documentation for the provider you are using for more
	# information on available options.

	#config.vm.provision :shell, :path => "vagrant-docker-vm-init.sh"
end