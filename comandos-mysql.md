### Erros comuns do MySQL
> Caso o erro `ERROR 2006 (HY000) at line xxxx: MySQL server has gone away` seja apresentado, vá no arquivo `my.ini` e altere o parametro `max_allowed_packet` que fica na seção `[mysqld]` e reinicie o serviço do mysql.
```
max_allowed_packet=500M
```
###  Entrar automaticamente no mysql via linha de comando já informando a senha como parametro de conexao.
```
mysql -u <nome_usuario> -pmypassword -h <IP_HOST> -P 3306
Ex.: mysql -u root -h 172.19.0.3 -p12345678
```

###  Realizar o Dump de uma base automaticamente, com usuario e senha informados via linha de comando
```
mysqldump -u <nome_usuario> -B <nome_base_dados> -pmypassword > <caminho_completo_arquivo.sql>
Ex.: mysqldump -u root -B bdsisa -pmysql > /tmp/script_bdsisa_20170720.sql
```

### Teste de carga de estresse já pronto do MySQL (https://www.digitalocean.com/community/tutorials/how-to-measure-mysql-query-performance-with-mysqlslap)
```
mysqlslap --user=root --password --host=localhost  --auto-generate-sql --verbose
mysqlslap --user=root --password --host=localhost  --concurrency=50 --iterations=100 --number-int-cols=5 --number-char-cols=20 --auto-generate-sql --verbose
mysqlslap --user=root --password --host=localhost  --concurrency=50 --iterations=10 --create-schema=employees --query="SELECT * FROM dept_emp;" --verbose
```


### Correção do erro mysql 1366 incorrect integer value sql Mode http://stackoverflow.com/questions/8874647/general-error-1366-incorrect-integer-value-with-doctrine-2-1-and-zend-form-upda/8882396#8882396
```
SELECT @@GLOBAL.sql_mode; SELECT @@SESSION.sql_mode;

SET @@global.sql_mode= 'NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';
```

### Ativa e Desativa a Gravação dos Loghs de Acesso ao Sistema. Serve para capturar os SQLS realizados pela aplicação.
```
SET GLOBAL general_log = 'OFF';
E...
SET GLOBAL general_log = 'ON';
```

### O caminho em que o arquivo foi gerado foi:
```
C:\xampp\mysql\data\<Nome_da_estação>.log
```

### Listar todos os usuarios cadastrados no mysql
```
SELECT * FROM mysql.user;
```

### Criar um novo usuario
```
CREATE USER 'usuario'@'localhost' IDENTIFIED BY '123456';

GRANT ALL PRIVILEGES ON dbcontroletotal . * TO 'usuario'@'localhost';
GRANT ALL PRIVILEGES ON * . * TO 'usuario'@'localhost';

FLUSH PRIVILEGES;
```

### Listar todas as Views de um banco de dados
```
SHOW FULL TABLES IN database_name WHERE TABLE_TYPE LIKE 'VIEW';
```

### Campos de inserção automatica de Datas na Inserção ou atualização do registro
```
CREATE TABLE foo (
    creation_time      DATETIME DEFAULT   CURRENT_TIMESTAMP,
    modification_time  DATETIME ON UPDATE CURRENT_TIMESTAMP
)
```

### O grande problema de se calcular a diferença de tempo entre datas pode ser resolvido com uma função do MYSQL a TIMESTAMPDIFF().
###Seguem alguns exemplos de como calcula a diferença entre TIMESTAMP e retorno em: 
#### Horas
```
SELECT TIMESTAMPDIFF(HOUR, hora_inicial, hora_final ) FROM TABELA
```

#### Minutos
```
SELECT TIMESTAMPDIFF(MINUTE, hora_inicial, hora_final ) FROM TABELA
```

#### Segundos
```
SELECT TIMESTAMPDIFF(SECOND, hora_inicial, hora_final ) FROM TABELA


Dica: Para calcular diferença entre campos DATE utilize a função DATEDIFF.
Dica: Para calcular diferença entre campos TIME utilize a função TIMEDIFF.
```

### Buscar por uma ocorrencia de string dentro de outra string
```
select * from email_2 where locate('string_desejada',em_email);
```
