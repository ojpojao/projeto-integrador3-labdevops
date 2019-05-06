# Setup para o LAB Projeto Integrador 3

1. Instale o VirtualBox e o Vagrant
2. Certifique-se que o vagrant está no PATH de executáveis do seu SO
3. Acesse a URL *https://github.com/paulojoao93/projeto-integrador3-labdevops*  e clique no botão *clone or download* e escolha a opção zip
4. Descompate o arquivo. Abra um terminal na pasta descompactada

## Exemplo no Windows 10
- Abra um terminal e execute os comandos abaixo:
```
vagrant init paulojoao93/PI3-zabbix-server
```
Um arquivo VagrantFile tem aparência semelhante ao que está abaixo. É aqui que descreveremos o provisionamento das nossas máquinas virtuais.
```ruby
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
end
```
