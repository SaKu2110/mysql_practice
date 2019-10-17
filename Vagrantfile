# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "practice.mysql" do |o|
    o.vm.box = "centos/7"
    o.vm.hostname = "linux-user"
    o.vm.provision "shell", inline: <<-SHELL
	rpm -ivh https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
	yum update -y
	yum install -y mysql-community-devel
	yum install -y mysql-community-server
	echo "\n# how to setup mysql" >> /etc/motd
	echo '$ mysql_secure_installation' >> /etc/motd
	echo '# how to login mysql' >> /etc/motd
	echo "$ mysql -u root -p\n" >> /etc/motd
    SHELL
  end
end
