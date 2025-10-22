# Code Review Guidelines

Diretrizes e boas práticas para realizar e receber code reviews efetivos.

## 📂 Estrutura

```
guidelines/
├── README.md                    # Este arquivo
├── code-review-checklist.md    # Checklist de review
├── pr-author-guide.md          # Guia para autores de PR
├── reviewer-guide.md           # Guia para reviewers
├── best-practices.md           # Boas práticas gerais
└── examples/                   # Exemplos de reviews
    ├── good-review.md
    └── bad-review.md
```

## 🎯 Objetivo

Code review efetivo:
- Melhora qualidade do código
- Compartilha conhecimento
- Detecta bugs antes de produção
- Mantém padrões consistentes
- Ensina e mentora o time
- Constrói cultura de colaboração

## 🔍 O que Revisar

### Funcionalidade
- [ ] O código faz o que deveria fazer?
- [ ] Casos edge estão cobertos?
- [ ] Lógica de negócio está correta?
- [ ] Validações apropriadas existem?

### Design e Arquitetura
- [ ] Segue padrões do projeto?
- [ ] Responsabilidades bem definidas?
- [ ] Acoplamento baixo, coesão alta?
- [ ] Reutilização apropriada?
- [ ] SOLID principles seguidos?

### Legibilidade
- [ ] Código é autoexplicativo?
- [ ] Nomes são descritivos?
- [ ] Complexidade é gerenciável?
- [ ] Comentários onde necessário?
- [ ] Formatação consistente?

### Performance
- [ ] Algoritmos eficientes?
- [ ] Queries otimizadas?
- [ ] Sem loops desnecessários?
- [ ] Recursos liberados apropriadamente?
- [ ] Caching onde apropriado?

### Segurança
- [ ] Input validation presente?
- [ ] SQL injection prevenido?
- [ ] XSS protection?
- [ ] Autenticação/autorização corretas?
- [ ] Secrets não expostos?
- [ ] Rate limiting considerado?

### Testes
- [ ] Cobertura adequada?
- [ ] Casos edge testados?
- [ ] Testes são significativos?
- [ ] Mocks apropriados?
- [ ] Testes de integração quando necessário?

### Documentação
- [ ] README atualizado?
- [ ] API documentada?
- [ ] Comentários em código complexo?
- [ ] Exemplos fornecidos?
- [ ] CHANGELOG atualizado?

### Manutenibilidade
- [ ] Fácil de entender?
- [ ] Fácil de modificar?
- [ ] Código duplicado minimizado?
- [ ] Dependências gerenciáveis?
- [ ] Debt técnico evitado?

## 👤 Para Autores de PR

### Antes de Submeter
1. **Self-review**: Revise seu próprio código primeiro
2. **Testes**: Garanta que todos passam
3. **Linting**: Código segue style guide
4. **Commits**: Mensagens claras e descritivas
5. **Tamanho**: PR focado e não muito grande
6. **Descrição**: Completa e clara

### Boas Práticas
- Mantenha PRs pequenos (< 400 linhas idealmente)
- Uma mudança lógica por PR
- Descreva o "porquê", não só o "o quê"
- Adicione screenshots/demos quando relevante
- Responda comentários construtivamente
- Não leve feedback pessoalmente
- Agradeça reviewers pelo tempo

### Respondendo a Comentários
- Seja receptivo ao feedback
- Faça perguntas se não entender
- Explique decisões se necessário
- Marque comentários como resolvidos
- Faça as mudanças sugeridas ou explique por que não

## 👥 Para Reviewers

### Princípios
1. **Seja Gentil**: Crítica construtiva, não pessoal
2. **Seja Específico**: Comentários claros e acionáveis
3. **Seja Oportuno**: Revise em tempo hábil
4. **Seja Colaborativo**: Trabalhem juntos para melhorar
5. **Seja Educativo**: Explique o "porquê"

### Como Comentar
✅ **Bom**:
```
Sugestão: Podemos extrair esta lógica para uma função separada
para melhorar testabilidade e reutilização.

Exemplo:
function validateEmail(email) {
  // validation logic
}
```

❌ **Ruim**:
```
Isso está errado. Refatore.
```

### Tipos de Comentários

**Blocking (deve ser corrigido)**:
```
🔴 BLOCKING: Esta validação permite SQL injection.
Precisamos sanitizar o input antes de usar na query.
```

**Importante (deve ser considerado)**:
```
🟡 IMPORTANTE: Esta abordagem pode causar N+1 queries.
Considere usar eager loading ou uma query JOIN.
```

