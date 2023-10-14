## Gerenciando pacotes nugets

### Listar os repositórios configurados

```
nuget sources
```

### Criar um repositório local

```
nuget sources add -name {repository_name} -Source {repository_path}
```

### Remover um repositório local

```
nuget sources remove -name {repository_name}
```

### Criar um pacote para posterior publicação em repositórios

Manter pelo menos as principais propriedades do projeto preenchidas para gerar o arquivo nuspec. Exemplo de nuspec:
```
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
    <AssemblyVersion>1.0.0.0</AssemblyVersion>
    <Authors>Leandro</Authors>
    <Company>LGG</Company>
    <Description>Data access component.</Description>
    <FileVersion>1.0.0.0</FileVersion>
    <PackageId>LGG.Framework</PackageId>
    <Product>LGG.Framework</Product>
    <Version>1.0.0</Version>
  </PropertyGroup>
</Project>
```

Criar o pacote (usando dotnet cli) e adicionar ao repositório
```
dotnet pack [--configuration=release]
nuget add <package_name.0.0.0.nupkg> -source <repository_path>
```

### Remover um pacote de um repositório local
```
nuget delete {NOME_PACOTE} {NUMERO_VERSAO} -source {PATH_REPOSITORIO}
```
