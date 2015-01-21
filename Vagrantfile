# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "hashicorp/precise32"
    config.vm.network :forwarded_port, host: 5001, guest: 8080

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "site.yml"
        # ansible.verbose = "v"

        ansible.groups = {
            "appservers" => ["default"]
        }

        ansible.extra_vars = {
            hostname: "vagrant.redmine-reports.com",
            remote_user: "vagrant"
        }
    end
end
