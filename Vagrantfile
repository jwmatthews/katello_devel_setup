# -*- mode: ruby -*-
# vi: set ft=ruby :

KATELLO_GIT_CHECKOUT="../katello"

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  #config.vm.box = "rhel64_x86_64"
  #config.vm.box_url = "http://file.rdu.redhat.com/~jmatthew/vagrant/VirtualBox/rhel64_x86_64.box"
  config.vm.box = "CentOS-6.4-x86_64-v20130427"
  config.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20130427.box"

  config.vm.hostname = "katdev.example.com"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network :private_network, ip: "172.31.2.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network :public_network

  config.vm.synced_folder KATELLO_GIT_CHECKOUT, "/katello"
  config.vm.provision :shell,
      :inline => "cd /vagrant && ./setup_katello_devel_env.sh"
end
