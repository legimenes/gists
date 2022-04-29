## Gerenciando o Portainer

#### Baixar a imagem
```
docker pull portainer/portainer
```

#### Criar um container
> Flags:</br>
-d = rodar em background</br>
--name = nome do container</br>
-p = mapeamento das portas (porta local:porta container)</br>
--restart = habilita o reinício do container automaticamente</br>
-v /var/run/docker.sock:/var/run/docker.sock = permite gerenciar um ambiente Docker local</br>
-v = volume especificando o diretório de saída do sistema operacional
```
docker run -d --name portainer -p 7000:9000 --restart always -v /var/run/docker.sock:/var/run/docker.sock -v c:\lg\containers\portainer\data:/data portainer/portainer
```
