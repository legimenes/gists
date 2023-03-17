## Comandos para o Entity Framework Core

#### Atualizar ferramenta
```
dotnet tool update --global dotnet-ef
```

#### Listar migrações
```
dotnet ef migrations list
```

#### Criar migração
```
dotnet ef migrations add <migration_name> [-o <Data/Migrations>] [--verbose]
```

#### Atualizar banco de dados
```
dotnet ef database update [--verbose]
```

#### Atualizar banco de dados para uma migração específica
```
dotnet ef database update <migration_name> [--verbose]
```

#### Remover ultima migração
```
dotnet ef migrations remove [--verbose]
```

#### Scaffold
```
dotnet ef dbcontext scaffold <"string_conexao"> Microsoft.EntityFrameworkCore.SqlServer [-o nome_pasta] [-f] [-t nome_tabela1 -t nome_tabela2] [--verbose]
```
