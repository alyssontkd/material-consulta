###  Atualizar a referencia do repositório local ao repositório remoto quando se renomeia o repositório Remoto
```
git remote set-url <nome_referencia> <novo_nome_remoto> <antigo_nome_remoto>

Ex: git remote set-url origin https://github.com/alyssontkd/proxy-reverso-docker.git https://github.com/alyssontkd/proxy-reverso.git

```

###  Listar apenas os arquivos unmerged (não sofreram merge) antes de fazer um push ou commit
```
git diff --name-status --diff-filter=U
```

###  Desabilitar a verificação SSL (Exemplo do Erro: SSL certificate problem: unable to get local issuer certificate)
```
git config --global http.sslVerify false
```

###  Comando para fazer o git ignorar mudança de permissao como alteração no arquivo.
```
git config core.fileMode false
```

###  Recupera o status de todos os arquivos de acordo com o hash do commit passado como parametro. (Desfaz uma ação de merge automatico quando encontra um conflito)
```
git reset --hard <hash>
Ex: git reset --hard 5df97995cf4a1c1e08dd31a4243e449a8c5e21d4
```

###  Desfaz um commit e ainda gera um Log do que foi revertido
```
git revert --strategy resolve <hash>
Ex: git revert --strategy resolve 5df97995cf4a1c1e08dd31a4243e449a8c5e21d4
```

###  Buscando por um código no seu histórico de commits
```
git grep 'nomeDoCodigo()' $(git rev-list --all)
```

###  Encontrando em qual commit um código foi adicionado / removido
```
git log -StextoDoCodigo
```

###  Apagar Branch Remota
```
git push <nome do origin> > --delete <nome do branch>
Ex: git push ssh_origin --delete dev-andre

```

###  Apagar Branch Local
```
git branch -D <nome do branch>
Ex:  git branch -D seguranca
```

###  Criar uma branch de Segurança
```
git checkout -b <BRANCH-NAME>
Ex: git checkout -b seguranca
```

###  Forçar um "git push" para sobrescrever os arquivos remotos
```
git push -f <remote> <branch>
Ex: git push -f origin master
```

###  Forçar um "git checkout" para sobrescrever os arquivos locais
```
git checkout -f <remote> <branch>
git checkout -f master
```

###  Para forçar Sobrescrever arquivos nao controlados pelo git
```
git fetch --all
git reset --hard origin/<BRANCH-NAME>

Ex: git reset --hard origin/master
```

###  Atualizar todas as informaçoes locais
```
git fetch [origem]

Ex: git fetch ssh_origin ou git fetch origin
```
###  Remover arquivos cacheados que foram ignorados, mas continuam versionados
```
git rm vendor/* -r --cached
git add .
git commit -m 'Ajustando cache dos arquivos'
```

###  Adicionar uma nova origem ao repositorio com autenticaçao SSH
```
git remote add <nome_da_origin> <caminho_repositorio_ssh>

Ex: git remote add ssh_origin git@github.com:alyssontkd/galo.git
```

###  Renomear uma origem existente
```
git remote rename <origem_inicial> <origem_renomeada>

Ex: git remote rename origin2 ssh_origin
```

###  Remover uma origem local
```
git remote rm <nome_origem>

Ex: git remote rm destination
```

###  Apresenta o erro "error: pathspec 'seguranca' did not match any file(s) known to git." ao tentar mudar de branch
```
git remote update
git fetch 
git checkout --track origin/<BRANCH-NAME>

Ex: git checkout --track origin/dev-alysson
```

###  Renomear destino do Repositorio
```
git remote set-url origin new_url

Ex: git remote set-url origin https://github.com/alyssontkd/prova.git
Ex: git remote set-url origin https://github.com/alyssontkd/vendor_zf2.git
Ex: git remote set-url ssh_origin git@github.com:alyssontkd/vendor_zf2.git
```

###  Forlar o PULL a sobrescrever os arquivos locais com as alterações da branch remota.
```
git fetch --all
git reset --hard origin/<BRANCH-NAME>
git pull origin <BRANCH-NAME>
```
```
Exemplo:
git reset --hard origin/master
git pull origin master
```


<!-- 
###  Criar Tags no Código para disponibilizar para Homologação e Produção
Roteiro de publicação de release

1) Certifique-se de que funcionalidade está ok em desenvolvimento no seu branch
2) Faça o merge da branch com a master
3) Certifique-se de que está trabalhando no branch correto e que os commits estão na versão correta:
$ git branch
* nome-do-branch
  master
$ git log

4) Mude para o branch master e faça o merge
$ git checkout master
$ git pull origin master
$ git merge nome-do-branch
É possível que ocorram conflitos. Um conflito é quando um arquivo é alterado em duas branches e o git não consegue fazer o merge automático. Nesse caso, você deve resolver o conflito na mão.

Para o changelog, adotar o padrão:
fix: correção de bug
novo: nova funcionalidade

5) Edite o arquivo CHANGELOG

6) Adicione o texto do release ao CHANGELOG
$ vim CHANGELOG
// faça o commit
$ git add CHANGELOG
$ git commit -m 'adicionando changelog da versão v1.x.x'
$ git push

7) Criar tag no código

// certifique-se de estar trabalhando no branch correto e faça o merge com o master, caso isso ainda não tenha sido feito
$ git branch
  correcoes
* master

// liste as tags que já existem
$ git tag
v1.3.0
v1.3.1
v1.3.2
v1.3.3

// crie a tag
$ git tag -a v1.3.1 -m 'informações sobre o release v1.3.1'

// envie a tag para o repositório central (ex: github, gitlab). Caso contrário a tag será apenas local
$ git push origin v1.3.1

/// ou envie todas as tags
$ git push --follow-tags
Em caso de dúvida, consultar http://192.168.14.67/wiki/Comandos_gerais_de_GIT/#tags

6) Subir para homologação

// verifique qual é a tag atual
$ git describe --tags
v1.3.0

// atualize o repositório
$ git pull

// baixe a tag nova criando uma branch para ela
# git checkout v1.3.1 -b v1.3.1

$ git describe --tags
v1.3.0
7) Verificar publicação

8) Preparar email de release

Caso haja necessidade, elaborar um email de release.

9) Subir para produção

# cd /var/www/novosalic.cultura.gov.br 

// verifique qual é a tag atual
# git describe --tags
v1.3.0

// atualize as referências do repositório sem alterar os arquivos
# git fetch

// verifique se a nova tag apareceu
# git tag
v1.3.0
v1.3.1

// baixe a tag nova criando uma branch para ela
# git checkout v1.3.1 -b v1.3.1
10) Enviar email

-->