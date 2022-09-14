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
apt-get install lsb-release
```
```
lsb_release -a
```

### Componentes externos
---

#### Conectar Telefone
Instalar e criar diretório
```
apt install jmtpfs
mkdir -p ~/mnt/phone
```
Montar partição
```
jmtpfs ~/mnt/phone/
```
Desmontar partição
```
fusermount -u ~/mnt/phone
```
