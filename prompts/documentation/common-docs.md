# Documentation Prompts

Prompts para criar documentação clara, completa e útil.

## 📚 Documentar API

### Objetivo
Criar documentação completa para endpoints de API.

### Prompt
```
Crie documentação completa para este endpoint de API:

**Código do Endpoint:**
[Cole o código do endpoint]

**Contexto:**
[Informações adicionais sobre o propósito]

A documentação deve incluir:
1. Descrição clara do que o endpoint faz
2. Método HTTP e rota
3. Parâmetros de rota (path params)
4. Query parameters
5. Request body schema
6. Headers necessários
7. Autenticação/autorização
8. Response schema (success e error)
9. Status codes possíveis
10. Exemplos de request/response
11. Rate limiting se aplicável
12. Erros comuns e como resolver

Formato: OpenAPI/Swagger 3.0
```

### Exemplo de Uso
```
Endpoint para criar usuários:

POST /api/v1/users
Headers: Authorization: Bearer {token}
Body: { name, email, role }
Response: 201 { id, name, email, role, createdAt }
```

### Tags
`documentation` `api` `openapi` `swagger`

---

## 📖 Documentar Função/Classe

### Objetivo
Criar JSDoc/TSDoc para funções e classes.

### Prompt
```
Crie documentação detalhada (JSDoc/TSDoc) para este código:

**Código:**
[Cole a função/classe]

A documentação deve incluir:
1. Descrição do propósito e comportamento
2. Tipo de cada parâmetro com descrição
3. Tipo de retorno com descrição
4. Exceções que podem ser lançadas
5. Exemplos de uso
6. Notas sobre performance se relevante
7. Warnings sobre edge cases
8. Links para recursos relacionados
9. @since tag se versioning é usado
10. @deprecated se aplicável

Siga o padrão de documentação do projeto.
```

### Exemplo
```typescript
/**
 * Calcula o total de um pedido incluindo impostos e descontos
 * 
 * @param items - Array de itens do pedido
 * @param taxRate - Taxa de imposto (0-1, ex: 0.1 para 10%)
 * @param discountCode - Código de desconto opcional
 * @returns Total calculado incluindo impostos e descontos
 * @throws {InvalidDiscountError} Se o código de desconto for inválido
 * 
 * @example
 * const total = calculateTotal(
 *   [{ price: 100, quantity: 2 }],
 *   0.1,
 *   'SAVE10'
 * );
 * // Returns 198 (200 base - 10% discount + 10% tax)
 */
```

### Tags
`documentation` `jsdoc` `tsdoc` `code-comments`

---

## 📋 Criar README

### Objetivo
Gerar README completo para um projeto.

### Prompt
```
Crie um README.md profissional para este projeto:

**Informações do Projeto:**
- Nome: [nome]
- Descrição: [breve descrição]
- Tecnologias: [lista de tech stack]
- Propósito: [para que serve]

O README deve incluir:
1. Título e badges (build, coverage, license)
2. Descrição breve e clara
3. Features principais
4. Screenshots/demos (se aplicável)
5. Pré-requisitos
6. Instruções de instalação
7. Instruções de configuração
8. Como usar/executar
9. Exemplos de uso
10. Estrutura do projeto
11. Scripts disponíveis
12. Como rodar testes
13. Como contribuir
14. Licença
15. Contato/suporte

Formato: Markdown com boa estrutura e visual.
```

### Tags
`documentation` `readme` `markdown` `project-docs`

---

## 🎓 Tutorial/Guide

### Objetivo
Criar tutorial passo-a-passo.

### Prompt
```
Crie um tutorial detalhado sobre [TÓPICO]:

**Público-Alvo:**
[Nível de experiência: iniciante/intermediário/avançado]

**Objetivo de Aprendizado:**
[O que o leitor aprenderá]

**Pré-requisitos:**
[Conhecimento/ferramentas necessárias]

O tutorial deve incluir:
1. Introdução clara do que será aprendido
2. Pré-requisitos listados
3. Passos numerados e detalhados
4. Código de exemplo em cada passo
5. Explicações do que cada parte faz
6. Screenshots ou diagramas quando útil
7. Troubleshooting de problemas comuns
8. Próximos passos/recursos adicionais
9. Exercícios práticos (opcional)
10. Conclusão e recapitulação

Estilo: Claro, amigável, com exemplos práticos.
```

