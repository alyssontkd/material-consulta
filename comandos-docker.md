###  Verify which cgroup driver dockerd is using
```
docker info | grep -i cgroup
```

###  Listar todas as redes geradas e gerenciadas pelo docker
```
docker network ls
```

###  Executar um comando dentro do container, neste caso estamos executando o bash
```
sudo docker exec -it <name_container> ou <id_container> /bin/bash 
Ex: sudo docker exec -it ambiente-desenvolvimento /bin/bash    
```

###  Parar a execução de um conteiner
```
sudo docker stop <name_container> ou <id_container>
Ex: sudo docker stop ambiente-desenvolvimentov1.0
```

###  Iniciar a execução de um conteiner que esta com o status de Stop
```
sudo docker start <name_container> ou <id_container>
Ex: sudo docker start ambiente-desenvolvimentov1.0
```

###  Rodar uma imagem para gerar um container
```
sudo docker run -i -t <name_image> ou <id_image> /bin/bash
Ex: sudo docker run -i -t 8dbd9e392a96 /bin/bash
```

###  Roda o composer para criar buildar as imagens e gerar os containers
```
sudo docker-compose up -d
Ex: sudo docker-compose up -d
```

###  Para remover todas aos containers incluindo as que estão em execução acrescente a opção "-f" ou "–force" após o comando "rm".
```
sudo docker rm -f <name_container> ou <id_container>
```

###  Para remover todas as images incluindo as que estão sendo utilizadas por containers acrescente a opção "-f" ou "–force" após o comando "rmi".
```
sudo docker rmi -f <name_image> ou <id_image>
```

###  Sequencia de passos para criar a imagem customizada do Conteiner PHP (Entre no diretorio onde esta o Dockerfile e execute os comandos abaixo)
```
sudo docker build -t alyssontkd/ambiente-desenvolvimento:latest -t alyssontkd/ambiente-desenvolvimento:1.0 .
docker images
sudo docker tag <IMAGE ID> alyssontkd/ambiente-desenvolvimento:latest
sudo docker login
sudo docker push alyssontkd/ambiente-desenvolvimento
```

###  Descobrindo o IP de algum conteiner docker
```
sudo docker inspect <name_container> | grep IPAddress
Ex.: sudo docker inspect database-mysql | grep IPAddress
```
