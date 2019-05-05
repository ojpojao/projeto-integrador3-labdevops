Vagrant.configure("2") do |config|
	config.vm.define "zabbix" do |zabbix|
		zabbix.vm.box = "jrio"
		zabbix.vm.box_url = "../debian-zabbix/package.box"
		zabbix.vm.hostname = "zabbix"
		zabbix.vm.network "private_network", ip: "192.168.100.10"
		zabbix.vm.network "forwarded_port", guest: 80, host: 8080
		#zabbix.vm.network "public_network"

		zabbix.ssh.keys_only = false
		zabbix.ssh.username = "vagrant"
		zabbix.ssh.password = "vagrant"
		zabbix.ssh.insert_key = false

		zabbix.vm.provider "virtualbox" do |vb|
			vb.gui = false
			vb.name = "vagrant-zabbix"
			vb.memory = "1024"
		end
	end

	config.vm.define "node01" do |node01|
		node01.vm.box = "jrio"
		node01.vm.box_url = "../debian-zabbix/package.box"
		node01.vm.hostname = "node01-zabbix"
		node01.vm.network "private_network", ip: "192.168.100.20"
		node01.vm.network "public_network"

		node01.ssh.keys_only = false
		node01.ssh.username = "vagrant"
		node01.ssh.password = "vagrant"
		node01.ssh.insert_key = false

		node01.vm.provider "virtualbox" do |vb|
			vb.gui = false
			vb.name = "node01-zabbix"
			vb.memory = "512"
		end
	end	
end
