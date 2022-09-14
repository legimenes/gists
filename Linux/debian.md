## Guia da distribuição Debian

### Download e instalação
---

#### Url da imagem para instalação:
https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/<br>
Selecionar: {versão}-live+nonfree/amd64/iso-hybrid

### root
---

#### Entrar no modo root
```
sudo -s
```

### apt
---

#### Atualizar apt
```
apt update
```

#### Atualizar pacotes instalados
```
apt upgrade
```

#### Exbir pacotes instalados
```
apt list --installed
```

#### Local das fontes de download do apt
```
cat /etc/apt/sources.list
```

### Monitoramento do SO
---

#### Versao do debian instalado
```
apt install lsb-release
```
```
lsb_release -a
```

### Instalação de aplicações
---

#### SDK do .NET
Download
```
wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
```
SDK do .NET
```
sudo apt-get update && \
sudo apt-get install -y dotnet-sdk-6.0
```
Runtime do .NET
```
sudo apt-get update && \
sudo apt-get install -y aspnetcore-runtime-6.0
```
