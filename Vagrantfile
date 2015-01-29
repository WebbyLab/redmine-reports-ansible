# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "hashicorp/precise32"
    config.vm.network :forwarded_port, host: 5000, guest: 80

    config.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "site.yml"
        # ansible.verbose = "v"

        ansible.groups = {
            "appservers" => ["default"]
        }

        ansible.extra_vars = {
            hostname: "localhost",
            nginx_proxy_listen_port: "80",
            remote_user: "vagrant"
        }
    end
end
