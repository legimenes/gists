# Guia da distribuição Ubuntu

## Índice
[**Download e instalação do SO**](#download-e-instalação-do-so)  
[**Configurações do SO**](#configurações-do-so)  
&nbsp;&nbsp;[Region and languages](#region-and-languages)  
[**Usuário root**](#usuário-root)  
&nbsp;&nbsp;[Entrar em modo root](#entrar-em-modo-root)  
[**apt**](#apt)  
&nbsp;&nbsp;[Atualizar apt](#atualizar-apt)  
&nbsp;&nbsp;[Atualizar pacotes instalados](#atualizar-pacotes-instalados)  
&nbsp;&nbsp;[Exbir pacotes instalados](#exbir-pacotes-instalados)  
&nbsp;&nbsp;[Remover pacote específico instalado](#remover-pacote-específico-instalado)  
&nbsp;&nbsp;[Remover pacotes não utilizados](#remover-pacotes-não-utilizados)  
&nbsp;&nbsp;[Local das fontes de download do apt](#local-das-fontes-de-download-do-apt)  
[**Gerenciamento do SO**](#gerenciamento-do-so)  
&nbsp;&nbsp;[Checar informações do sistema](#checar-informações-do-sistema)  
&nbsp;&nbsp;[Alterar hostname](#alterar-hostname)  
&nbsp;&nbsp;[Criar bash scripts](#criar-bash-scripts)  
[**Wine**](#wine)  
&nbsp;&nbsp;[Checar versão instalada](#checar-versão-instalada)  
&nbsp;&nbsp;[Configurar diretório do wine](#configurar-diretório-do-wine)  
&nbsp;&nbsp;[Executar aplicação windows](#executar-aplicação-windows)  
&nbsp;&nbsp;[Desinstalar aplicação windows](#desinstalar-aplicação-windows)  

## Download e instalação do SO

Seguir as instruções em: https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview

## Configurações do SO

### Region and languages

Keyboard|Language|Formats|Input sources
-|-|-|-
non ABNT2|English (United States)|Brasil|English (US, intl, with dead keys)

## Usuário root

### Entrar em modo root
```
sudo -s
```

## apt

### Atualizar apt
```
apt update
```

### Atualizar pacotes instalados
```
apt upgrade
```

### Exbir pacotes instalados
```
apt list
```
`--installed`: pacotes instalados

### Remover pacote específico instalado
```
apt remove <package-name>
```

Para remover também arquivos de configuração associados ao pacote
```
apt purge <package-name>
```

### Remover pacotes não utilizados
```
apt autoremove
```

### Local das fontes de download do apt
```
cd /etc/apt/sources.list.d
```

## Gerenciamento do SO

### Checar informações do sistema
**Versão atual da distribuição**
```
apt install lsb-release
lsb_release -a
```

**Detalhes da CPU**
```
lscpu
```

### Alterar hostname
Em novas instalações de SO o nome de usuário no terminal pode resultar em algo similar a `leandro@leandro-To-be-filled-by-O-E-M`. Para alterar o hostname executar o comando abaixo e reiniciar o SO.
```
sudo hostnamectl set-hostname <HOSTNAME>
```
Local onde fica definido o hostname
```
cd /sys/devices/virtual/dmi/id/modalias
```

### Criar bash scripts
1. Criar um arquivo com a extensão **.sh**  
2. Inlcuir na primeira linha do arquivo:
```
#!/bin/bash
```
3. Fazer o arquivo executável
```
chmod +x <filename>
```
4. Executar o script
```
./<filename>
```

## Wine

### Checar versão instalada
```
wine --version
```

### Configurar diretório do wine

Este comando cria o diretório de configuração do Wine, normalmente localizado em *~/.wine*. Este diretório funciona como o drive C: equivalente do Wine, onde as aplicações windows são instaladas e configuradas.
```
wineboot
```

### Executar aplicação windows
```
wine start <path/application.exe>
```

### Desinstalar aplicação windows
```
wine uninstaller
```
