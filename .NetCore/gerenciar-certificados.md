## Criar certificado HTTPS para ambiente DEV

#### Limpar certificado previamente instalado
```
dotnet dev-certs https --clean
```

#### Criar novo certificado
```
dotnet dev-certs https -t
```

#### Verificar certificado criado
```
dotnet dev-certs https --check
```
