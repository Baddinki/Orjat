# Multislave vagrant for Puppet
# Copyright 2017 Tero Karvinen http://TeroKarvinen.com
# Ohjeet täällä http://terokarvinen.com/2017/provision-multiple-virtual-puppet-slaves-with-vagrant
# Osa Tero Karvisen Linux kurssia..

$tscript = <<TSCRIPT
apt-get update
apt-get -y install puppet
grep ^server /etc/puppet/puppet.conf || echo -e "\n[agent]\nserver=master\n" |sudo tee -a /etc/puppet/puppet.conf
grep master /etc/hosts || echo -e "\n172.28.172.247  master\n"|sudo tee -a /etc/hosts
puppet agent --enable
sudo service puppet start
sudo service puppet restart
TSCRIPT

Vagrant.configure(2) do |config|

 config.vm.box = "bento/ubuntu-16.04"
 config.vm.provision "shell", inline: $tscript

 config.vm.define "orja01" do |orja01|
 tero01.vm.hostname = "orja01"
 end

 config.vm.define "orja02" do |orja02|
 tero02.vm.hostname = "orja02"
 end

end
