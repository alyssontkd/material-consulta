# Cucumber

Na especificação do Cucumber as funcionalidades são escritas utilizando a linguagem chamada Gherkin (próxima linguagem natural) e contém algumas palavras-chave.

### Para obter um relatório de todas as linguas suportadas pelo cucumber:
```
cucumber --i18n-languages
```
### Para iniciar um projeto com a estrutura padrão do cucumber:
```
cucumber --init
```
### Criando as estruturas de pastas e arquivos necessários em um projeto padrão de Cucumber:
```
create   features
create   features/step_definitions
create   features/support
create   features/support/env.rb
```
### Gerando steps de forma rápida:
```
cucumber -d
```
### Não mostrar na tela os snippets que ainda faltam concluir:
```
cucumber --no-snippets
ou
cucumber -i
```
### Executando os testes de forma padrão:
```
cucumber
```
### Executando os cenários por tags:
```
cucumber -t @name_tag
```
### Especificar o número de vezes para repetir os testes com falha:
```
cucumber --retry 2
```
### Executa os cenários na ordem em que são definidos.:
```
cucumber --order defined
```
### Definir que os cenários sejam executados de forma aleatória:
```
cucumber --order random
```
### Exibir os arquivos carregados durante a execução:
```
cucumber --verbose
```
### Cancelar a execução dos testes, caso o primeiro cenário falhar:
```
cucumber --fail-fast
```
### Executar os testes, de acordo com determinado perfil:
```
cucumber --profile
```

PS: "Cucumber não serve apenas para automatizar os testes. Cucumber é uma ferramenta de colaboração com a intenção de criar um entendimento comum entre todos os membros do time."

