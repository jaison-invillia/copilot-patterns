# Criar Endpoint de API REST

## Objetivo
Gerar um endpoint de API REST completo com validações, tratamento de erros e documentação.

## Contexto
Use este prompt quando precisar criar novos endpoints para APIs REST, incluindo todas as camadas necessárias (controller, service, repository).

## Prompt
```
Crie um endpoint REST completo para [RECURSO] com os seguintes requisitos:

1. Método HTTP: [GET/POST/PUT/DELETE]
2. Rota: [/api/v1/recurso]
3. Parâmetros: [lista de parâmetros]
4. Validações: [regras de validação]
5. Resposta esperada: [estrutura da resposta]

Inclua:
- Controller com roteamento
- Service com lógica de negócio
- Validação de entrada
- Tratamento de erros apropriado
- Documentação OpenAPI/Swagger
- Testes unitários básicos
- Logs estruturados

Siga as convenções REST e boas práticas de segurança.
```

## Exemplo de Uso
```
Crie um endpoint REST completo para usuários com os seguintes requisitos:

1. Método HTTP: POST
2. Rota: /api/v1/users
3. Parâmetros: name (string, required), email (string, required, valid email), age (number, optional, min 18)
4. Validações: email único, formato de email válido, nome mínimo 3 caracteres
5. Resposta esperada: { id, name, email, age, createdAt }
```

## Resultado Esperado
- Código do controller com endpoint configurado
- Código do service com lógica de negócio
- Validadores de entrada
- Handlers de erro
- Documentação Swagger
- Testes unitários
- Exemplos de requisição/resposta

## Tags
`api` `rest` `endpoint` `crud` `validation`
