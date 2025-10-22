# Debugging Prompts

Prompts para auxiliar na identificação e resolução de bugs.

## 🐛 Analisar Bug

### Objetivo
Identificar a causa raiz de um bug e sugerir soluções.

### Prompt
```
Analise o seguinte bug e ajude a identificar a causa raiz:

**Sintoma:**
[Descreva o que está acontecendo]

**Comportamento Esperado:**
[O que deveria acontecer]

**Código Relevante:**
[Cole o código aqui]

**Logs/Errors:**
[Cole logs ou mensagens de erro]

**Contexto:**
- Ambiente: [desenvolvimento/staging/produção]
- Versão: [versão do software]
- Quando começou: [informação temporal]
- Frequência: [sempre/às vezes/raramente]

Por favor:
1. Analise o código e identifique possíveis causas
2. Explique por que o bug está ocorrendo
3. Sugira soluções com exemplos de código
4. Recomende testes para validar a correção
5. Sugira como prevenir bugs similares no futuro
```

### Exemplo de Uso
```
Analise o seguinte bug:

**Sintoma:**
Usuários estão recebendo erro 500 ao tentar fazer login

**Comportamento Esperado:**
Login deveria retornar token JWT e status 200

**Código:**
async function login(req, res) {
  const { email, password } = req.body;
  const user = await User.findOne({ email });
  const isValid = bcrypt.compare(password, user.password);
  if (isValid) {
    const token = jwt.sign({ id: user.id }, SECRET);
    res.json({ token });
  } else {
    res.status(401).json({ error: 'Invalid credentials' });
  }
}

**Logs:**
TypeError: Cannot read property 'password' of null
```

### Tags
`debugging` `bug-analysis` `troubleshooting` `root-cause`

---

## 🔍 Interpretar Error Message

### Objetivo
Entender mensagens de erro complexas e suas implicações.

### Prompt
```
Ajude-me a entender esta mensagem de erro:

**Error Message:**
[Cole a mensagem de erro completa]

**Stack Trace:**
[Cole o stack trace se disponível]

**Contexto:**
[Descreva o que estava tentando fazer quando o erro ocorreu]

Por favor explique:
1. O que a mensagem de erro significa em termos simples
2. Qual é a causa mais provável
3. Como reproduzir o erro
4. Como corrigir o problema
5. Como prevenir no futuro
```

### Tags
`error-interpretation` `stack-trace` `debugging`

---

## 🔧 Performance Debugging

### Objetivo
Identificar e resolver problemas de performance.

### Prompt
```
Analise este problema de performance:

**Problema:**
[Descreva o problema de performance]

**Métricas:**
- Tempo de resposta atual: [X ms/s]
- Tempo esperado: [Y ms/s]
- Volume de dados: [quantidade]
- Número de usuários: [quantidade]

**Código:**
[Cole o código que está lento]

**Dados de Profiling:**
[Se disponível, cole resultados de profiler]

Por favor:
1. Identifique os gargalos de performance
2. Analise a complexidade algorítmica
3. Sugira otimizações específicas
4. Forneça código otimizado
5. Explique o ganho de performance esperado
6. Sugira ferramentas para medir melhorias
```

### Exemplo
```
Código lento em produção:

function getOrdersWithItems(userId) {
  const orders = db.query('SELECT * FROM orders WHERE user_id = ?', [userId]);
  
  for (let order of orders) {
    const items = db.query('SELECT * FROM items WHERE order_id = ?', [order.id]);
    order.items = items;
    
    for (let item of items) {
      const product = db.query('SELECT * FROM products WHERE id = ?', [item.product_id]);
      item.product = product;
    }
  }
  
  return orders;
}

// Tempo atual: 2.5s para 100 pedidos
// Esperado: < 100ms
```

### Tags
`performance` `optimization` `profiling` `debugging`

---

## 🧪 Reproduzir Bug

### Objetivo
Criar steps para reproduzir um bug de forma consistente.

### Prompt
```
Preciso criar passos para reproduzir este bug:

**Bug Report:**
[Descrição do bug]

**Ambiente:**
[Detalhes do ambiente]

**Informações Disponíveis:**
[Qualquer informação sobre quando/como ocorre]

Por favor crie:
1. Passos detalhados para reproduzir
2. Dados de teste necessários
3. Configurações específicas requeridas
4. Estado inicial do sistema
5. Resultado esperado vs atual em cada passo
6. Script de reprodução se apropriado
```

### Tags
`reproduction` `testing` `debugging`

---

## 📊 Analisar Logs

### Objetivo
Analisar logs para identificar problemas.

### Prompt
```
Analise estes logs e identifique problemas:

**Logs:**
[Cole os logs aqui]

**Contexto:**
[Quando os logs foram coletados e por quê]

Por favor:
1. Identifique padrões suspeitos
2. Aponte erros e warnings importantes
3. Identifique possíveis problemas
4. Sugira o que investigar mais
5. Recomende melhorias no logging
```

### Tags
`logs` `analysis` `debugging` `monitoring`

---

## 🔄 Race Condition

### Objetivo
Identificar e corrigir race conditions.

### Prompt
```
Suspeito de uma race condition neste código:

**Código:**
[Cole o código]

**Sintomas:**
[Descreva o comportamento inconsistente]

**Ambiente:**
- Concorrência: [número de threads/requests paralelas]
- Recursos compartilhados: [lista]

Por favor:
1. Identifique possíveis race conditions
2. Explique como a race condition ocorre
3. Sugira soluções (locks, transactions, etc)
4. Forneça código corrigido
5. Sugira testes para validar a correção
```

### Tags
`concurrency` `race-condition` `threading` `debugging`

---

## 💾 Memory Leak

### Objetivo
Identificar e corrigir memory leaks.

### Prompt
```
Analise este possível memory leak:

**Sintomas:**
- Uso de memória: [cresce continuamente]
- Após quanto tempo: [X horas/dias]
- Heap snapshot: [se disponível]

**Código Suspeito:**
[Cole código que pode estar causando leak]

Por favor:
1. Identifique possíveis causas do memory leak
2. Explique como o leak está ocorrendo
3. Sugira correções específicas
4. Recomende ferramentas para detectar leaks
5. Sugira práticas para prevenir leaks
```

### Tags
`memory-leak` `performance` `debugging` `profiling`

---

## 🌐 Network Debugging

### Objetivo
Debugar problemas de rede e APIs.

### Prompt
```
Preciso debugar este problema de rede:

**Problema:**
[Descreva o problema]

**Request:**
- Method: [GET/POST/etc]
- URL: [url]
- Headers: [headers]
- Body: [request body]

**Response:**
- Status: [status code]
- Headers: [response headers]
- Body: [response body]

**Network Logs:**
[Logs de rede se disponíveis]

Por favor:
1. Analise a request/response
2. Identifique o problema
3. Sugira correções
4. Recomende debugging adicional se necessário
```

### Tags
`network` `api` `debugging` `http`
