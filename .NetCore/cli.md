# .NET Core Command Line Interface

## Install EntityFramework Core
```
dotnet tool install -g dotnet-ef
```

## Install Scaffolder
```
dotnet tool install -g dotnet-aspnet-codegenerator
```

## Identity Scaffolder 
```
dotnet aspnet-codegenerator identity [--useDefaultUI] [-dc <dbcontext_name_with_namespace>]
```

## Create solution
```
dotnet new sln --name <solution_name>
```

## Migrate solution to slnx
```
dotnet sln migrate
```

## Create project
```
dotnet new <classlib|webapi|webapp|console|xunit> --name <project_name> [-f <netcoreapp3.1|net5.0|net6.0|net7.0|net8.0|net9.0|net10.0>]
```

## Add project to solution
```
dotnet sln add .\<project_directory>\<project_name>.csproj
```
```
dotnet sln add <project_name>
```

## Remove project from solution
```
dotnet sln remove .\<project_directory>\<project_name>.csproj
```

## Add referece from one project to another
```
dotnet add <project_name> reference <referenced_project_name>
```

## Add nuget package
```
dotnet add package <package_name> [--version=<version_number>]
```

## Add nuget package from local repository
```
dotnet add [project] package <package_name> [--version <version_number>] -s <repository_path>
```

## Remove reference from nuget package
```
dotnet remove package <package_name>
```

## Clean project
```
dotnet clean
```

## Build
```
dotnet build [<solution_name.sln|project_name.csproj>] [--configuration Release]
```

## Publish
```
dotnet publish [--configuration Release]
```
