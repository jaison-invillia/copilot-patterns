# Contribuindo para o Copilot Patterns

Obrigado por considerar contribuir! Este documento fornece diretrizes para contribuições.

## 📋 Índice

- [Código de Conduta](#código-de-conduta)
- [Como Contribuir](#como-contribuir)
- [Estrutura do Repositório](#estrutura-do-repositório)
- [Padrões e Convenções](#padrões-e-convenções)
- [Processo de Review](#processo-de-review)

## 🤝 Código de Conduta

Este projeto segue princípios de respeito, colaboração e inclusão. Esperamos que todos os contribuidores:

- Sejam respeitosos e profissionais
- Aceitem feedback construtivo
- Foquem no que é melhor para a comunidade
- Demonstrem empatia com outros membros

## 🚀 Como Contribuir

### Reportando Issues

Antes de criar uma issue:
1. Busque por issues similares existentes
2. Use o template apropriado
3. Forneça informações detalhadas
4. Inclua exemplos quando possível

### Sugerindo Melhorias

Para sugerir novos patterns ou melhorias:
1. Abra uma issue descrevendo a proposta
2. Explique o valor/benefício
3. Forneça exemplos se possível
4. Aguarde feedback antes de implementar

### Submitting Changes

1. **Fork o repositório**
   ```bash
   git clone https://github.com/[seu-usuario]/copilot-patterns
   cd copilot-patterns
   ```

2. **Crie uma branch**
   ```bash
   git checkout -b feature/nome-descritivo
   # ou
   git checkout -b fix/descricao-do-bug
   ```

3. **Faça suas alterações**
   - Siga os padrões do projeto
   - Mantenha commits organizados
   - Use mensagens de commit claras

4. **Teste suas mudanças**
   - Verifique que exemplos funcionam
   - Valide markdown
   - Revise ortografia e gramática

5. **Commit suas mudanças**
   ```bash
   git add .
   git commit -m "feat: adiciona exemplo de X"
   ```

6. **Push para sua branch**
   ```bash
   git push origin feature/nome-descritivo
   ```

7. **Abra um Pull Request**
   - Use o template de PR apropriado
   - Descreva claramente as mudanças
   - Referencie issues relacionadas
   - Aguarde review

## 📁 Estrutura do Repositório

```
copilot-patterns/
├── .copilot/          # Configurações do Copilot Spaces
├── prompts/           # Prompts reutilizáveis
├── chatmodes/         # Chat modes customizados
├── instructions/      # Instruções para o Copilot
├── architecture/      # Templates de arquitetura
├── templates/         # Templates de issues e PRs
└── guidelines/        # Diretrizes de code review
```

### Onde Adicionar Conteúdo

| Tipo de Conteúdo | Diretório | Exemplo |
|------------------|-----------|---------|
| Prompt reutilizável | `prompts/[categoria]/` | `prompts/testing/integration-tests.md` |
| Chat mode | `chatmodes/` | `chatmodes/security-reviewer.yml` |
| Instrução de linguagem | `instructions/languages/` | `instructions/languages/python.md` |
| Instrução de framework | `instructions/frameworks/` | `instructions/frameworks/react.md` |
| Template de arquitetura | `architecture/[tipo]/` | `architecture/frontend/spa.md` |
| Template de issue | `templates/issues/` | `templates/issues/task.md` |
| Template de PR | `templates/pull_requests/` | `templates/pull_requests/bugfix.md` |
| Guideline | `guidelines/` | `guidelines/best-practices.md` |

## 📝 Padrões e Convenções

### Markdown

- Use headers hierárquicos (##, ###, ####)
- Inclua emoji para melhor visualização (opcional mas encorajado)
- Use code blocks com linguagem especificada
- Adicione links internos quando relevante

### Estrutura de Arquivos

Cada arquivo deve conter:

1. **Título claro**: Nível 1 header
2. **Objetivo**: O que o documento cobre
3. **Conteúdo organizado**: Seções lógicas
4. **Exemplos práticos**: Código ou uso
5. **Tags**: Para facilitar busca (quando aplicável)

### Exemplo de Template

```markdown
# Título do Pattern

## Objetivo
Descrição clara do que este pattern resolve.

## Contexto
Quando usar este pattern.

## Implementação
Como implementar.

## Exemplos
Código de exemplo.

## Considerações
Pontos importantes.

## Tags
`tag1` `tag2` `tag3`
```

### Commits

Siga o padrão [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` Nova feature ou pattern
- `fix:` Correção de erro ou typo
- `docs:` Atualização de documentação
- `refactor:` Reorganização sem mudar funcionalidade
- `chore:` Tarefas de manutenção

Exemplos:
```
feat: adiciona prompt para testes de integração
fix: corrige typo em chatmode architect
docs: atualiza README com novos exemplos
refactor: reorganiza estrutura de prompts
```

### Nomenclatura de Arquivos

- Use kebab-case: `api-endpoint.md`
- Seja descritivo: `rest-api-architecture.md` não `api.md`
- Use extensões apropriadas: `.md` para markdown, `.yml` para YAML

## 🔍 Processo de Review

### Para Contribuidores

1. **Auto-review**: Revise suas próprias mudanças primeiro
2. **Seja receptivo**: Aceite feedback construtivamente
3. **Responda prontamente**: Endereço comentários em tempo hábil
4. **Faça perguntas**: Se não entender feedback, pergunte

### Critérios de Review

PRs serão avaliados em:

- **Qualidade**: Conteúdo é preciso e útil?
- **Clareza**: Explicações são claras?
- **Exemplos**: Código de exemplo funciona?
- **Formatação**: Segue padrões do projeto?
- **Valor**: Adiciona valor ao repositório?

### Aprovação

PRs precisam de:
- Mínimo 1 aprovação de maintainer
- Sem comentários não resolvidos
- CI checks passando (se aplicável)

## ✅ Checklist de Contribuição

Antes de submeter um PR, verifique:

- [ ] Código/exemplos foram testados
- [ ] Markdown está bem formatado
- [ ] Ortografia e gramática revisadas
- [ ] Seguiu padrões de nomenclatura
- [ ] Adicionou exemplos práticos
- [ ] Documentou decisões importantes
- [ ] README atualizado (se necessário)
- [ ] Commits seguem padrão
- [ ] PR tem descrição clara
- [ ] Issues relacionadas foram linkadas

## 🎓 Boas Práticas

### Escrevendo Prompts

- Seja específico e claro
- Inclua contexto suficiente
- Forneça exemplos de uso
- Documente resultado esperado
- Adicione tags relevantes

### Criando Chat Modes

- Defina persona clara
- Liste expertise específica
- Forneça exemplos de interação
- Documente formato de resposta esperado

### Documentando Arquitetura

- Inclua diagramas quando útil
- Liste trade-offs
- Forneça exemplos de código
- Documente decisões importantes
- Inclua checklist de implementação

### Criando Templates

- Seja abrangente mas não excessivo
- Use linguagem clara
- Inclua exemplos
- Adicione checklists
- Mantenha formatação consistente

## 🆘 Precisa de Ajuda?

Se tiver dúvidas:

1. Verifique a documentação existente
2. Busque issues similares
3. Abra uma issue com sua pergunta
4. Seja específico sobre o que precisa

## 📚 Recursos Úteis

- [Markdown Guide](https://www.markdownguide.org/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)

## 🙏 Reconhecimento

Agradecemos a todos que contribuem para tornar este repositório uma referência de qualidade!

---

**Dúvidas?** Abra uma issue ou entre em contato com os maintainers.
