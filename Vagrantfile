Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"

  # config.vm.box_check_update = false
  config.vm.network "private_network", type: "dhcp"
  #config.vm.network "public_network", ip: "192.168.1.10", bridge: "wlp3s0"
  #config.vm.network "public_network", ip: "192.168.1.10", bridge: "wlp2s0"
  #config.vm.network "private_network", ip: "192.168.1.10"
  # config.vm.synced_folder "../data", "/vagrant_data"

  #config.vm.network "forwarded_port", guest: 3306, host: 3306
  config.vm.network :forwarded_port, guest: 3306, host: 3306
  config.vm.network :forwarded_port, guest: 8181, host: 8181
  config.vm.network :forwarded_port, guest: 1521, host: 1521
  config.vm.network :forwarded_port, guest: 8025, host: 8025
  config.vm.network :forwarded_port, guest: 1025, host: 1025
  config.vm.network :forwarded_port, guest: 27017, host: 27017
  config.vm.network :forwarded_port, guest: 28017, host: 28017

  config.vm.provider "VirtualBox" do |vb|
     vb.memory = "6192"
  end
  config.vm.provision "shell", inline: <<-SHELL
	sudo apt-get update
	sudo apt-get install apt-transport-https ca-certificates curl software-properties-common build-essential mysql-client
	sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
	sudo apt-get update
	sudo apt-get install -y docker-ce=18.06.1~ce~3-0~ubuntu vim unrar
	echo "Realizando tar no hybris-server.tar.gz"
	#cd /vagrant/data/
	#tar zxvf hybris-server.tar.gz
	#echo "fim do tar"
	sudo ls /vagrant/data/
	echo "Criando grupo docker"
	sudo usermod -aG docker $USER
	#sudo addgroup --system docker
	sudo adduser vagrant docker
	newgrp docker
	echo "Fim da permissão do grupo docker."
	sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
	sudo chmod +x /usr/local/bin/docker-compose
	cd /vagrant
	docker-compose up -d
  SHELL
end
