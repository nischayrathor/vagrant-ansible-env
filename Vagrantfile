Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"
  config.vm.box = "ubuntu/trusty64"
  config.vm.define "haproxy"
  config.vm.define "web-application"
  config.vm.define "db"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "setup-infra.yml"
    ansible.host_vars = {
      "haproxy" => {"service" => "haproy"},
      "web-application" => {"service" => "web-app"},
      "db" => {"service" => "db"},
    }
  end
end
