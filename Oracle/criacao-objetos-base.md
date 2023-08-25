## Criação de objetos base do Banco de Dados

### Criação de usuário com direitos de admin
```
create user <username>
  identified by <password>
  default tablespace USERS
  temporary tablespace TEMP
  profile DEFAULT
  
grant connect to <username> with admin option
grant dba to <username> with admin option
grant unlimited tablespace to <username> with admin option
```
  
### Criação de tablespaces
```
create tablespace <tablespace_name>
  logging
  datafile 'C:\oracle\oradata\<database_name>/base.dbf' 
  size 32m 
  autoextend on 
  next 32m maxsize 500m
  extent management local

create tablespace <tablespace_index_name>
  logging
  datafile 'C:\oracle\oradata\<database_name>/baseind.dbf' 
  size 32m 
  autoextend on 
  next 32m maxsize 500m
  extent management local
```
