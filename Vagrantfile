# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  # Public network (choose your network, e.g. Wi-Fi)
  config.vm.network "public_network"

  # Provisioning: installing nginx and changing the port to 82
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y nginx
    sed -i 's/listen 80 default_server;/listen 82 default_server;/' /etc/nginx/sites-available/default
    sed -i 's/listen \\[::\\]:80 default_server;/listen [::]:82 default_server;/' /etc/nginx/sites-available/default
    systemctl restart nginx
  SHELL
end