# Criar um novo banco de dados e restaurar o backup dentro dente banco via terminal
```
createdb -h localhost -p 5432 -U <usaerdb> <database_name>
psql -U <usaerdb> -d  <database_name> -f /paht-file/file-name.sql
```
### Exemplo
```
$ createdb -h localhost -p 5432 -U postgres opera360text
$ psql -U postgres -d opera360 -f D:/tmp/opera360.sql
```

# Realizar Backup do tipo Plain a partir do Terminal (Com comandos INSERT)
```
pg_dump -U db_user -W -F p db_name > /path_of_the_dump/dump_file.sql
```
### Exemplo
```
pg_dump -U postgres -W -F p opera360 --column-inserts > D:/tmp/opera360.sql
```

# Realizar Restore do tipo Plain a partir do Terminal
```
psql -U db_user -d db_name -f /path_of_the_dump/dump_file.sql
```
### Exemplo
```
$ psql -U postgres -d opera360 -f D:/tmp/opera360.sql
```

# Criar um banco de dados a partir do terminal para importar um dump plain
```
createdb -h localhost -p 5432 -U dbuser testdb
```
### Exemplo
```
$ createdb -h localhost -p 5432 -U postgres opera360
```

# Conectar a um banco de dados específico no servidor  Postgres
```
psql -U <username> -d <database_name> -h localhost
```
### Exemplo
```
$ psql -U postgres -d opera360 -h localhost
Senha: <Informe a senha do usuario postgres>
```

# Conectar a um servidor Postgres
```
psql -U postgres -h localhost -W
Senha: <Informe a senha do usuario postgres>
```

# Criar um banco de dados logado no Postgres 
```
CREATE DATABASE your_database_name;
CREATE DATABASE opera360;
```
