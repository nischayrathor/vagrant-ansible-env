Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"
  config.vm.box = "ubuntu/trusty64"
  #  config.vm.define "haproxy"
  #  config.vm.define "web-application"
  #  config.vm.define "db"
  config.vm.define "haproxy" do |haproxy|
    haproxy.vm.hostname = 'haproxy'
    haproxy.vm.network "private_network", ip: "192.168.50.222"
    haproxy.vm.provision "ansible" do |ansible|
      ansible.playbook = "setup-haproxy.yml"
    end
    haproxy.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 256]
      v.customize ["modifyvm", :id, "--name", "haproxy"]
    end
  end
  config.vm.define "webapps" do |webapps|
    webapps.vm.hostname = 'webapps'
    webapps.vm.network "private_network", ip: "192.168.50.223"
    webapps.vm.provision "ansible" do |ansible|
      ansible.playbook = "setup-webapps.yml"
    end
    webapps.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 256]
      v.customize ["modifyvm", :id, "--name", "webapps"]
    end
  end
  config.vm.define "db" do |db|
    db.vm.hostname = 'db'
    db.vm.network "private_network", ip: "192.168.50.224"
    db.vm.provision "ansible" do |ansible|
      ansible.playbook = "setup-db.yml"
    end
    db.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db"]
    end
  end
end
