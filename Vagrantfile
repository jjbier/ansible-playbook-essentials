#-*- mode: ruby -*-
# vi: set ft=ruby :
# Sample Vagrantfile  to setup 
# for Ansible Playbook Essitentials

unless Vagrant.has_plugin?("vagrant-hostsupdater")
    system "vagrant plugin install vagrant-hostsupdater"
end

Vagrant.configure('2') do |config|
    
    config.vm.define "docker" do |docker|

    end    
    
    #config.vm.box           = 'opscode-centos-6.5'
    #config.vm.box_url       = 'http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box'
    # config.vm.memory = 1024
    # config.vm.cpus = 2    


    config.vm.define "www" do |www|
        www.vm.network :private_network, ip: "192.168.200.101"
        www.vm.hostname = 'www.cfs.lo' 
        # config.vm.provision "ansible" do |ansible|
        #     ansible.playbook = "provisioning/www.yml"
        #     ansible.groups = {
        #         "webserver" => ["www"],
        #     }
        # end        
    end   
    config.vm.define "db" do |db|
        db.vm.network :private_network, ip: "192.168.200.102"
        db.vm.hostname = 'db0.cfs.lo' 
        # config.vm.provision "ansible" do |ansible|
        #     ansible.playbook = "provisioning/db.yml"
        #     ansible.verbose = 'vvvv'
        #     ansible.groups = {
        #         "database_server" => ["db"],
        #     }
        # end           
    end    
    config.vm.define "dbel" do |db|
        db.vm.network :private_network, ip: "192.168.200.103"
        db.vm.hostname = 'db1.cfs.lo' 
        db.vm.box = "ansible-ubuntu-1204-i386"
        db.vm.box = "https://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-i386-vagrant-disk1.box"
        # config.vm.provision "ansible" do |ansible|
        #     ansible.playbook = "provisioning/db.yml"
        #     ansible.groups = {
        #         "database_server" => ["dbel"],
        #     }
        # end             
    end    
#    config.vm.define "lb" do |lb|
#        lb.vm.network :private_network, ip: "192.168.61.13"
#    end    
#    

    # Add autorization key with ssh user keys
    config.vm.provision "file",   source: "~/.ssh/id_rsa.pub", destination: "/tmp/authorized_keys"
    config.vm.provision "shell",  inline: 'echo `cat /tmp/authorized_keys` >> /home/vagrant/.ssh/authorized_keys'

    # config.vm.provision "ansible" do |ansible|
    #     ansible.limit = 'webserver'
    # end
end