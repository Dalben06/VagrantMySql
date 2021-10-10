Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end


  config.vm.define "mysql" do |mysql|

    mysql.vm.network "forwarded_port", guest: 3306, host: 3306

    mysql.vm.provider "virtualbox" do |vb|
      vb.name = "VM-MySQL"
    end
    mysql.vm.provision "shell", inline: "apt-get update"
    mysql.vm.provision "shell", inline: "apt-get install -y mysql-server-5.7"
    mysql.vm.provision "shell", inline: "cat /vagrant/mysqld.cnf > /etc/mysql/mysql.conf.d/mysqld.cnf"
    mysql.vm.provision "shell", inline: "service mysql restart" 
  end

end
