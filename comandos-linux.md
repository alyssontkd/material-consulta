### Executa um comando automaticamente a cada xx segundos
```
;; Executa do df-vh a cada 5 segundos
watch -n 5 df -vh
```
watch -n 5 df -vh

### Lista todos os arquivos modificados nos ultimos 05 minutos
```
;; Executa do find /tmp -mmin -05 -ls a cada 2 segundos
watch -n 2 find /tmp -mmin -05 -ls
```
watch -n 2 find /tmp -mmin -05 -ls

### Lista todos os arquivos modificados nos ultimos 10 dias
```
;; Executa do find /tmp -mmin -05 -ls a cada 2 segundos
watch -n 2 find /tmp -mtime -10 -ls
```
watch -n 2 find /tmp -mtime -10 -ls

### Lista todos os arquivos modificados a mais 10 dias
```
;; Executa do find /tmp -mmin +10 -ls a cada 2 segundos
watch -n 2 find /tmp -mtime +10 -ls
```
watch -n 2 find /tmp -mtime +10 -ls

### Apagar arquivos com mais de XX dias
```
;; mais que 360 dias
find /usr/local/scci-fpc/.git/objects/pack ! -mtime -360 |xargs rm -rf
```

### Enviar Email com sendEmail via Terminal do Ubuntu
```
;; Modo Debug
$ sendEmail -v -v -f central.millenium@gmail.com -t alyssontkd@gmail.com -u "Test Mail" -o username="central.millenium@gmail.com" -o password="magatti1981" -s "smtp.gmail.com:587" -o message-file=TODO.md

;; Modo Enviar Email com Anexo (Gmail)
$ sendEmail -f central.millenium@gmail.com -t alyssontkd@gmail.com -u "[Anexo] Backup do servidor da FINANCEIRO" -m "Backup do servidor FINANCEIRO" -a TODO.md -s smtp.gmail.com:587 -xu central.millenium@gmail.com -xp magatti1981 -o tls=yes

;; Modo Enviar Email com Anexo (Outro Serviço de Email)
$ sendEmail -f asstjinforma@vertenti.com.br -t alyssontkd@gmail.com -u "[Anexo] Teste de envio de email" -m "Backup do servidor ASSTJ" -a TODO.md -s smtp.hostinger.com.br:587 -xu asstjinforma@vertenti.com.br -xp 	 -o tls=yes
```

### Apagar arquivos baseado na sua data de modificação. Serve para apagar arquivos antigos que não são mais utilizados
```
sudo find '[caminho]' -mtime +10 -type f -exec rm {} \; || true

Ex:
sudo find '/var/log/launcher' -mtime +10 -type f -exec rm {} \; || true

OBS: -mtimen avaliará como verdadeiro se o tempo de modificação do arquivo subtraído do tempo de inicialização, dividido por 86400 (com o restante descartado) for n.
```

### Retorna a quantidade de processos que esta sendo executada por cada usuarioi logado no servidor
```
# ps -eo user=|sort|uniq -c
```

### Retorna a quantidade de processos de um serviço específico que esta sendo executada no servidor
```
# ps -C <nome-do-processo> | wc -l
Ex: 
# ps -C httpd | wc -l
ou
# pgrep httpd | wc -l
```

### Para substituir uma string por outra sem entrar no arquivo
```
sed -i 's,TEXTO_ORIGINAL,novo_texto,g' nome_arquivo

Ex:
sed -i 's,GLPI,glpi,g' glpi_app1.sql
```

### Retorna a quantidade de arquivos dentro de um diretório
```
$ find /var/www/html -maxdepth 1 -type d | while read -r dir; do printf "%s:\t" "$dir"; find "$dir" -type f | wc -l; done
```

### Limpando o diretório /boot no CentOS e Família RedHat
```
yum install yum-utils -y
package-cleanup --oldkernels --count=1
grub2-mkconfig -o /boot/grub2/grub.cfg ( atualizar a tela inicial do grub2: /boot/grub2/grub.cfg)

Caso você queira evitar este problema futuramente, edite o arquivo /etc/yum.conf e altere o parametro abaixo:
installonly_limit=2 ou installonly_limit=1

```

### Desabilitando um repositório de pacotes no linux da família RedHad (Mint e CentOS):
```
$ yum-config-manager --disable <nome-repositorio>

Ex: 
$ yum-config-manager --disable gitlab_gitlab-ee-source
```

### Instalando o HTOP no CentOS e Família RedHat
```
$ cd /tmp
$ wget dl.fedoraproject.org/pub/epel/7/x86_64/Packages/e/epel-release-7-11.noarch.rpm
$ rpm -ihv epel-release-7-11.noarch.rpm
$ yum install htop -y
```

### Liberando porta 80 - http no firewall do linux da família RedHad (Mint e CentOS):
```
$ sudo firewall-cmd --list-all                           (Lista os serviços liberados)
$ sudo firewall-cmd --add-service=http --permanent       (Adiciona a porta 80 como autorizada a receber conexão)
$ sudo firewall-cmd --reload                             (Recarregue as configurações do Browser)
$ sudo firewall-cmd --list-all                           (Lista os serviços liberados)
```

### Removendo porta 22 - SSH no firewall do linux da família RedHad (Mint e CentOS):
```
$ sudo firewall-cmd --list-all                           (Lista os serviços liberados)
$ sudo firewall-cmd --remove-service=ssh --permanent    (Só execute caso deseja remover a liberação do SSH)
$ sudo firewall-cmd --reload                             (Recarregue as configurações do Browser)
$ sudo firewall-cmd --list-all                           (Lista os serviços liberados)
```

### Compactar um diretório com o comando TAR 
```
tar -zcf nome_arq.tar nome_dir_ou_arq_a_ser_compactado
Ex: tar -zcf banco_projeto.tar /tmp/banco (diretório)
Ex: tar -zcf pacote.tar arquivo1.gif memorando.htm carta.doc (arquivos individuais)
```

### Para descompactar arquivos no formato TAR
```
tar -zxvf nomedoarq.tar
```

### Para descompactar arquivos no formato ZIP
```
unzip arquivo.zip
```
### Visualizar o conteúdo de um arquivo ZIP sem descompactar 
```
unzip -l meuarquivo.zip
```

### Listando todos os pacotes instalados no CentOs (YUM)
```
yum list installed
```

### Exportando a lista de todos os pacotes instalados no CentOs (YUM) para um arquivo
```
yum list installed > <caminho_arquivo>
Ex: yum list installed > /tmp/yum-list.txt
```
### Criando o diretório 'planilhas' já criando todos os diretórios precedentes automaticamente
Observ.: Só existe até o diretório /home/alysson e desejo criar uma pasta, onde não existe suas pastas precedentes.
```
mkdir -p /home/alysson/sistemas/sisa/planilhas
```
### Para criar várias pastas dentro de um diretório local
```
mkdir sistema banco documentos testes scripts
```
### Para criar várias subpastas dentro de um diretório 
Criando vários diretórios dentro do diretório `sistemas`
```
mkdir -p sistemas/{banco,documentos,testes,scripts,requisitos}
```
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

