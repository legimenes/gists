## Comandos do Docker

#### Exibir detalhes do Docker
```
docker info
```

### Imagens
---

#### Listar todas as imagens
```
docker images -a
```

#### Exibir informações detalhadas de uma imagem específica
```
docker image inpect {image_name}
```

#### Remover uma imagem específica
```
docker image rm {image_name}
```

#### Remover imagens pendentes (camadas que não têm relação com nenhuma imagem marcada)
```
docker images purge
```

### Containers
---

#### Listar todos os containers
```
docker ps -a
```

#### Criar um container
> Flags:</br>
-d = rodar em background (sem esperar comandos no prompt)</br>
-it = modo interativo (aguarda interação)</br>
--restart = inicializa o container automaticamente quando o docker inicializar
```
docker run [-d|-it] --name {container_name} [--restart always] {image_name}
```

#### Inicializar um container específico
```
docker start {container_name}
```

#### Inicializer um container automaticamente
> Flags:</br>
no = não inicializar automaticamente (default)</br>
on-failure = reinicializar somente em caso de erro</br>
always = sempre reinicializa o container se parar, se for parado manualmente é reinicializado somente quando o Docker daemon iniciar ou for inicializado manualmente</br>
unless-stopped = igual o always, exceto que se for parado manualmente não é reinicializado mesmo depois que o Docker daemon iniciar

#### Configurando a política de restart para um container parado
```
docker run -d --restart {no|on-failure|always|unless-stopped} {container_name}
```

#### Configurando a política de restart para um container em execução
```
docker update --restart {no|on-failure|always|unless-stopped} {container_name}
```

#### Exibir a data de um container específico
```
docker exec -it {container_id} date
```

#### Executar o shell de um container que possua o recurso
```
docker exec -it {container_id} bash
```

#### Remover um container específico
```
docker container rm {container_id}
```

### Redes
---

#### Listar as redes
```
docker network ls
```

### Gerenciamento
---

#### Remover imagens, containers parados, volumes e redes que estão pendentes (não associados a um container)
> Flags:</br>
-a = remove adicionalmente quaisquer containeres e todas as imagens não utilizadas (não apenas imagens pendentes)
```
docker system prune [-a]
```

#### Copiar arquivo do host para um container
```
docker cp {path_do_diretorio_com_arquivo} container_id:/{path_do_diretorio_com_arquivo}
```
