## Configuração do LocalDB

### String de conexão
```
Data Source=(LocalDB)\v12.0;AttachDbFilename=|DataDirectory|\<file_name>.mdf;Integrated Security=SSPI
```

### Resolvendo problemas de conexão
Executar no terminal:
```
"<path_instalacao_sql_server>\<versao>\Tools\Binn\SqlLocalDB.exe" create "v<versao>"
```

Exemplo:
```
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" create "v12.0
```
