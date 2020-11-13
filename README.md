# Docker and VirtualBox

1. Instalando docker

	sudo apt-get update && apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
	
	
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -


	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"


	sudo apt-get install docker-ce docker-ce-cli containerd.io

2. Add user no ao grupo docker e instalando compose

	sudo usermod -aG docker $USER && newgrp docker


	sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose


sudo chmod +x /usr/local/bin/docker-compose


3. Restaurando o dump do mysql:


	mysql -h127.0.0.1 -uroot -p -D lmva_db < lmva_db.dump.sql


4. Executando docker-composer

	docker-composer up -d

# Configurando Mail Fake

http://127.0.0.1:8025/#


local.properties
server=127.0.0.1
port=1025

