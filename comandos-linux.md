### Listar todos os usuarios cadastrados no meu linux
```
getent passwd | cut -d \: -f1
```

###  Conectar via SSH do Linux utilizando um certificado - Amazon AWS
```
ssh -i "caminho_completo_do_certificado" <usuario>@<host>
Ex: ssh -i "magatti.pem" ubuntu@ec2-35-160-28-149.us-west-2.compute.amazonaws.com
```

###  Conectar a um host via SSH passando a porta de conexao.
```
ssh root@sapassejus01.sistemasinternet.com.br -p 22666
```

###  Descobrir a versão do sistema operacional (linux)
```
cat /etc/os-release
```

###  Adiciona usuario ao grupo
```
gpasswd -a nome_usuario nome_grupo
```

###  Procurar um termo nos arquivos de um diretório, excluido um diretório da busca
```
grep -rins --exclude-dir=diretorio/excluido/da/busca/ 'termo_procurado' /diretorio/realizacao/busca
```


### Edita o arquivo responsavel pelos SUDORS do S.O
```
visudo
```


###  Copiar arquivos de um servicor remoto via scp
```
scp -P 22666 root@sapassejus01.sistemasinternet.com.br:/tmp/glpi.acthosti.com.br.conf /tmp
```

###  Transferir arquivos locais para um servicor remoto via scp
```
scp -P 22666 /tmp/glpi.acthosti.com.br.conf root@sapassejus01.sistemasinternet.com.br:/tmp
```

### Copiar arquivos de um servicor Amazon AWS para a máquina local via scp
```
scp -i "/home/alysson/magatti.pem" ubuntu@ec2-35-160-28-149.us-west-2.compute.amazonaws.com:/tmp/script_inicial_2017_08_29.sql .
```

###  Buscar e substituir string com VIM
```
:%s/<busca>/<subtituta>/g
:%s/pera/uva/g
EX: 
```

###  Recuperar o WSDL
```
wget --certificate=/opt/minc-cert/cert2015.cer -private-key=/opt/minc-cert/cert2015.cer https://webservice.siop.gov.br/services/WSQuantitativo?wsdl
```

###  Listar a codificação de todos os arquivos
```
find . -type f -exec file --mime {} \;
```

###  Listar a codificação de todos os arquivos (filtrar por um tipo específico)
```
find . -type f -iname "*.php" -exec file --mime {} \;
```

### Convertendo Arquivos de ISO-8859-1 para UTF-8
```
iconv -f iso-8859-1 -t utf-8 arquivo.txt > arquivo_novo.txt 
```

### Convertendo Arquivos de UTF-8 para ISO-8859-1
```
iconv -f utf-8 -t iso-8859-1 arquivo.txt > arquivo_novo.txt 
```

### Renomeando todos os arquivos de uma  pasta [/home/musicas] (incluindo as subpastas, usando o find), de ISO-8859-1 para UTF-8: 
```
find /var/www/html/siminc -type f | while read line; do mv "$line" "$(echo $line | iconv -f iso-8859-1 -t utf-8)"; done
```


### Alterar permissoes de todos os Arquivos para 774
```
find . -type f -exec chmod 774 {} \;
```

### Altera a permissao de todas as pastas para 775
```
find . -type d -exec chmod 775 {} \;
```

### Altera o dono e o grupo de todos os arquivos
```
chown -R apache: .
```


### Caminho do VHost no Debian
```
/etc/httpd/conf.d/
```

### Caminho de Log do CronTab no Ubuntu.
```
cat /var/log/syslog | less
```

### Listar Alterações para o cronTab
```
crontab -l
```

### Editar o cronTab
```
crontab -e
```
###  Ordenar conteudo dos diretórios por tamanho, onde o maior fica no top
```
du -h --max-depth=1 | sort -h -r
```

### Descobrir versão do DEBIAN
```
lsb_release -a 
```

### Descobrir versão do CentOS
```
cat /etc/*-release | grep PRETTY
```
Saída:
```
PRETTY_NAME="CentOS Linux 7 (Core)"
```

###  Customizaçãono Terminal (Colar dentro do arquivo .profile)
```
alias la='ls -la --color=auto'
```

