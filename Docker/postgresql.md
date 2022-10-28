## Gerenciamento do PostgreSQL

#### Baixar a imagem do Postegre
```
docker pull postgres
```

#### Baixar a imagem do pgadmin
```
docker pull dpage/pgadmin4
```

#### Criar rede para integração de uma instância do PostgreSQL com o pgAdmin4
```
docker network create --driver bridge postgres-network
```

#### Criar um container
> Flags:</br>
-d = rodar em background</br>
--name = nome do container</br>
-p = mapeamento das portas (porta local:porta container)</br>
--network = rede para comunicação do PostgreSQL com o pgAdmin4</br>
-v = volume especificando o diretório de saída do sistema operacional
```
docker run -d --name postgres-server -p 5444:5432 --network=postgres-network -e "POSTGRES_PASSWORD=sasa" -v C:\docker\postgres\data:/var/lib/postgresql/data postgres
```

#### Criar um container para o pgAdmin4
```
docker run -d --name pgadmin4 --network=postgres-network -p 15444:80 -e "PGADMIN_DEFAULT_EMAIL=leandro@leandro.com" -e "PGADMIN_DEFAULT_PASSWORD=sasa" -v C:\docker\pgadmin4:/var/lib/pgadmin dpage/pgadmin4
```

#### Executar o PostgreSQL em modo interativo
```
docker exec -it postgres-server psql -U postgres \c <database_name>
```

#### Comando do PostgreSQL para exportar de um arquivo csv para tabela
```
COPY ufs(sigla, nome, codigoibge) FROM '/var/lib/postgresql/data/records.csv' DELIMITER ';' CSV HEADER;
```
