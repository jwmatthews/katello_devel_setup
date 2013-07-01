Katello Development Setup
===================

Shell/Vagrant scripts to provision a VM in a development environment for Katello 

#### Features
1. Scripts to automate katello development setup from: 
 https://fedorahosted.org/katello/wiki/DevelopmentSetup
1. Provisions and configures a new VM based on CentOS 6.4
1. Uses the ruby 193 SCL to run the rails server
1. The VM and host are sharing the Katello git checkout allowing the host to edit code and see it reflected in VM

#### Requirements
1. Install VirtualBox
 * https://www.virtualbox.org/wiki/Linux_Downloads
2. Install Vagrant  
>rpm -Uvh http://files.vagrantup.com/packages/7e400d00a3c5a0fdf2809c8b5001a035415a607b/vagrant_1.2.2_x86_64.rpm
3. Checkout katello git repo: https://github.com/Katello/katello
 * It is assumed that the Katello checkout exists 1 directory up from this repo
 * Edit "Vagrantfile" and change KATELLO_GIT_CHECKOUT if you have katello somewhere else  
>KATELLO_GIT_CHECKOUT="../katello"  
  * Note:  This git checkout will be shared with the HOST and the VM

#### Instructions
1. vagrant up
 * Allow ~20-30 minutes for:
   * a CentOS 6.4 VM to be downloaded/booted
   * katello nightly RPMs to be installed
   * switch over to using katello git checkout opposed to RPMs
1. Edit /etc/hosts  
>172.31.2.10 katdev.example.com
1. Start the rails server on the VM by sshing into the VM.
 * User: vagrant
 * Pass: vagrant  
>ssh vagrant@katdev.example.com
>cd /katello
>sudo scl enable ruby193 "rails s"
1. On your host visit: http://katdev.example.com:3000/katello


