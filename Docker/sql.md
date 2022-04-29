## Gerenciando o SQL Server

#### Baixar imagem
```
docker pull mcr.microsoft.com/mssql/server:2019-latest
```

#### Docker Compose
```
services:
    sqlserver:
        image: mcr.microsoft.com/mssql/server:2019-latest
        container_name: sqlserver
        environment:
            SA_PASSWORD: "sasa"
            ACCEPT_EULA: Y
        ports:
            - 1433:1433
        volumes:
            - c:\lg\containers\sqlserver\data:/var/opt/mssql/data
            - c:\lg\containers\sqlserver\log:/var/opt/mssql/log
            - c:\lg\containers\sqlserver\secrets:/var/opt/mssql/secrets
        restart: always
```
