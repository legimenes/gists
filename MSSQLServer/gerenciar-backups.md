## Gerenciar backups no MS SQL Server

### Listar arquivos do backup
```
RESTORE FILELISTONLY FROM DISK = N'<path_arquivo.bak>'
```

### Restaurar backup
```
RESTORE DATABASE <nome_banco_dados>
FROM DISK = N'<path_arquivo.bak>'
WITH MOVE '<nome_logico_dados>' TO '<path_arquivo_Data.mdf>',
MOVE '<nome_logico_logs>' TO '<path_arquivo_Log.ldf>'
```
