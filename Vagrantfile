# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
perl -i -pe "s/^php_admin_value\[open_basedir\].+$//" /etc/php5/fpm/pool.d/www.conf
service php5-fpm restart
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "spicyweb/apache-phpfpm"
  config.vm.hostname = "phpfpm.local"
  config.vm.network "private_network", ip: "192.168.33.154"
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--paravirtprovider", "kvm"]
#    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
end
