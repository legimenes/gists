## Interface de linha de comando do .Net Core

#### Instalar EntityFramework Core
```
dotnet tool install -g dotnet-ef
```

#### Instalar Scaffolder
```
dotnet tool install -g dotnet-aspnet-codegenerator
```

#### Scaffolder Identity
```
dotnet aspnet-codegenerator identity [--useDefaultUI] [-dc <dbcontext_name_with_namespace>]
```

#### Criar solution
```
dotnet new sln --name <solution_name>
```

#### Criar projeto
```
dotnet new <classlib|webapi|webapp|console|xunit> --name <project_name> [-f <netcoreapp3.1|net5.0|net6.0|net7.0>]
```

#### Adicionar projeto à solution
```
dotnet sln add .\<project_directory>\<project_name>.csproj
```
```
dotnet sln add <project_name>
```

#### Remover projeto da solution
```
dotnet sln remove .\<project_directory>\<project_name>.csproj
```

#### Adicionar referência de um projeto dentro de outro
```
dotnet add <project_name> reference <referenced_project_name>
```

#### Adicionar pacote do nuget
```
dotnet add package <package_name> [--version=<version_number>]
```

#### Adicionar pacote do nuget de repositório local
```
dotnet add [project] package <package_name> [--version <version_number>] -s <repository_path>
```

#### Remover referência de pacote nuget
```
dotnet remove package <package_name>
```

#### Limpar projeto
```
dotnet clean
```

#### Executar build
```
dotnet build [<solution_name.sln|project_name.csproj>] [--configuration Release]
```

#### Publicar
```
dotnet publish [--configuration Release]
```