**Sugestão (nice to have)**:
```
💡 SUGESTÃO: Este nome de variável poderia ser mais descritivo.
Que tal `activeUserCount` em vez de `count`?
```

**Questão (precisa clarificação)**:
```
❓ QUESTÃO: Por que escolhemos esta abordagem em vez de X?
Há alguma razão específica que não estou vendo?
```

**Elogio (reconhecimento)**:
```
✨ ELOGIO: Excelente uso de pattern matching aqui!
Muito mais legível que a versão anterior.
```

### Processo de Review

1. **Overview**: Entenda o contexto e objetivo
2. **Design**: Revise arquitetura e abordagem geral
3. **Code**: Revise implementação linha por linha
4. **Tests**: Verifique cobertura e qualidade
5. **Docs**: Confira documentação
6. **Summary**: Forneça feedback consolidado

### Priorização

**P0 - Crítico** (deve bloquear merge):
- Bugs severos
- Vulnerabilidades de segurança
- Breaking changes não documentados
- Perda de dados possível

**P1 - Importante** (deve ser endereçado):
- Problemas de performance
- Violações de padrões importantes
- Testes inadequados
- Design issues

**P2 - Nice to have** (pode ser endereçado depois):
- Melhorias de legibilidade
- Otimizações menores
- Sugestões de refatoração
- Comentários adicionais

## ⏱️ Timing

### SLA de Review
- Pequeno PR (< 100 linhas): 4 horas
- Médio PR (100-400 linhas): 1 dia
- Grande PR (> 400 linhas): 2 dias

### Quando Revisar
- Ao menos 2x por dia
- De manhã e tarde
- Priorize PRs bloqueantes
- Use notificações para alertas

## 🚫 Anti-padrões

### Para Autores
❌ PRs enormes (> 1000 linhas)
❌ Múltiplas features em um PR
❌ Descrição vaga ou ausente
❌ Testes não passando
❌ Ignorar comentários de review
❌ Forçar merge sem aprovações

### Para Reviewers
❌ Comentários vagos ("isso está ruim")
❌ Nitpicking excessivo em estilo
❌ Reescrever todo o código
❌ Delays longos em reviews
❌ Aprovar sem realmente revisar
❌ Comentários não construtivos

## 📊 Métricas de Sucesso

### Quantidade
- Tempo médio de review
- Número de iterações por PR
- Taxa de bugs escapados
- Cobertura de código

### Qualidade
- Satisfação do time
- Bugs encontrados em review
- Conhecimento compartilhado
- Melhoria contínua de código

## 🎓 Níveis de Review

### Nível 1 - Básico
- Funcionalidade correta
- Testes passando
- Sem erros óbvios

### Nível 2 - Intermediário
- Design e arquitetura
- Performance
- Segurança básica
- Legibilidade

### Nível 3 - Avançado
- Otimizações complexas
- Edge cases raros
- Implicações de arquitetura
- Escalabilidade futura

## 🔄 Automação

Use ferramentas para automatizar:
- Formatação de código (Prettier, ESLint)
- Type checking (TypeScript)
- Linting (ESLint, RuboCop)
- Testes automáticos (Jest, Pytest)
- Security scans (Snyk, Dependabot)
- Performance checks

Review humano foca em:
- Lógica de negócio
- Design e arquitetura
- Casos edge complexos
- Experiência do usuário
- Manutenibilidade

## ✅ Aprovação

Aprove quando:
- [ ] Funcionalidade está correta
- [ ] Qualidade de código é adequada
- [ ] Testes são suficientes
- [ ] Documentação está completa
- [ ] Não há issues bloqueantes
- [ ] Confortável com o código em produção

Request changes quando:
- Issues bloqueantes (P0/P1)
- Testes inadequados
- Bugs identificados
- Problemas de segurança
- Debt técnico significativo

## 💬 Cultura de Review

### Valores
- Respeito mútuo
- Crescimento contínuo
- Colaboração sobre competição
- Excelência técnica
- Feedback construtivo

### Etiqueta
- Assuma boa intenção
- Use "nós" em vez de "você"
- Faça perguntas, não acusações
- Celebre bom código
- Aprenda com cada review

## 📚 Recursos

- [Google Engineering Practices](https://google.github.io/eng-practices/review/)
- [Code Review Best Practices](https://blog.palantir.com/code-review-best-practices-19e02780015f)
- [The Art of Code Review](https://www.alexandra-hill.com/2018/06/25/the-art-of-giving-and-receiving-code-reviews/)
