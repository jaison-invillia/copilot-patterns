# Guia Completo do Copilot Patterns

Este documento fornece uma visão geral completa do repositório e como utilizá-lo com GitHub Copilot Spaces.

## 📊 Visão Geral

O **Copilot Patterns** é um repositório centralizado que organiza:

- ✨ **Prompts Reutilizáveis** - Templates de prompts para diferentes cenários
- 💬 **Chat Modes** - Configurações de comportamento do Copilot Chat
- 📖 **Instructions** - Diretrizes para geração de código
- 🏗️ **Architecture Templates** - Padrões de arquitetura de projetos
- 📋 **Issue/PR Templates** - Templates padronizados
- ✅ **Code Review Guidelines** - Diretrizes de revisão de código

## 🗂️ Estrutura Completa

```
copilot-patterns/
│
├── 📁 .copilot/                       # Configurações do GitHub Copilot Spaces
│   └── config.yml                    # Arquivo de configuração principal
│
├── 📁 prompts/                        # Prompts reutilizáveis organizados por categoria
│   ├── README.md                     # Guia de uso de prompts
│   ├── code-generation/              # Geração de código
│   │   └── api-endpoint.md          # Criar endpoints REST
│   ├── testing/                      # Testes
│   │   └── unit-tests.md            # Criar testes unitários
│   ├── refactoring/                  # Refatoração
│   │   └── performance.md           # Otimização de performance
│   ├── debugging/                    # Debugging
│   │   └── common-issues.md         # Problemas comuns
│   └── documentation/                # Documentação
│       └── common-docs.md           # Docs comuns
│
├── 📁 chatmodes/                      # Chat modes customizados
│   ├── README.md                     # Guia de chat modes
│   ├── code-reviewer.yml             # Mode para code review
│   └── architect.yml                 # Mode para arquitetura
│
├── 📁 instructions/                   # Instruções para o Copilot
│   ├── README.md                     # Guia de instruções
│   ├── languages/                    # Por linguagem de programação
│   │   └── typescript.md            # TypeScript guidelines
│   ├── frameworks/                   # Por framework
│   ├── tasks/                        # Por tipo de tarefa
│   └── best-practices/               # Boas práticas gerais
│       └── security.md              # Segurança
│
├── 📁 architecture/                   # Templates de arquitetura
│   ├── README.md                     # Guia de arquitetura
│   ├── backend/                      # Arquiteturas backend
│   │   └── rest-api.md              # REST API completo
│   ├── frontend/                     # Arquiteturas frontend
│   ├── full-stack/                   # Arquiteturas full-stack
│   ├── data/                         # Arquiteturas de dados
│   └── patterns/                     # Padrões arquiteturais
│
├── 📁 templates/                      # Templates de issues e PRs
│   ├── README.md                     # Guia de templates
│   ├── issues/                       # Templates de issues
│   │   ├── bug-report.md            # Reportar bugs
│   │   └── feature-request.md       # Solicitar features
│   └── pull_requests/                # Templates de PRs
│       └── feature.md               # PR de feature
│
├── 📁 guidelines/                     # Diretrizes de code review
│   ├── README.md                     # Guia completo
│   └── code-review-checklist.md     # Checklist detalhado
│
├── 📄 README.md                       # Este arquivo - Documentação principal
├── 📄 CONTRIBUTING.md                 # Guia de contribuição
└── 📄 .gitignore                      # Arquivos ignorados pelo Git
```

## 🚀 Como Usar Este Repositório

### 1. Com GitHub Copilot Chat

#### Usar Prompts
```
Use o prompt em prompts/code-generation/api-endpoint.md 
para criar um endpoint REST para gerenciar produtos
```

#### Ativar Chat Mode
```
Ative o chat mode "Code Reviewer" e revise este código:
[seu código aqui]
```

### 2. Com GitHub Copilot Spaces

O repositório está configurado para uso direto com Copilot Spaces através do arquivo `.copilot/config.yml`.

**Recursos habilitados:**
- Auto-sugestão de prompts
- Chat modes customizados
- Instruções aplicadas automaticamente
- Referência a arquitetura e guidelines

### 3. Como Referência

Navegue pelos diretórios para encontrar:
- Exemplos de código
- Boas práticas
- Templates reutilizáveis
- Padrões estabelecidos

