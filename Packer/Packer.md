# Packer

* Pré-requisito
        Instalação do Docker

        Rodando o Dockefile do Packer

        Exportar as credenciais

        Instalar Ansible


Criar usuário AWS com acesso prográmatico e exportando

	export AWS_ACCESS_KEY_ID=AKIA3VD3ZOEEQNDCZU4G
	export AWS_SECRET_ACCESS_KEY=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



# Rodando imagem do packer via Docker

        docker run -it -v $PWD:/app -w /app --entrypoint "" hashicorp/packer:light sh

# Builders

É obrigatorio a sessão "builders" no Packer aonde tem as informações sobre a IMG. 
Quando executo o build do packer-estudo01.json. Ele cria uma instancia temporia na AWS e bate uma foto,
criando minha IMG. E depois exclui essa instancia, deixando apenas minha IMG na conta da AWS.

Deploy
        packer build packer.json

# Ansible Provisioners

Existe 2 formas de usam o Ansible no Packer. Na máquina temporaia (local) que o Packer ou na sua máquina(remoto) via ssh conecta 
na máquina temporaria. Usando via ssh não é necessário fazer instalações na máquina temporaria.

# Instalado Ansible meu container(local)
        apk -U add ansible

# Deploy com arquivo variables.json
        packer build -var-file=variables.json packer-estudo04-var-file.json

#  Troubleshooting
        packer build -var-file=variables.json -on-error=ask packer-eestudo04-var-file.json        

        PACKER_LOG=1 packer build -var-file=variables packer-estudo04-var-file.json
