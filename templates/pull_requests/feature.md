---
name: Feature Pull Request
about: Template para PRs de novas features
title: '[FEATURE] '
labels: feature
assignees: ''
---

## 📝 Descrição

### Resumo
Breve descrição da feature implementada.

### Detalhes
Descrição detalhada das mudanças realizadas.

## 🔗 Issue Relacionada

Closes #[issue-number]

## 🎯 Tipo de Mudança

- [ ] Nova feature (mudança que adiciona funcionalidade)
- [ ] Breaking change (mudança que pode quebrar funcionalidade existente)
- [ ] Requer atualização de documentação
- [ ] Requer migração de dados

## 🖼️ Screenshots/Demo

Se aplicável, adicione screenshots ou GIFs demonstrando a funcionalidade.

**Antes:**
[Screenshot do estado anterior]

**Depois:**
[Screenshot do novo estado]

**Demo:**
[Link para vídeo demo ou GIF]

## 🧪 Como Testar

Instruções detalhadas para testar a feature:

1. Faça checkout desta branch
2. Rode `npm install` (se houver novas dependências)
3. Execute `npm run dev`
4. Vá para [URL/página]
5. Faça X, Y, Z
6. Verifique que [resultado esperado]

### Casos de Teste

**Caso 1: [Nome do cenário]**
- Passos: ...
- Resultado esperado: ...

**Caso 2: [Nome do cenário]**
- Passos: ...
- Resultado esperado: ...

## ✅ Checklist de Implementação

### Código
- [ ] Código segue style guide do projeto
- [ ] Self-review realizado
- [ ] Código comentado em partes complexas
- [ ] Sem console.log ou código de debug
- [ ] Sem código comentado/morto
- [ ] Variáveis e funções com nomes descritivos

### Testes
- [ ] Testes unitários adicionados/atualizados
- [ ] Testes de integração adicionados/atualizados
- [ ] Testes E2E adicionados (se aplicável)
- [ ] Todos os testes passam localmente
- [ ] Cobertura de testes mantida/aumentada

### Documentação
- [ ] README atualizado (se necessário)
- [ ] Documentação de API atualizada (se aplicável)
- [ ] Comentários JSDoc/TSDoc adicionados
- [ ] CHANGELOG.md atualizado
- [ ] Exemplos de uso adicionados

### Performance
- [ ] Não introduz regressão de performance
- [ ] Queries otimizadas (se aplicável)
- [ ] Bundle size verificado (frontend)
- [ ] Lazy loading considerado onde apropriado

### Segurança
- [ ] Input validation implementada
- [ ] Autenticação/autorização verificada
- [ ] Secrets não commitados
- [ ] Dependências seguras
- [ ] OWASP Top 10 considerado

### Acessibilidade (Frontend)
- [ ] Navegação por teclado funciona
- [ ] Labels apropriadas em elementos de formulário
- [ ] Contraste de cores adequado
- [ ] Screen reader friendly
- [ ] ARIA attributes quando necessário

### Compatibilidade
- [ ] Testado em Chrome
- [ ] Testado em Firefox
- [ ] Testado em Safari
- [ ] Testado em Edge
- [ ] Mobile responsivo (se aplicável)

### Database
- [ ] Migrations criadas (se aplicável)
- [ ] Rollback testado (se aplicável)
- [ ] Índices adicionados onde necessário
- [ ] Performance de queries verificada

## 🔄 Dependências

### Novas Dependências
Lista de novos pacotes adicionados:

```json
{
  "package-name": "version"
}
```

**Justificativa**: Por que esta dependência é necessária?

### Dependências Atualizadas
```json
{
  "package-name": "old-version → new-version"
}
```

**Breaking Changes**: Listar breaking changes relevantes.

## 🚨 Breaking Changes

Se esta feature introduz breaking changes:

### Mudanças
- [ ] Alteração na API pública
- [ ] Mudança no schema do banco
- [ ] Mudança em variáveis de ambiente
- [ ] Mudança em configurações

### Descrição dos Breaking Changes
Descreva detalhadamente o que mudou e o impacto.

### Migration Guide
Como migrar da versão anterior:

1. Passo 1
2. Passo 2
3. Passo 3

## 🎯 Impacto

### Componentes Afetados
- [ ] Frontend
- [ ] Backend
- [ ] Database
- [ ] API
- [ ] Infraestrutura
- [ ] Documentação

### Estimativa de Risco
**Risco**: [Alto/Médio/Baixo]

**Justificativa**: Por que este é o nível de risco?

## 📊 Métricas

### Performance
- Tempo de resposta: [antes → depois]
- Uso de memória: [antes → depois]
- Bundle size: [antes → depois]

### Cobertura de Testes
- Antes: X%
- Depois: Y%

## 🔍 Review Focus Areas

Áreas que requerem atenção especial durante review:

1. [Área 1]: [Por que precisa atenção]
2. [Área 2]: [Por que precisa atenção]

## 📸 Evidências

### Testes Passando
[Screenshot dos testes passando]

### CI/CD Status
- [ ] Build passou
- [ ] Testes passaram
- [ ] Lint passou
- [ ] Type check passou
- [ ] Security scan passou

## 🔗 Links Úteis

- [Documentação relacionada]
- [Design/Mockup]
- [Issue de discussão]
- [ADR (se aplicável)]

## 💬 Notas para Reviewers

Informações adicionais que podem ajudar na review:

- Decisões de design importantes
- Trade-offs considerados
- Áreas que precisam de atenção especial
- Dúvidas ou incertezas

## 🚀 Deploy Notes

### Pré-requisitos para Deploy
- [ ] Variáveis de ambiente configuradas
- [ ] Migrations executadas
- [ ] Configurações atualizadas

### Steps para Deploy
1. Passo 1
2. Passo 2
3. Passo 3

### Rollback Plan
Como fazer rollback se algo der errado:
1. Passo 1
2. Passo 2

## ✅ Aprovações Necessárias

- [ ] Code review (mínimo 2 aprovações)
- [ ] QA/Testing
- [ ] Product Owner
- [ ] Security review (se aplicável)
- [ ] Architecture review (se breaking changes)

## 📝 Notas Adicionais

Qualquer informação adicional relevante.
