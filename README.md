# Packer

Pré-requisito

Instalar Ansible
	
		sudo apt install ansible
	
Instalação do Packer
	
		curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
		sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
		sudo apt-get update && sudo apt-get install packer

AWS CLI

		curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
		unzip awscliv2.zip
		sudo ./aws/install

# Builders

É obrigatorio "builders" no Packer aonde tem as informações sobre a IMG. 
Quando executo o build do packer-estudo01.json. Ele cria uma instancia temporia na AWS e bate uma foto,
criando minha IMG. E depois exclui essa instancia, deixando apenas minha IMG na conta da AWS.

# Deploy packer-estudo01.json
        packer build packer-estudo01.json
	
# Deploy packer-02-k8s
	packer build packer-estudo02.json
	
# Deploy packer-estudo03-var
	packer build packer-estudo03-var.json
	
# Deploy packer-estudo04-var-file
	packer build -var-file=variables.json packer-estudo04-var-file.json

# Ansible Provisioners

Existe 2 formas de usam o Ansible no Packer. Na máquina temporária (local) ou na sua máquina (remoto). 

# Deploy com arquivo variables.json
        packer build -var-file=variables.json packer-estudo04-var-file.json

#  Troubleshooting
        packer build -var-file=variables.json -on-error=ask packer-eestudo04-var-file.json        

        PACKER_LOG=1 packer build -var-file=variables packer-estudo04-var-file.json

# Listando módulos
	ansible-doc -l
	
# Listando módulo específico
	ansible-doc aws_s3