## 📚 Guias Detalhados por Seção

### Prompts (`/prompts`)

**O que são:** Templates de instruções reutilizáveis para o Copilot.

**Quando usar:** Quando precisar de código específico seguindo padrões estabelecidos.

**Categorias disponíveis:**
- **code-generation:** Gerar novos componentes e funcionalidades
- **testing:** Criar e melhorar testes
- **refactoring:** Melhorar código existente
- **debugging:** Identificar e corrigir bugs
- **documentation:** Criar documentação

**Como criar novos prompts:** Veja `prompts/README.md`

### Chat Modes (`/chatmodes`)

**O que são:** Configurações que definem o comportamento do Copilot Chat.

**Quando usar:** Para ter assistência especializada em diferentes contextos.

**Modes disponíveis:**
- **code-reviewer:** Revisão de código focada em qualidade
- **architect:** Decisões arquiteturais e design de sistemas

**Como criar novos modes:** Veja `chatmodes/README.md`

### Instructions (`/instructions`)

**O que são:** Diretrizes detalhadas para desenvolvimento em tecnologias específicas.

**Quando usar:** Como referência ao trabalhar com uma linguagem ou framework.

**Organizadas por:**
- **languages:** Python, TypeScript, Java, etc.
- **frameworks:** React, Node.js, .NET, etc.
- **tasks:** API development, testing, deployment
- **best-practices:** Security, performance, code quality

**Como adicionar instruções:** Veja `instructions/README.md`

### Architecture (`/architecture`)

**O que são:** Templates completos de arquitetura de projetos.

**Quando usar:** Ao iniciar novo projeto ou reestruturar existente.

**Tipos disponíveis:**
- **backend:** REST API, GraphQL, Microservices, Serverless
- **frontend:** SPA, SSR, Micro-frontends
- **full-stack:** Monorepo, JAMstack
- **data:** Data Lake, Data Warehouse, Real-time
- **patterns:** Event-Driven, CQRS, Clean Architecture

**Como usar templates:** Veja `architecture/README.md`

### Templates (`/templates`)

**O que são:** Templates padronizados para issues e pull requests.

**Quando usar:** Ao criar issues ou PRs para manter consistência.

**Disponíveis:**
- **Issues:** bug-report, feature-request, task, question
- **Pull Requests:** feature, bugfix, refactoring, documentation

**Como usar templates:** Veja `templates/README.md`

### Guidelines (`/guidelines`)

**O que são:** Diretrizes detalhadas para code review.

**Quando usar:** Ao revisar código ou preparar PRs.

**Inclui:**
- Checklist completo de review
- Guia para autores de PR
- Guia para reviewers
- Boas práticas e exemplos

**Como fazer bons reviews:** Veja `guidelines/README.md`

## 🎯 Casos de Uso Comuns

### Caso 1: Criar Nova API REST

1. Consulte `architecture/backend/rest-api.md` para estrutura
2. Use `prompts/code-generation/api-endpoint.md` para criar endpoints
3. Siga `instructions/languages/typescript.md` para TypeScript
4. Aplique `instructions/best-practices/security.md` para segurança
5. Crie testes com `prompts/testing/unit-tests.md`

### Caso 2: Revisar Pull Request

1. Use chat mode `code-reviewer`
2. Siga `guidelines/code-review-checklist.md`
3. Consulte `instructions/best-practices/security.md` para segurança
4. Verifique conformidade com `architecture/` do projeto

### Caso 3: Debugar Problema

1. Use prompts em `prompts/debugging/common-issues.md`
2. Ative chat mode `architect` para problemas arquiteturais
3. Consulte `instructions/` relevantes
4. Documente solução em `templates/pull_requests/bugfix.md`

### Caso 4: Documentar Feature

1. Use `prompts/documentation/common-docs.md`
2. Siga padrões em `templates/`
3. Atualize `architecture/` se aplicável
4. Submeta PR usando template apropriado

## 🔧 Configuração do Copilot Spaces

O arquivo `.copilot/config.yml` configura:

```yaml
# Habilita recursos avançados
advanced_features: true

# Diretórios que o Copilot usa como referência
reference_directories:
  - prompts
  - chatmodes
  - instructions
  - architecture
  - templates
  - guidelines

# Auto-sugestão de prompts
prompts:
  enabled: true
  auto_suggest: true

# Chat modes customizados
chat_modes:
  enabled: true
  modes_directory: "chatmodes"

# Instruções aplicadas automaticamente
instructions:
  enabled: true
  apply_on_startup: true
```

