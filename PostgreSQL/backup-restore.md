## Backup e restore de base de dados

Executar dentro da pasta bin

### Backup
```
pg_dump.exe –h <NOME_SERVIDOR> –p <PORTA> –U <USUARIO> –F t –f <PATH_DESTINO>
```

### Restore
```
pg_restore.exe –h <NOME_SERVIDOR> –p <PORTA> –U <USUARIO> -d <NOME_DATABASE> <PATH_DESTINO>
```
