## Gerar chaves para certificados

Usar o openssl

### Gerar chave privada RSA
```
genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048
```

### Gerar chave pública RSA
```
rsa -pubout -in private_key.pem -out public_key.pem
```
