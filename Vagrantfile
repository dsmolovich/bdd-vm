# -*- mode: ruby; -*-

# Force Virtualbox for those people who have installed vagrant-lxc (e.g.)
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

Vagrant.configure("2") do |config|
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

  config.vm.define "master" do |testMaster|
    config.vm.network "private_network", ip: "192.168.36.100"
    testMaster.vm.box = "2creatives/centos65-x86_64-20140116"
    config.vm.hostname = "master"
    config.ssh.forward_x11 = true

    config.vm.provision "shell", inline: <<-SHELL
      VMSETUPDIR="/vagrant/.setup/master"

      cp -r $VMSETUPDIR/etc/pki/rpm-gpg/* /etc/pki/rpm-gpg/
      cp -r $VMSETUPDIR/etc/yum.repos.d/* /etc/yum.repos.d/
      yum install -y vim php55w php55w-dom php55w-mbstring php55w-pecl-xdebug java7 firefox xorg-x11-xauth xorg-x11-server-Xvfb
      cp -r $VMSETUPDIR/* /

      dbus-uuidgen > /var/lib/dbus/machine-id

      cd /home/vagrant
      curl -sS https://getcomposer.org/installer | php
      php composer.phar update

      ln -s /vagrant/tests/behat.yml behat.yml
      ln -s /vagrant/tests/features features
    SHELL
  end


end