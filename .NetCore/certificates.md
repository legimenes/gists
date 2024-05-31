# Create HTTPS cerfificate for DEV environment

## Clean previous installed certificate
```
dotnet dev-certs https --clean
```

## Create new certificate
```
dotnet dev-certs https -t
```

## Verify certificate creation
```
dotnet dev-certs https --check
```
