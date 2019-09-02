# Principais comandos utilizados com React
### Resumo para preparar o ambiente para desenvolver em React com Expo
```
$ npm install -g npm  (Atualiza globalmente a versão do Node.js)
$ npm install --save react@latest (Instalar a ultima versão do react)
$ npm install -g expo-cli (Instalar a ultima versão do Expo)
$ npm audit fix  (Corrige alguns erros automaticamente)
```

### Atualizando a versão do SDK do EXPO
```
$ vim package.json
{
  "react-native": "https://github.com/expo/react-native/archive/sdk-34.0.0.tar.gz",
  "expo": "^34.0.1", <- Atualize o numero da versao aqui
  "react": "16.8.3"
}

# Após altera a versão, delete o diretório `node_modules` e execute o comando `npm install` novamente

$ cd <pasta-projeto>
$ rm -rf node_modules
$ rm -rf package-lock.json
$ npm install
```

### Fazer o build para android

```
$ expo build:android
```

### Instalando modulos de dependencia
`Unable to resolve module `scheduler` from.....`
```
$ expo-cli install scheduler
```
### Atualizando uma dependência
`Exemplo: npm WARN deprecated joi@14.0.4: This version has been deprecated in accordance with the hapi support policy....`
```
$ expo-cli install scheduler
```