### Tags
`documentation` `tutorial` `guide` `learning`

---

## 🔧 Changelog Entry

### Objetivo
Criar entradas de changelog seguindo padrões.

### Prompt
```
Crie entradas de changelog para estas mudanças:

**Mudanças:**
[Listar pull requests ou commits]

Formato: Keep a Changelog

Organize em:
- Added: Novas features
- Changed: Mudanças em features existentes
- Deprecated: Features que serão removidas
- Removed: Features removidas
- Fixed: Bug fixes
- Security: Correções de segurança

Para cada item:
- Seja conciso mas descritivo
- Inclua número de PR/issue
- Use linguagem clara para usuários
- Agrupe mudanças relacionadas
```

### Exemplo
```markdown
## [1.2.0] - 2024-01-15

### Added
- User profile pictures support (#123)
- Export data to CSV functionality (#125)

### Changed
- Improved loading performance by 40% (#130)
- Updated email templates design (#128)

### Fixed
- Fixed crash when deleting last item (#132)
- Corrected timezone display in reports (#135)
```

### Tags
`documentation` `changelog` `release-notes`

---

## 📐 Arquitetura/Design

### Objetivo
Documentar decisões arquiteturais.

### Prompt
```
Documente esta decisão arquitetural (ADR):

**Contexto:**
[Por que precisamos tomar uma decisão]

**Opções Consideradas:**
1. [Opção 1]
2. [Opção 2]
3. [Opção 3]

**Decisão:**
[Qual opção foi escolhida]

Formato: Architecture Decision Record

Deve incluir:
1. Status (proposto/aceito/descontinuado)
2. Contexto detalhado
3. Opções consideradas com prós/contras
4. Decisão tomada e justificativa
5. Consequências (positivas e negativas)
6. Data da decisão
7. Pessoas envolvidas
8. Links para discussões/documentos relacionados
```

### Exemplo Template
```markdown
# ADR-003: Escolha de Database

**Status:** Aceito
**Data:** 2024-01-15
**Deciders:** [Lista de pessoas]

## Contexto
Precisamos escolher um banco de dados...

## Opções Consideradas
1. PostgreSQL
2. MongoDB
3. MySQL

## Decisão
Escolhemos PostgreSQL porque...

## Consequências
### Positivas
- ACID compliance
- JSON support

### Negativas
- Requer mais setup
```

### Tags
`documentation` `adr` `architecture` `design-decisions`

---

## 🚀 Deployment Docs

### Objetivo
Documentar processo de deployment.

### Prompt
```
Crie documentação de deployment para:

**Aplicação:**
[Tipo e tecnologias]

**Ambiente:**
[Onde será deployado]

A documentação deve incluir:
1. Pré-requisitos (serviços, contas, etc)
2. Variáveis de ambiente necessárias
3. Processo de build
4. Processo de deployment passo-a-passo
5. Configurações de infraestrutura
6. Database migrations
7. Smoke tests pós-deploy
8. Rollback procedure
9. Monitoring e logs
10. Troubleshooting comum
11. Contatos para suporte

Inclua comandos específicos e exemplos.
```

### Tags
`documentation` `deployment` `devops` `operations`

---

## 🧪 Testing Documentation

### Objetivo
Documentar estratégia e práticas de teste.

### Prompt
```
Documente a estratégia de testes para este projeto:

**Projeto:**
[Descrição]

**Stack de Testes:**
[Ferramentas usadas]

Deve incluir:
1. Visão geral da estratégia de testes
2. Tipos de testes (unit, integration, e2e)
3. Quando escrever cada tipo
4. Como rodar testes
5. Como escrever novos testes
6. Padrões e convenções
7. Mocking e fixtures
8. Coverage requirements
9. CI/CD integration
10. Troubleshooting de testes

Inclua exemplos de testes bem escritos.
```

### Tags
`documentation` `testing` `qa` `best-practices`
