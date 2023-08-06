## Comandos para gerenciamento do Internet Information Services

### Diretório para executar os comandos

```
cd %systemroot%\system32\inetsrv
```

### Criar Appication Pool

```
appcmd add apppool /name:<APLICATIONPOOL_NAME> /managedRuntimeVersion:<VERSION> /managedPipelineMode:<Basic|Integrated>
```

Exemplo:
```
appcmd add apppool /name:PoolSite1 /managedRuntimeVersion:v4.0 /managedPipelineMode:Integrated
```

### Deletar Application Pool

```
appcmd delete apppool <APLICATIONPOOL_NAME>
```

### Criar Website

```
appcmd add site /name:<WEBSITE_NAME> /physicalPath:<SITE_PATH> /bindings:<PROTOCOL_PORT>
```

Exemplo:
```
appcmd add site /name:site1 /physicalPath: c:\site1 /bindings:http/*:85:
```

### Alterar Application Pool do Website criado

```
appcmd set app <WEBSITE_NAME>/ /applicationPool:<APLICATIONPOOL_NAME>
```

Exemplo:
```
appcmd set app site1/ /applicationPool:PoolSite1
```

### Criar Aplicação Virtual dentro do Website

```
appcmd add app /site.name:<WEBSITE_NAME> /path:/<VIRTUALAPPLICATION_NAME> /physicalPath:<PATH>
```

Exemplo:
```
appcmd add app /site.name:site1 /path:/sitecliente1 /physicalPath:c:\sitecliente1
```

### Alterar o Application Pool da Aplicação Virtual criada

```
appcmd set app <WEBSITE_NAME>/<VIRTUALAPPLICATION_NAME> /applicationPool:<APLICATIONPOOL_NAME>
```
