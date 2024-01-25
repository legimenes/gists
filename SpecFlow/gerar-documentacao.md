## Gerar documentação do resultado da execução dos testes

### Dependências

SpecFlow.Plus.LivingDocPlugin

### Instalação da CLI LivingDoc

```
dotnet tool install --global SpecFlow.Plus.LivingDoc.CLI
```

### Gerar o relatório HTML

```
cd <path_projeto>\bin\<Debug|Release>\<versao_dotnet>
livingdoc test-assembly <nome_projeto_com_namespace>.dll -t TestExecution.json
```
