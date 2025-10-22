# Chat Modes

Configurações de chat modes personalizados para diferentes contextos de desenvolvimento.

## 📂 Estrutura

```
chatmodes/
├── README.md              # Este arquivo
├── code-reviewer.yml      # Mode para code review
├── architect.yml          # Mode para arquitetura
├── debugger.yml          # Mode para debugging
├── tester.yml            # Mode para testes
└── documenter.yml        # Mode para documentação
```

## 🎯 O que são Chat Modes?

Chat modes são configurações que ajustam o comportamento do GitHub Copilot Chat para contextos específicos. Cada mode define:

- Persona e tom de voz
- Conhecimento especializado
- Formato de resposta
- Nível de detalhe
- Foco específico

## 🔧 Como Usar

1. Escolha o chat mode apropriado para sua tarefa
2. Ative o mode no GitHub Copilot Chat
3. Faça suas perguntas no contexto definido
4. O Copilot responderá com o comportamento configurado

## 📝 Criando Novos Modes

Template para criar um novo chat mode:

```yaml
name: "Nome do Mode"
description: "Descrição do comportamento"
persona: "Descrição da persona"
expertise:
  - "Área 1"
  - "Área 2"
tone: "profissional|casual|técnico"
response_format:
  - "Formato preferido"
  - "Estrutura de resposta"
focus:
  - "Foco principal"
  - "Aspectos a enfatizar"
examples:
  - question: "Pergunta exemplo"
    answer: "Resposta exemplo"
```

## 🎭 Modes Disponíveis

### Code Reviewer
Foco em análise de código, identificação de problemas e sugestões de melhoria.

### Architect
Especializado em design de sistemas, padrões arquiteturais e decisões técnicas.

### Debugger
Auxilia na identificação e resolução de bugs, análise de logs e troubleshooting.

### Tester
Especializado em criação de testes, estratégias de teste e qualidade de código.

### Documenter
Foco em criação de documentação clara, completa e útil.
