# Guia da distribuição Debian
by **Leandro Gimenes**

## Índice
[Histórico de versões](#histórico-de-versões)  
[DFSG](#dfsg)  
[Download](#download)  
[Instalação](#instalação)  
[Modo root](#modo-root)  
&nbsp;&nbsp;[Comando su](#comando-su)  
&nbsp;&nbsp;[Configurar usuário como root](#configurar-usuário-como-root)  
&nbsp;&nbsp;[Comando sudo](#comando-sudo)  

<div style="page-break-before: always;"></div>

## Histórico de versões
| Versão | Nome | Lançamento |
| - | - | - |
| 12.0 | Bookworm | 10 de junho de 2023 |
| 11.0 | Bullseye | 14 de agosto de 2021 |
| 10.0 | Buster | 6 de julho de 2019 |
| 9.0 |	Stretch | 17 de junho de 2017 |
| 8.0 |	Jessie | 25/26 de abril de 2015 |
| 7.0 | Wheezy | 4 de maio de 2013 |
| 6.0 | Squeeze | 6 de fevereiro de 2011 |
| 5.0 |	Lenny | 14 de fevereiro de 2009 |
| 4.0 | Etch | 8 de abril de 2007 |
| 3.1 |	Sarge |	6 de junho de 2005 |
| 3.0 |	Woody |	19 de julho de 2002 |
| 2.2	| Potato | 14/15 de agosto de 2000 |
| 2.1	| Slink | 9 de março de 1999 |
| 2.0 |	Hamm | 24 de julho de 1998 |
| 1.3	| Bo | 5 de junho de 1997 |
| 1.2	| Rex	| 12 de dezembro de 1996 |
| 1.1 | Buzz | 17 de junho de 1996 |

## DFSG
O Debian possui uma filosofia rígida de priorizar software livre. O Debian só inclui software que segue a DFSG (Diretrizes de Software Livre da Debian), ou seja, programas e componentes com licenças que garantem total liberdade para os usuários (código aberto, modificável, distribuível, etc.). Os firmwares, pequenos programas de baixo nível usados para inicializar e operar certos hardware (como placas Wi-Fi, GPUs, etc.), que são proprietários (ou non-free) também não estão incluídos nos repositórios principais (main) do Debian.

A imagem ISO padrão do Debian (a chamada netinst ou a completa) só contém software livre. Se o seu hardware precisa de um firmware proprietário para funcionar, o instalador pode:
* Não reconhecer o hardware durante a instalação
* Exibir uma mensagem pedindo para você fornecer o firmware manualmente (geralmente via USB)

Embora o Debian seja purista com software livre, algumas soluções são oferecidas:
* Durante a instalação, se o instalador detectar que falta um firmware, é informado o nome do arquivo necessário (ex.: iwlwifi-7260-17.ucode), podendo ser baixado de outro computador, colocado num pendrive e fornecido ao instalador quando solicitado novamente
* O Debian disponibiliza ISOs não oficiais com a seção non-free-firmware incluída. Essas imagens têm os firmwares proprietários mais comuns já embutidos, facilitando a instalação em máquinas que dependem desses componentes
* A partir do Debian 12 (Bookworm), o Debian criou um repositório separado chamado non-free-firmware (antes, firmwares não-livres estavam no repositório non-free). Esse repositório contém firmwares proprietários que você pode habilitar manualmente.

## Download
Url de todas as imagens:  
https://cdimage.debian.org/images/

Url das imagens non-free incluíndo pacotes de firmware:  
https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/<br>
Selecionar: <versão>-live+nonfree/amd64/iso-hybrid

## Instalação

```bash
sudo dpkg -i /media/usb/<filename.deb>
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```

## Modo root

### Comando su
O comando **su -** (substitute user) permite que você mude para o usuário *root* no terminal. O **-** carrega o ambiente do root (como variáveis de sistema), garantindo que você tenha todas as configurações do root. Sem o **-**, você herda algumas configurações do usuário atual.
```bash
su -
```
O modo root está habilidado com o prompt mudando para algo como `root@hostname:#`

### Configurar usuário como root

Não é recomendado utilizar o sistema no modo *root*. É mais seguro configurar um usuário para ter acesso ao **sudo**:
```bash
su -
adduser <username> sudo
exit
```
Reiniciar a sessão para aplicar as modificações.


### Comando sudo
O comando **sudo** permite executar comandos como *root* sem precisar mudar completamente para o usuário *root*.
```bash
sudo [comando]
```
O sistema pedirá a senha de usuário (não a do *root*).


---
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

### Gerenciamento do SO
---

#### Versão da distribuição instalada
```
apt-get install lsb-release
```
```
lsb_release -a
```

#### Listar pacotes instalados
```
dpkg-query -l
dpkg-query -l [| grep nome_pacote]
```

#### Alterar o owner
```
chown [-R] <usuario> <pasta_ou_arquivo>
```

### Componentes externos
---

#### Conectar telefone
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
