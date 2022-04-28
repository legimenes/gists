## Interface de linha de comando do .Net Core

#### Instalar EntityFramework Core
```
dotnet tool install dotnet-ef --global
```

#### Criar solution
```
dotnet new sln --name {solution_name}
```

#### Criar projeto class library
```
dotnet new classlib --name {project_name} [-f {netcoreapp3.1|net5.0|net6.0}]
```

#### Criar projeto xunit
```
dotnet new xunit --name {project_name} [-f {netcoreapp3.1|net5.0|net6.0}]
```

#### Adicionar projeto à solution
```
dotnet sln add .\{project_directory}\{project_name}.csproj
```

#### Adicionar referência de um projeto dentro de outro
```
dotnet add {project_name} reference {referenced_project_name}
```

#### Adicionar pacote do nuget
```
dotnet add package {package_name} [--version={version_number}]
```

#### Adicionar pacote do nuget de repositório local
```
dotnet add package {package_name} [--version {version_number}] -s {repository_path}
```

#### Remover referência de pacote nuget
```
dotnet remove package {package_name}
```

#### Limpar projeto
```
dotnet clean
```

#### Executar build
```
dotnet build [{solution_name.sln|project_name.csproj}] [--configuration Release]
```

#### Publicar
```
dotnet publish [--configuration Release]
```

#### Criar um pacote para posterior publicação em repositórios
```
dotnet pack [--configuration=release]
nuget add {package_name.0.0.0.nupkg} -source {repository_path}
```
