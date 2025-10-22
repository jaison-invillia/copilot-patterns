# Refatorar para Melhorar Performance

## Objetivo
Refatorar código existente para melhorar performance, mantendo a funcionalidade original.

## Contexto
Use este prompt quando identificar gargalos de performance ou código que pode ser otimizado.

## Prompt
```
Analise e refatore o seguinte código para melhorar a performance:

[CÓDIGO AQUI]

Considere:
1. Complexidade algorítmica (Big O)
2. Uso de memória
3. Operações I/O
4. Queries ao banco de dados (N+1 problems)
5. Caching quando apropriado
6. Lazy loading vs eager loading
7. Paralelização de operações

Requisitos:
- Manter a funcionalidade original
- Adicionar benchmarks antes/depois
- Documentar as otimizações realizadas
- Manter a legibilidade do código
- Adicionar comentários explicativos
- Sugerir métricas de monitoramento

Forneça uma análise detalhada das melhorias de performance.
```

## Exemplo de Uso
```
Analise e refatore o seguinte código para melhorar a performance:

function processUsers(users) {
  const results = [];
  for (let user of users) {
    const orders = database.getOrdersByUserId(user.id);
    for (let order of orders) {
      const items = database.getItemsByOrderId(order.id);
      results.push({ user, order, items });
    }
  }
  return results;
}

Identifique o problema N+1 e otimize usando joins ou batch loading.
```

## Resultado Esperado
- Código refatorado com melhorias de performance
- Análise da complexidade antes/depois
- Estimativa de ganho de performance
- Testes que garantem funcionalidade preservada
- Documentação das mudanças
- Sugestões de monitoramento

## Tags
`refactoring` `performance` `optimization` `big-o` `caching`
