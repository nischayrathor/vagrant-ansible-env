Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"
  config.vm.box = "ubuntu/trusty64"
  #  config.vm.define "haproxy"
  #  config.vm.define "web-application"
  #  config.vm.define "db"
  config.vm.define "haproxy" do |haproxy|
    haproxy.vm.provision "ansible" do |ansible|
      ansible.playbook = "setup-haproxy.yml"
    end
  end
  config.vm.define "webapps" do |webapps|
    webapps.vm.provision "ansible" do |ansible|
      ansible.playbook = "setup-webapps.yml"
    end
  end
  config.vm.define "db" do |db|
    db.vm.provision "ansible" do |ansible|
      ansible.playbook = "setup-db.yml"
    end
  end
end