## 📖 Recursos Adicionais

### Documentação
- `README.md` - Visão geral principal
- `CONTRIBUTING.md` - Como contribuir
- Cada diretório tem seu próprio README

### Padrões
- Conventional Commits para mensagens de commit
- Markdown para toda documentação
- YAML para configurações
- Kebab-case para nomes de arquivos

### Ferramentas Recomendadas
- GitHub Copilot (obrigatório)
- GitHub Copilot Chat (recomendado)
- VSCode ou editor compatível
- Markdown preview

## 🤝 Contribuindo

Adoraríamos suas contribuições! Veja `CONTRIBUTING.md` para:
- Como adicionar novos patterns
- Padrões de qualidade
- Processo de review
- Convenções do projeto

## 🎓 Melhores Práticas

### Ao Usar Este Repositório

1. **Explore primeiro:** Navegue pelos diretórios antes de criar novo conteúdo
2. **Adapte, não copie:** Use como inspiração e adapte ao seu contexto
3. **Contribua melhorias:** Encontrou algo útil? Compartilhe!
4. **Mantenha atualizado:** Pull as últimas mudanças regularmente
5. **Dê feedback:** Abra issues com sugestões

### Ao Contribuir

1. **Qualidade sobre quantidade:** Prefira exemplos completos e bem documentados
2. **Seja específico:** Evite generalidades, forneça código real
3. **Teste seus exemplos:** Garanta que código funciona
4. **Documente decisões:** Explique o "porquê", não só o "como"
5. **Siga os padrões:** Mantenha consistência com conteúdo existente

## 📊 Estatísticas do Repositório

- **Prompts:** 5 categorias, múltiplos exemplos
- **Chat Modes:** 2 modes especializados
- **Instructions:** 2 categorias (languages, best-practices)
- **Architecture:** 1 template completo (REST API)
- **Templates:** 3 templates (2 issues, 1 PR)
- **Guidelines:** 2 documentos completos

## 🔄 Roadmap

Áreas para expansão futura:

### Prompts
- [ ] Mais exemplos de code generation
- [ ] Prompts para diferentes linguagens
- [ ] Prompts de migração de código

### Chat Modes
- [ ] Security Expert mode
- [ ] Performance Optimizer mode
- [ ] Documentation Writer mode

### Instructions
- [ ] Python guidelines
- [ ] Java guidelines
- [ ] React guidelines
- [ ] Node.js guidelines

### Architecture
- [ ] GraphQL API template
- [ ] Microservices template
- [ ] Serverless template
- [ ] Frontend SPA template

### Templates
- [ ] Mais templates de issues
- [ ] Mais templates de PRs
- [ ] Templates de documentação

## 💡 Dicas Avançadas

### Combinar Recursos

**Exemplo 1: Nova Feature Completa**
```
1. Use architecture/backend/rest-api.md como base
2. Aplique prompts/code-generation/api-endpoint.md
3. Siga instructions/languages/typescript.md
4. Crie testes com prompts/testing/unit-tests.md
5. Documente com prompts/documentation/common-docs.md
6. Submeta com templates/pull_requests/feature.md
```

**Exemplo 2: Code Review Completo**
```
1. Ative chatmodes/code-reviewer.yml
2. Use guidelines/code-review-checklist.md
3. Verifique security com instructions/best-practices/security.md
4. Valide arquitetura com architecture/
```

### Customização

Você pode:
- Fork este repo para sua organização
- Adaptar templates ao seu workflow
- Adicionar guidelines específicas do seu time
- Criar chat modes personalizados

## 🆘 Suporte

Se precisar de ajuda:

1. **Documentação:** Leia os READMEs de cada seção
2. **Exemplos:** Veja os arquivos de exemplo
3. **Issues:** Abra uma issue para perguntas
4. **Contribuições:** PRs são bem-vindos!

## 📝 Licença

Este projeto é de uso interno da organização.

---

**Última Atualização:** 2024-01-15
**Versão:** 1.0.0
**Mantido por:** Equipe de Desenvolvimento

Para mais informações, veja os arquivos individuais em cada diretório.
