# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"


  # assigned by DHCP
  #config.vm.network "public_network"
  # assigned by static
  config.vm.network "public_network", ip:"192.168.10.233/16"

  config.vm.synced_folder "./conf", "/tftpboot", mount_options: ['dmode=777','fmode=755']

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y tftp tftpd-hpa

    echo 'TFTP_USERNAME="tftp"' > /etc/default/tftpd-hpa
    echo 'TFTP_DIRECTORY="/tftpboot"' >> /etc/default/tftpd-hpa
    echo 'TFTP_ADDRESS=":69"' >> /etc/default/tftpd-hpa
    echo 'TFTP_OPTIONS="--secure --create -p"' >> /etc/default/tftpd-hpa

    systemctl restart tftpd-hpa.service

    chmod -R a+rwx /tftpboot
    chown -R tftp /tftpboot
    ip addr | grep inet
  SHELL
end
