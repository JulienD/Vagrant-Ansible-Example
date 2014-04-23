# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "Precise64"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network "forwarded_port", guest: 80, host: 8070

  config.vm.network :private_network, ip: "33.33.33.12"

  config.vm.synced_folder ".", "/home/vagrant/Src", nfs: true
  #config.vm.synced_folder "public_html", "/home/vagrant/public_html", nfs: true
  #config.vm.synced_folder "public_html", "/home/vagrant/public_html"

  config.vm.provider :virtualbox do |vb|
    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    # vb.gui = true
  end

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "provisioning/hosts"
    ansible.playbook = "provisioning/playbook.yml"
  end

end
