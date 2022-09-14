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
