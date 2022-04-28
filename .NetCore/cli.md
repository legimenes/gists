# Interface de linha de comando do .Net Core

#### Instalar EntityFramework Core
```
dotnet tool install dotnet-ef --global
```

#### Criar solution
```
dotnet new sln --name {NOME_SOLUTION}
```

#### Criar projeto class library
```
dotnet new classlib --name {NOME_PROJETO} [-f {netcoreapp3.1|net5.0|net6.0}]
```

#### Criar projeto xunit
```
dotnet new xunit --name {NOME_PROJETO} [-f {netcoreapp3.1|net5.0|net6.0}]
```

#### Adicionar projeto à solution
```
dotnet sln add .\{DIRETORIO_PROJETO}\{NOME_PROJETO}.csproj
```

#### Adicionar referência de um projeto dentro de outro
```
dotnet add {NOME_PROJETO} reference {NOME_PROJETO_REFERENCIADO}
```

#### Adicionar pacote do nuget
```
dotnet add package {NOME_PACOTE} [--version={NUMERO_VERSAO}]
```

#### Adicionar pacote do nuget de repositório local
```
dotnet add package {NOME_PACOTE} [--version {NUMERO_VERSAO}] -s {PATH_REPOSITORIO}
```

#### Remover referência de pacote nuget
```
dotnet remove package {NOME_PACOTE}
```

#### Limpar projeto
```
dotnet clean
```

#### Executar build
```
dotnet build [{NOME_SOULUTION.sln|NOME_PROJETO.csproj}] [--configuration Release]
```

#### Publicar
```
dotnet publish [--configuration Release]
```

#### Criar um pacote para posterior publicação em repositórios
```
dotnet pack [--configuration=release]
nuget add {NOME_PACOTE.0.0.0.nupkg} -source {PATH_REPOSITORIO}
```
