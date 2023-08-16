## Importação de CSV

Comando:
```
COPY <TABELA>[(campos)]
FROM {'PATH_CSV'} DELIMITER <'CARACTER_DELIMITDADOR'> CSV HEADER;
```

Exemplo:
```
COPY public.users(name, email)
FROM 'C:/temp/users.csv' DELIMITER ';' CSV HEADER;
```
