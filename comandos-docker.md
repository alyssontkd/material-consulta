## Reiniciar o Apache dentro de um Conteiner
```
# docker exec -it <CONTEINER_ID> /bin/bash
# /etc/init.d/apache2 reload
```
## Erro do Docker quando o encaminhamento IPv4 está desativado (CentOs 7)
Quando o daemon do docker não pode se conectar ao mundo externo para baixar qualquer coisa durante o tempo de compilação um erro é gerado. Normalmente este erro é encontrado quando você está tentando criar uma imagem docker: **"[Warning] IPv4 forwarding is disabled. Networking will not work."**. Esta mensagem está nos informando será necessário habilitar o encaminhamento IPV4.

Para resolver acesse o arquivo `/usr/lib/sysctl.d/99-docker.conf` com seu editor favorito e adicione, edite ou crie as seguintes entradas para o arquivo para que o docker possa acessar o mundo externo a sua infraestrutura:
```
fs.may_detach_mounts=1
net.ipv4.ip_forward=1
```
Feito isso basta reiniciar o serviço docker da sua máquina e prosseguir com suas atividades.
```
[mbacchi@centos7 ~]$ sudo systemctl restart docker
[mbacchi@centos7 ~]$
```
## Para apagar tudo que o docker consumiu e que não está sendo mais utilizado por ele no seu servidor.
```
#### espaço em disco antes da liberação ####
root@meuservidor:~# df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      7.7G  6.9G  880M  89% /

#### comando para executar a liberação do espaço ####
root@meuservidor:~# docker system prune -a
WARNING! This will remove:
        - all stopped containers
        - all volumes not used by at least one container
        - all networks not used by at least one container
        - all images without at least one container associated to them
Are you sure you want to continue? [y/N] y

#### espaço em disco depois da liberação ####
root@meuservidor:~# df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      7.7G  5.0G  2.8G  64% /
```

##  Verificando qual driver cgroup está sendo utilizado pelo dockerd 
```
docker info | grep -i cgroup
```

##  Listar todas as redes geradas e gerenciadas pelo docker
```
docker network ls
```

##  Executar um comando dentro do container, neste caso estamos executando o bash
```
sudo docker exec -it <name_container> ou <id_container> /bin/bash 
Ex: sudo docker exec -it ambiente-desenvolvimento /bin/bash    
```

##  Parar a execução de um conteiner
```
sudo docker stop <name_container> ou <id_container>
Ex: sudo docker stop ambiente-desenvolvimentov1.0
```

##  Iniciar a execução de um conteiner que esta com o status de Stop
```
sudo docker start <name_container> ou <id_container>
Ex: sudo docker start ambiente-desenvolvimentov1.0
```

##  Rodar uma imagem para gerar um container
```
sudo docker run -i -t <name_image> ou <id_image> /bin/bash
Ex: sudo docker run -i -t 8dbd9e392a96 /bin/bash
```

##  Roda o composer para criar buildar as imagens e gerar os containers
```
sudo docker-compose up -d
Ex: sudo docker-compose up -d
```

##  Para remover todas aos containers incluindo as que estão em execução acrescente a opção "-f" ou "–force" após o comando "rm".
```
sudo docker rm -f <name_container> ou <id_container>
```

##  Para remover todas as images incluindo as que estão sendo utilizadas por containers acrescente a opção "-f" ou "–force" após o comando "rmi".
```
sudo docker rmi -f <name_image> ou <id_image>
```

##  Sequencia de passos para criar a imagem customizada do Conteiner PHP (Entre no diretorio onde esta o Dockerfile e execute os comandos abaixo)
```
sudo docker build -t alyssontkd/ambiente-desenvolvimento:latest -t alyssontkd/ambiente-desenvolvimento:1.0 .
docker images
sudo docker tag <IMAGE ID> alyssontkd/ambiente-desenvolvimento:latest
sudo docker login
sudo docker push alyssontkd/ambiente-desenvolvimento
```

##  Descobrindo o IP de algum conteiner docker
```
sudo docker inspect <name_container> | grep IPAddress
Ex.: sudo docker inspect database-mysql | grep IPAddress
```

# Limitando a memória ram dos containers

## Configurando a memória para um container

*Comando*
```console
docker run -it --memory 512m debian
```

Para visualizar a memória configurada para o container, utilize o seguinte comando:

*Comando*
```console
docker inspect <id_container> | grep -i mem
```

*Saída*
```console
"Memory": 536870912,
"CpusetMems": "",
"KernelMemory": 0,
"MemoryReservation": 0,
"MemorySwap": 1073741824,
"MemorySwappiness": -1,
```

> Observe que na primeira linha temos a quantidade de memória que configuramos para o container.

## Alterando a memória do container

Após o container ter sido criado, caso você precise alterar o limite de memória utilizada por ele, utilize o seguinte comando:

*Comando*
```console
docker update --memory 256m <id_container|nome_container>
```

> Você pode substituir o parâmetro ``--memory`` por ``-m`` se preferir.

# Limitando a CPU dos containers

## Configurando o limite de uso de cpu do container

*Comando*
```console
docker run -it --cpu-shares 1024 debian
```

## Alterando o limite de uso de cpu do container

*Comando*
```console
docker update --cpu-shares 512 <id_container|nome_container>
```

## Adicionando uma Chave SSH dentro de uma imagem docker para clone automático (sem solicitar login e senha)
```
FROM ubuntu

MAINTAINER Luke Crooks "luke@pumalo.org"

# Update aptitude with new repo
RUN apt-get update

# Install software 
RUN apt-get install -y git
# Make ssh dir
RUN mkdir /root/.ssh/

# Copy over private key, and set permissions
ADD id_rsa /root/.ssh/id_rsa

# Create known_hosts
RUN touch /root/.ssh/known_hosts
# Add bitbuckets key
RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts

# Clone the conf files into the docker container
RUN git clone git@bitbucket.org:User/repo.git
```

## Instalção do DOCKER no Debian e RedHat
**Instalando o docker via repositório do Ubuntu, Deepin e família Debian**
```
$ sudo apt update
$ sudo apt install docker.io
$ sudo systemctl start docker
$ sudo systemctl enable docker
$ docker --version
Docker version 18.03.1-ce, build 9ee9f40
```
**Instalando no CentOS, Mint e família RedHat**
```
$ sudo yum update
$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2
$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
$ sudo yum install docker-ce
$ sudo usermod -aG docker $(whoami)
$ sudo systemctl enable docker.service
$ docker --version
Docker version 18.03.1-ce, build 9ee9f40
```

## Instalar DOCKER-COMPOSE no Debian e RedHat
**Instalando no CentOS, Mint e família RedHat**
```
$ sudo yum install epel-release
$ sudo yum install -y python-pip
$ sudo pip install docker-compose
$ sudo yum upgrade python*
$ pip install --upgrade pip
```
## No Ubuntu, Deepin e família Debian
```
$ sudo curl -L https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

**Pronto! Seu docker-compose já deve estar instalado. Valide a instalação com o comando abaixo:**
```
$ docker-compose --version
```
