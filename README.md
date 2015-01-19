## Install roles
sudo ansible-galaxy install -r galaxyfile --force

##Deploy with vagrant
vagrant box add phusion/ubuntu-14.04-amd64 https://vagrantcloud.com/phusion/boxes/ubuntu-14.04-amd64/versions/2/providers/virtualbox.box
vagrant up

## Copy public ssh key to server
ssh-copy-id user@domain -p port

## Deploy project to production
ansible-playbook site.yml -i production --ask-sudo-pass