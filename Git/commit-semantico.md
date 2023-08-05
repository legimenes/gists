## Commit semânticos

### Formatação
```
feat: adicionando log
^--^  ^-------------^
|     |
|     +-> Resumo no tempo presente.
|
+-------> tipo: chore, ci, docs, feat, fix, refactor, style, ou test.
```

### Tipos

`build`: (anteriormente conhecido como chore) usado para identificar alterações aos recursos de compilação (envolvendo scripts, configurações ou ferramentas) e dependências de pacotes.

`ci`: usado para identificar mudanças relacionadas ao sistema de integração e implantação contínua - envolvendo scripts, configurações ou ferramentas.

`docs`: usado para identificar mudanças na documentação relacionadas ao projeto.

`feat`: usado para identificar novas funcionalidades para o usuário mantendo a compatibilidade com versões anteriores. Não deve ser usado para identificar scripts.

`fix`: usado para identificar correções de bugs mantendo a compatibilidade com versões anteriores. Não deve ser usado para identificar scripts.

`perf`: usado para identificar alterações de desenvolvimento relacionadas a melhorias de desempenho compatíveis com versões anteriores.

`refactor`: usado para identificar alterações de refatoração de código que não adiciona funcionalidades ou corrige bugs. Exemplo: remover código redundante, simplificar o código, renomear variáveis ​​e etc.

`style`: usado para identificar alterações de código relacionadas ao estilo como recuos, ponto e vírgula, aspas, vírgulas à direita e etc.

`test`: usado para identificar alterações de código relacionadas a testes como refatorar testes existentes ou adicionar novos testes.
