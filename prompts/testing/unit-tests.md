# Criar Testes Unitários

## Objetivo
Gerar testes unitários completos e abrangentes para funções, classes ou módulos.

## Contexto
Use este prompt quando precisar criar testes unitários com boa cobertura e seguindo as melhores práticas.

## Prompt
```
Crie testes unitários completos para [FUNÇÃO/CLASSE/MÓDULO] considerando:

1. Casos de sucesso (happy path)
2. Casos de erro e exceções
3. Casos limite (edge cases)
4. Validações de entrada
5. Mocks de dependências externas

Estrutura dos testes:
- Arrange (preparação)
- Act (execução)
- Assert (verificação)

Inclua:
- Descrições claras de cada teste
- Setup e teardown quando necessário
- Cobertura mínima de 80%
- Testes de integração onde apropriado
- Asserções significativas

Use o framework de testes [FRAMEWORK] e siga as convenções do projeto.
```

## Exemplo de Uso
```
Crie testes unitários completos para a classe UserService considerando:

Métodos a testar:
- createUser(userData)
- getUserById(userId)
- updateUser(userId, updates)
- deleteUser(userId)

Use o framework Jest e mock as dependências do banco de dados.
```

## Resultado Esperado
- Arquivo de teste completo
- Múltiplos casos de teste por método
- Mocks apropriados
- Asserções claras e específicas
- Cobertura abrangente de cenários
- Comentários explicativos quando necessário

## Tags
`testing` `unit-tests` `tdd` `jest` `mocha` `coverage`
