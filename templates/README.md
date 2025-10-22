# Templates

Templates para issues e pull requests que padronizam a comunicação e documentação.

## 📂 Estrutura

```
templates/
├── README.md              # Este arquivo
├── issues/               # Templates de issues
│   ├── bug-report.md
│   ├── feature-request.md
│   ├── task.md
│   └── question.md
└── pull_requests/        # Templates de PRs
    ├── feature.md
    ├── bugfix.md
    ├── refactoring.md
    └── documentation.md
```

## 🎯 Objetivo

Templates ajudam a:
- Garantir informações completas
- Padronizar comunicação
- Facilitar triagem e priorização
- Acelerar reviews e aprovações
- Documentar decisões e mudanças

## 📝 Templates de Issues

### Bug Report
Para reportar bugs e problemas

**Quando usar**: Algo não está funcionando como esperado

**Inclui**:
- Descrição do problema
- Passos para reproduzir
- Comportamento esperado vs atual
- Screenshots/logs
- Ambiente (OS, browser, versões)

### Feature Request
Para solicitar novas funcionalidades

**Quando usar**: Propor nova feature ou melhoria

**Inclui**:
- Descrição da feature
- Motivação e valor
- Proposta de solução
- Alternativas consideradas
- Impacto e complexidade

### Task
Para tarefas técnicas e melhorias

**Quando usar**: Trabalho técnico sem ser bug ou feature

**Inclui**:
- Descrição da tarefa
- Contexto e motivação
- Critérios de aceitação
- Checklist de ações
- Estimativa de esforço

### Question
Para dúvidas e discussões

**Quando usar**: Esclarecer dúvidas sobre o projeto

**Inclui**:
- Pergunta clara
- Contexto
- O que já foi tentado
- Informações relevantes

## 📝 Templates de Pull Requests

### Feature
Para novas funcionalidades

**Quando usar**: Adicionar nova feature

**Inclui**:
- Descrição da mudança
- Issue relacionada
- Tipo de mudança
- Screenshots/demos
- Checklist de revisão
- Testes adicionados

### Bugfix
Para correções de bugs

**Quando usar**: Corrigir um bug

**Inclui**:
- Descrição do bug
- Issue relacionada
- Root cause
- Solução implementada
- Testes adicionados
- Regression tests

### Refactoring
Para refatorações

**Quando usar**: Melhorar código sem mudar comportamento

**Inclui**:
- Motivação da refatoração
- Mudanças realizadas
- Impacto em performance/legibilidade
- Testes mantidos/atualizados
- Breaking changes (se houver)

### Documentation
Para atualizações de documentação

**Quando usar**: Melhorar ou adicionar documentação

**Inclui**:
- Tipo de documentação
- Motivação
- Mudanças realizadas
- Links para docs relacionadas

## 🔧 Como Usar

### Para Issues
1. Ao criar issue, selecione o template apropriado
2. Preencha todas as seções obrigatórias
3. Adicione labels relevantes
4. Adicione a um projeto/milestone se aplicável

### Para Pull Requests
1. Ao criar PR, selecione o template apropriado
2. Preencha todas as seções
3. Marque os itens do checklist
4. Solicite reviewers apropriados
5. Link issues relacionadas

## ✨ Boas Práticas

### Issues
- Seja específico e objetivo
- Adicione contexto suficiente
- Use formatação markdown
- Adicione screenshots quando relevante
- Mantenha uma issue por problema/feature
- Use labels para categorização
- Atualize a issue conforme progride

### Pull Requests
- Um PR por feature/fix
- Título descritivo e conciso
- Descrição detalhada de mudanças
- Link para issue relacionada
- Testes adicionados/atualizados
- Documentação atualizada
- CI/CD passando
- Código revisado pelo autor antes de submeter
- Mantenha PRs focados e pequenos

## 📋 Checklist Geral

### Antes de Criar Issue
- [ ] Busquei issues existentes similares
- [ ] Li a documentação relacionada
- [ ] Tentei reproduzir/entender o problema
- [ ] Coletei informações necessárias

### Antes de Criar PR
- [ ] Código está completo e funcional
- [ ] Testes passam localmente
- [ ] Adicionei novos testes quando necessário
- [ ] Atualizei documentação
- [ ] Segui guia de estilo do projeto
- [ ] Fiz self-review do código
- [ ] Comentei código complexo
- [ ] Nenhuma mudança não relacionada

## 🎓 GitHub Features

### Issue Templates
Configure templates padrão em `.github/ISSUE_TEMPLATE/`

### PR Templates
Configure template padrão em `.github/pull_request_template.md`

### Labels
Use labels para categorizar:
- `bug`, `feature`, `documentation`, `question`
- `priority: high/medium/low`
- `status: in-progress/blocked/review`
- `type: breaking-change`

### Automation
Use GitHub Actions para:
- Auto-assign reviewers
- Auto-label baseado em paths
- Validar checklist preenchido
- Executar testes em PRs

## Recursos
- [GitHub Issues Documentation](https://docs.github.com/en/issues)
- [GitHub PR Documentation](https://docs.github.com/en/pull-requests)
