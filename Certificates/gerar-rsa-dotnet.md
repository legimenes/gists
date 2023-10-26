## Gerar RSA no .NET

Instalar o pacote BouncyCastle.NetCore

### Obter chave privada do RSA
```
public RSAParameters GetPrivateKeyRSAParameters(string privateKey)
{
	RsaPrivateCrtKeyParameters rsaPrivateKeyParams;
	using (var sr = new StringReader(privateKey))
	{
		PemReader pemReader = new PemReader(sr);
		rsaPrivateKeyParams = (RsaPrivateCrtKeyParameters)pemReader.ReadObject();
	}

	RSAParameters rsaParameters = new RSAParameters
	{
		Modulus = rsaPrivateKeyParams.Modulus.ToByteArrayUnsigned(),
		Exponent = rsaPrivateKeyParams.PublicExponent.ToByteArrayUnsigned(),
		D = rsaPrivateKeyParams.Exponent.ToByteArrayUnsigned(),
		P = rsaPrivateKeyParams.P.ToByteArrayUnsigned(),
		Q = rsaPrivateKeyParams.Q.ToByteArrayUnsigned(),
		DP = rsaPrivateKeyParams.DP.ToByteArrayUnsigned(),
		DQ = rsaPrivateKeyParams.DQ.ToByteArrayUnsigned(),
		InverseQ = rsaPrivateKeyParams.QInv.ToByteArrayUnsigned(),
	};

	RSACryptoServiceProvider rsaProvider = new RSACryptoServiceProvider(2048);
	rsaProvider.ImportParameters(rsaParameters);

	RSAParameters privateKeyRSAParameters = rsaProvider.ExportParameters(true);

	return privateKeyRSAParameters;
}
```

### Obter chave pública do RSA
```
public RSAParameters GetPublicKeyRSAParameters(string publicKey)
{
	RsaKeyParameters rsaPublicKeyParams;
	using (var sr = new StringReader(publicKey))
	{
		PemReader pemReader = new PemReader(sr);
		rsaPublicKeyParams = (RsaKeyParameters)pemReader.ReadObject();
	}

	RSAParameters rsaParameters = new RSAParameters
	{
		Modulus = rsaPublicKeyParams.Modulus.ToByteArrayUnsigned(),
		Exponent = rsaPublicKeyParams.Exponent.ToByteArrayUnsigned()
	};

	RSACryptoServiceProvider rsaProvider = new RSACryptoServiceProvider(2048);
	rsaProvider.ImportParameters(rsaParameters);

	RSAParameters publicKeyRSAParameters = rsaProvider.ExportParameters(false);

	return publicKeyRSAParameters;
}
```

### Gerando a RSASecurityKey
```
RsaSecurityKey securityKey = new RsaSecurityKey(rsaParameters)
```

### Gerando o objeto de Certificado RSA
```
using RSA rsaCertificate = RSA.Create(rsaParameters);
```
