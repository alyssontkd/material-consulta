# Principais comandos utilizados com React

### Atualizando a versão do Node instalada na Máquina
```
$ npm install -g npm  (Atualiza globalmente a versão do Node.js)
```

### Instalar a ultima versão do react
```
$ npm install --save react@latest
```

### Instalar a ultima versão do Expo
```
$ npm install -g expo-cli
```

### Atualizando a versão do SDK do EXPO
```
{
  "react-native": "https://github.com/expo/react-native/archive/sdk-34.0.0.tar.gz",
  "expo": "^34.0.1", <- Atualize o numero da versao aqui
  "react": "16.8.3"
}
```
```
# Após altera a versão, delete o diretório `node_modules` e execute o comando `npm install` novamente

$ cd <pasta-projeto>
$ rm -rf node_modules
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
