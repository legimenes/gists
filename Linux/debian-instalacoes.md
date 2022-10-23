## Instalações recomendadas para distribuição Debian

#### Pacotes básicos
---

```
apt-get install curl apt-transport-https lsb-release
```

### Pacotes para Desenvolvimento
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

### Pacotes para interface gráfica
---

#### Google Chrome
```
apt install wget
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
apt install ./google-chrome-stable_current_amd64.deb
```

#### stremio
```
wget https://dl.strem.io/shell-linux/v4.4.116/stremio_4.4.116-1_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/multiverse/f/fdk-aac/libfdk-aac1_0.1.5-1_amd64.deb 
sudo dpkg -i libfdk-aac1_0.1.5-1_amd64.deb
sudo apt install ./stremio_4.4.116-1_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/universe/x/x264/libx264-152_0.152.2854+gite9a5903-2_amd64.deb
sudo apt install ./libx264-152_0.152.2854+gite9a5903-2_amd64.deb
```

### qBitTorrent:
```
apt-get install qbittorrent
```

#### VS Code
```
apt install software-properties-common
apt install apt-transport-https
apt install curl
curl -sSL https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
apt update
apt install code
```
