## Comandos git

### Exibir status da branch de trabalho
```
git status
```

### Criar branch
```
git checkout -b <branch_name>
```

### Mudar de branch
```
git checkout <branch_name>
```

### Remover branch localmente
```
git branch -d <branch_name>
```

Obs.: Fetch para remover referências não usadas
```
git fetch --prune
```

### Publicar uma branch remotamente
```
git push -u origin <branch_name>
```

### Merge de branches
Mudar para a branch que vai receber o merge
```
git merge <branch_name>
```

### Fazendo commit e pull
```
git add .
git commit -m "<commit description>"
git pull <URL from repository>
```
