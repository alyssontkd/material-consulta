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
