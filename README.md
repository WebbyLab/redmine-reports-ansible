## Install roles
sudo ansible-galaxy install -r galaxyfile --force

##Deploy with vagrant
vagrant box add phusion/ubuntu-14.04-amd64 https://vagrantcloud.com/phusion/boxes/ubuntu-14.04-amd64/versions/2/providers/virtualbox.box

vagrant up

## Copy public ssh key to server
ssh-copy-id user@domain -p port

## Deploy project to production

Modify production file

    hostname            WRITE_YOUR_HOSTNAME (example: redmine-reports.job.com)
    remote_user         WRITE_YOUR_REMOTE_USER (example: root)
    basic_auth_login    WRITE_YOUR_BASIC_AUTH_LOGIN (example: user)
    basic_auth_password WRITE_YOUR_BASIC_AUTH_PASSWORD (example: password)
    redmine_url         WRITE_YOUR_REDMINE_URL (example: http://redmine.job.com/)
    redmine_host        WRITE_YOUR_REDMINE_HOST (example: redmine.job.com)
    redmine_api_key     WRITE_YOUR_REDMINE_API_KEY ( api_key from redmine )
    mail_from           MAIL_FROM (example: reports@redmine.com )
    mail_min_log_time   MINIMAL_LOG_TIME (example: 40 hours at last week for eight-hour shift)
    mail_destination_emails ARRAY_DESTINATION_EMAILS (example: ["worker1@mail.com", "worker2@mail.com"]);

ansible-playbook site.yml -i production --ask-sudo-pass