# Code Review Checklist

Use esta checklist ao realizar code reviews para garantir cobertura completa.

## 🎯 Antes de Começar

- [ ] Li a descrição do PR e entendi o objetivo
- [ ] Revisei a issue relacionada (se houver)
- [ ] Entendi o contexto e motivação das mudanças
- [ ] Verifico se o PR é de tamanho razoável (< 400 linhas idealmente)

## ✅ Funcionalidade

### Correção
- [ ] O código faz o que a descrição diz que faz?
- [ ] A lógica está correta?
- [ ] Casos edge são tratados?
- [ ] Validações apropriadas existem?
- [ ] Tratamento de erros está adequado?

### Completude
- [ ] Todos os requisitos da issue foram atendidos?
- [ ] Features relacionadas foram consideradas?
- [ ] Não há TODOs não resolvidos críticos?
- [ ] Migrations necessárias foram criadas?

## 🏗️ Design e Arquitetura

### Estrutura
- [ ] Segue padrões de arquitetura do projeto?
- [ ] Separação de responsabilidades está clara?
- [ ] Classes/funções têm uma única responsabilidade?
- [ ] Abstrações fazem sentido?
- [ ] Não há código duplicado?

### Patterns
- [ ] Design patterns apropriados foram usados?
- [ ] SOLID principles foram seguidos?
- [ ] DRY (Don't Repeat Yourself) foi aplicado?
- [ ] Acoplamento está baixo?
- [ ] Coesão está alta?

### Escalabilidade
- [ ] Solução escala com aumento de dados?
- [ ] Performance foi considerada?
- [ ] Recursos são usados eficientemente?
- [ ] Código é extensível para futuras mudanças?

## 📝 Qualidade de Código

### Legibilidade
- [ ] Código é fácil de entender?
- [ ] Nomes de variáveis/funções são descritivos?
- [ ] Funções têm tamanho apropriado (< 50 linhas)?
- [ ] Complexidade ciclomática é baixa?
- [ ] Indentação e formatação estão corretas?

### Comentários
- [ ] Comentários explicam o "porquê", não o "o quê"?
- [ ] Código complexo está comentado?
- [ ] Não há comentários obsoletos?
- [ ] JSDoc/TSDoc em funções públicas?
- [ ] TODOs têm contexto e responsável?

### Convenções
- [ ] Style guide do projeto foi seguido?
- [ ] Naming conventions estão corretas?
- [ ] Estrutura de arquivos segue padrão?
- [ ] Imports organizados e ordenados?
- [ ] Linter passou sem erros?

## 🚀 Performance

### Algoritmos
- [ ] Complexidade algorítmica é apropriada?
- [ ] Não há loops desnecessários?
- [ ] Operações custosas são evitadas quando possível?
- [ ] Recursão é usada apropriadamente?

### Database
- [ ] Queries estão otimizadas?
- [ ] Índices necessários foram criados?
- [ ] N+1 queries foram evitadas?
- [ ] Batch operations usadas quando apropriado?
- [ ] Connection pooling considerado?

### Recursos
- [ ] Memória é gerenciada apropriadamente?
- [ ] File handles são fechados?
- [ ] Connections são liberadas?
- [ ] Cache é usado onde faz sentido?
- [ ] Lazy loading considerado?

### Frontend Específico
- [ ] Bundle size não aumentou significativamente?
- [ ] Code splitting usado apropriadamente?
- [ ] Lazy loading de componentes considerado?
- [ ] Imagens otimizadas?
- [ ] Renders desnecessários evitados?

## 🔐 Segurança

### Input Validation
- [ ] Todos os inputs são validados?
- [ ] Sanitização apropriada está presente?
- [ ] Type checking implementado?
- [ ] Limites de tamanho verificados?
- [ ] Formato de dados validado?

### Vulnerabilidades
- [ ] SQL injection prevenido?
- [ ] XSS protection implementada?
- [ ] CSRF protection presente (se aplicável)?
- [ ] Path traversal prevenido?
- [ ] Command injection bloqueado?

### Autenticação/Autorização
- [ ] Autenticação verificada onde necessário?
- [ ] Autorização apropriada implementada?
- [ ] Tokens/sessions gerenciados corretamente?
- [ ] Rate limiting considerado?
- [ ] Brute force protection?

### Dados Sensíveis
- [ ] Secrets não estão hardcoded?
- [ ] Senhas são hasheadas (nunca plaintext)?
- [ ] Dados sensíveis não aparecem em logs?
- [ ] PII é tratado apropriadamente?
- [ ] Compliance (GDPR, LGPD) considerado?

### Dependencies
- [ ] Novas dependências são necessárias?
- [ ] Dependências estão atualizadas?
- [ ] Não há vulnerabilidades conhecidas?
- [ ] Licenças são compatíveis?

## 🧪 Testes

### Cobertura
- [ ] Testes unitários foram adicionados?
- [ ] Testes de integração quando necessário?
- [ ] Casos edge estão cobertos?
- [ ] Cobertura é adequada (>80%)?
- [ ] Testes E2E para fluxos críticos?

### Qualidade
- [ ] Testes são significativos?
- [ ] Testes são independentes?
- [ ] Mocks são apropriados?
- [ ] Assertions são específicas?
- [ ] Testes são rápidos?
- [ ] Testes passam consistentemente?

### Cenários
- [ ] Happy path testado?
- [ ] Error cases testados?
- [ ] Edge cases cobertos?
- [ ] Null/undefined tratados?
- [ ] Boundary conditions testados?

## 📚 Documentação

### Código
- [ ] Funções complexas têm comentários?
- [ ] Decisões não óbvias explicadas?
- [ ] JSDoc/TSDoc em APIs públicas?
- [ ] Type definitions completas?

### Projeto
- [ ] README atualizado se necessário?
- [ ] CHANGELOG.md atualizado?
- [ ] API documentation atualizada?
- [ ] Migration guides fornecidos (breaking changes)?
- [ ] Exemplos de uso adicionados?

### Configuração
- [ ] .env.example atualizado?
- [ ] Novas variáveis documentadas?
- [ ] Setup instructions atualizadas?
- [ ] Deployment notes fornecidas?

## 🔄 Manutenibilidade

### Código Limpo
- [ ] Sem código comentado/morto?
- [ ] Sem console.logs em produção?
- [ ] Sem debugging code?
- [ ] Imports não usados removidos?
- [ ] Variáveis não usadas removidas?

### Debt Técnico
- [ ] Não introduz debt técnico significativo?
- [ ] TODOs são razoáveis?
- [ ] Workarounds estão documentados?
- [ ] Problemas conhecidos documentados?

### Futuro
- [ ] Código é extensível?
- [ ] Fácil de modificar no futuro?
- [ ] Não cria amarras desnecessárias?
- [ ] Backward compatibility considerada?

## 🎨 UI/UX (Frontend)

### Visual
- [ ] Segue design system?
- [ ] Responsivo em diferentes tamanhos?
- [ ] Browsers suportados testados?
- [ ] Visual consistente com resto da app?

### Acessibilidade
- [ ] Navegação por teclado funciona?
- [ ] Screen reader friendly?
- [ ] Contraste de cores adequado?
- [ ] ARIA labels apropriados?
- [ ] Foco visível em elementos interativos?

### Experiência
- [ ] Loading states implementados?
- [ ] Error states tratados?
- [ ] Feedback para ações do usuário?
- [ ] Validações de formulário claras?
- [ ] Performance percebida é boa?

## 🚢 Deploy

### Configuração
- [ ] Variáveis de ambiente documentadas?
- [ ] Configurações de produção corretas?
- [ ] Feature flags consideradas?
- [ ] Rollback plan documentado?

### Migrations
- [ ] Database migrations testadas?
- [ ] Rollback migrations funcionam?
- [ ] Data migration strategy clara?
- [ ] Downtime minimizado?

### Monitoring
- [ ] Logs apropriados adicionados?
- [ ] Métricas consideradas?
- [ ] Alertas configurados?
- [ ] Observabilidade mantida?

## ✅ Final

### CI/CD
- [ ] Build passou?
- [ ] Todos os testes passaram?
- [ ] Lint passou?
- [ ] Type check passou?
- [ ] Security scan passou?
- [ ] Coverage check passou?

### Review
- [ ] Todos os comentários foram endereçados?
- [ ] Issues bloqueantes resolvidos?
- [ ] Aprovações necessárias obtidas?
- [ ] Merge conflicts resolvidos?

### Confiança
- [ ] Me sinto confortável com este código em produção?
- [ ] Entendo completamente as mudanças?
- [ ] Confio que não quebrará nada?
- [ ] Estou feliz em dar manutenção neste código?

## 📊 Níveis de Severidade

Use para priorizar feedback:

### 🔴 Bloqueante (P0)
- Bugs críticos
- Vulnerabilidades de segurança
- Perda de dados possível
- Breaking changes não documentados

### 🟡 Importante (P1)
- Bugs não críticos
- Problemas de performance
- Violações de padrões importantes
- Testes inadequados

### 🟢 Sugestão (P2)
- Melhorias de legibilidade
- Otimizações menores
- Refatorações sugeridas
- Comentários adicionais

## 💡 Dicas

1. Foque no que importa - não nitpick em estilo (use linter)
2. Seja construtivo - sugira soluções
3. Faça perguntas - assuma boa intenção
4. Aprenda - cada review é oportunidade de crescimento
5. Seja oportuno - revise em tempo hábil
6. Celebre - reconheça bom código

## 🎯 Priorização

1. **Primeiro**: Segurança e correção
2. **Segundo**: Performance e escalabilidade
3. **Terceiro**: Manutenibilidade e legibilidade
4. **Último**: Style e preferências pessoais
