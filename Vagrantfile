VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/trusty64"
    web.vm.hostname = 'web'
    web.vm.box_url = "ubuntu/trusty64"
    web.vm.network :private_network, ip: "192.168.56.101"
    
    web.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "web"]
    end
    web.vm.provision :ansible do |ansible|
        ansible.playbook = "playbook.yml"
    end
  end
  
  config.vm.define "db" do |db|
    db.vm.box = "ubuntu/trusty64"
    db.vm.hostname = 'db'
    db.vm.box_url = "ubuntu/trusty64"
    db.vm.network :private_network, ip: "192.168.56.101"
    
    db.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db"]
    end
    db.vm.provision :ansible do |ansible|
        ansible.playbook = "playbook.yml"
    end
  end
end
