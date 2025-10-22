# Security Best Practices

## Objetivo
Diretrizes de segurança para aplicações web e APIs.

## Padrões de Segurança

### Autenticação

#### JWT (JSON Web Tokens)
```typescript
// Configuração segura de JWT
const jwtConfig = {
  secret: process.env.JWT_SECRET, // Nunca hardcode!
  expiresIn: '15m', // Curta duração para access tokens
  algorithm: 'HS256',
  issuer: 'your-app-name',
  audience: 'your-app-users'
};

// Refresh tokens devem ter duração maior
const refreshTokenConfig = {
  secret: process.env.REFRESH_TOKEN_SECRET,
  expiresIn: '7d'
};
```

#### Password Hashing
```typescript
import bcrypt from 'bcrypt';

// Use salt rounds adequado (10-12)
const SALT_ROUNDS = 12;

async function hashPassword(password: string): Promise<string> {
  return await bcrypt.hash(password, SALT_ROUNDS);
}

async function verifyPassword(password: string, hash: string): Promise<boolean> {
  return await bcrypt.compare(password, hash);
}
```

### Input Validation

#### Schema Validation com Zod
```typescript
import { z } from 'zod';

const UserSchema = z.object({
  email: z.string().email().max(255),
  name: z.string().min(2).max(100),
  age: z.number().int().min(18).max(150).optional(),
  password: z.string()
    .min(8)
    .regex(/[A-Z]/, 'Deve conter maiúscula')
    .regex(/[a-z]/, 'Deve conter minúscula')
    .regex(/[0-9]/, 'Deve conter número')
    .regex(/[^A-Za-z0-9]/, 'Deve conter caractere especial')
});

// Uso
function createUser(data: unknown) {
  const validated = UserSchema.parse(data);
  // validated é type-safe
}
```

#### Sanitização
```typescript
import DOMPurify from 'isomorphic-dompurify';

// Sanitize HTML para prevenir XSS
function sanitizeHTML(dirty: string): string {
  return DOMPurify.sanitize(dirty);
}

// Escape para SQL (use ORM sempre que possível)
// Nunca concatene strings em queries SQL!
```

### Prevenção de Vulnerabilidades

#### SQL Injection Prevention
```typescript
// ❌ NUNCA faça isso
const query = `SELECT * FROM users WHERE email = '${email}'`;

// ✅ Use parameterized queries
const query = 'SELECT * FROM users WHERE email = ?';
db.execute(query, [email]);

// ✅ Ou use ORM
const user = await prisma.user.findUnique({
  where: { email }
});
```

#### XSS Prevention
```typescript
// Frontend - Escape user input
import escapeHtml from 'escape-html';

function displayUserContent(content: string) {
  return escapeHtml(content);
}

// Use Content Security Policy headers
app.use(helmet.contentSecurityPolicy({
  directives: {
    defaultSrc: ["'self'"],
    scriptSrc: ["'self'", "'unsafe-inline'"],
    styleSrc: ["'self'", "'unsafe-inline'"],
    imgSrc: ["'self'", 'data:', 'https:'],
  }
}));
```

#### CSRF Protection
```typescript
import csrf from 'csurf';

// Configure CSRF protection
const csrfProtection = csrf({ cookie: true });

app.post('/api/transfer', csrfProtection, (req, res) => {
  // Route protegida
});
```

### Headers de Segurança

```typescript
import helmet from 'helmet';

app.use(helmet({
  contentSecurityPolicy: {
    directives: {
      defaultSrc: ["'self'"],
      styleSrc: ["'self'", "'unsafe-inline'"],
    },
  },
  hsts: {
    maxAge: 31536000,
    includeSubDomains: true,
    preload: true
  },
  frameguard: {
    action: 'deny'
  },
  noSniff: true,
  xssFilter: true
}));

// CORS configuration
app.use(cors({
  origin: process.env.ALLOWED_ORIGINS?.split(','),
  credentials: true,
  optionsSuccessStatus: 200
}));
```

### Rate Limiting

```typescript
import rateLimit from 'express-rate-limit';

// Rate limiter geral
const generalLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutos
  max: 100, // limite de 100 requests
  message: 'Too many requests from this IP'
});

// Rate limiter para login (mais restritivo)
const loginLimiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 5,
  message: 'Too many login attempts'
});

app.use('/api/', generalLimiter);
app.use('/api/auth/login', loginLimiter);
```

### Secrets Management

```typescript
// ✅ Use variáveis de ambiente
const config = {
  database: {
    url: process.env.DATABASE_URL,
    password: process.env.DB_PASSWORD
  },
  jwt: {
    secret: process.env.JWT_SECRET,
    refreshSecret: process.env.REFRESH_TOKEN_SECRET
  },
  api: {
    key: process.env.API_KEY
  }
};

// ✅ Valide que secrets existem no startup
function validateConfig() {
  const required = [
    'DATABASE_URL',
    'JWT_SECRET',
    'REFRESH_TOKEN_SECRET'
  ];
  
  const missing = required.filter(key => !process.env[key]);
  
  if (missing.length > 0) {
    throw new Error(`Missing required env vars: ${missing.join(', ')}`);
  }
}

// ❌ NUNCA commite secrets
// Adicione ao .gitignore:
// .env
// .env.local
// secrets/
```

### Logging Seguro

```typescript
import winston from 'winston';

// Configure logger para NÃO logar dados sensíveis
const logger = winston.createLogger({
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.json()
  ),
  transports: [
    new winston.transports.File({ filename: 'error.log', level: 'error' }),
    new winston.transports.File({ filename: 'combined.log' })
  ]
});

// ✅ Remova dados sensíveis antes de logar
function sanitizeForLog(data: any) {
  const sanitized = { ...data };
  delete sanitized.password;
  delete sanitized.token;
  delete sanitized.creditCard;
  delete sanitized.ssn;
  return sanitized;
}

logger.info('User created', sanitizeForLog(userData));
```

### Encryption

```typescript
import crypto from 'crypto';

// Encryption at rest
class Encryption {
  private algorithm = 'aes-256-gcm';
  private key: Buffer;

  constructor() {
    this.key = Buffer.from(process.env.ENCRYPTION_KEY!, 'hex');
  }

  encrypt(text: string): string {
    const iv = crypto.randomBytes(16);
    const cipher = crypto.createCipheriv(this.algorithm, this.key, iv);
    
    let encrypted = cipher.update(text, 'utf8', 'hex');
    encrypted += cipher.final('hex');
    
    const authTag = cipher.getAuthTag();
    
    return iv.toString('hex') + ':' + authTag.toString('hex') + ':' + encrypted;
  }

  decrypt(encrypted: string): string {
    const parts = encrypted.split(':');
    const iv = Buffer.from(parts[0], 'hex');
    const authTag = Buffer.from(parts[1], 'hex');
    const encryptedText = parts[2];
    
    const decipher = crypto.createDecipheriv(this.algorithm, this.key, iv);
    decipher.setAuthTag(authTag);
    
    let decrypted = decipher.update(encryptedText, 'hex', 'utf8');
    decrypted += decipher.final('utf8');
    
    return decrypted;
  }
}
```

## Checklist de Segurança

### Autenticação e Autorização
- [ ] Senhas hasheadas com bcrypt/argon2
- [ ] JWT com expiration curta
- [ ] Refresh tokens implementados
- [ ] MFA disponível para contas sensíveis
- [ ] Rate limiting em endpoints de auth
- [ ] Política de senha forte implementada
- [ ] Proteção contra brute force
- [ ] Logout invalida tokens
- [ ] Autorização verificada em cada request

### Input Validation
- [ ] Validação em todas as entradas do usuário
- [ ] Schema validation implementada
- [ ] Sanitização de HTML/JavaScript
- [ ] Tamanho máximo de input validado
- [ ] Tipo de dados validado
- [ ] Whitelist de valores quando possível

### Injection Prevention
- [ ] Parametrized queries ou ORM usado
- [ ] Nunca concatenar strings em SQL
- [ ] NoSQL injection prevenida
- [ ] Command injection prevenida
- [ ] LDAP injection prevenida
- [ ] XML injection prevenida

### XSS Prevention
- [ ] Content Security Policy configurado
- [ ] Output encoding implementado
- [ ] DOM sanitization em frontend
- [ ] HTTPOnly cookies para tokens
- [ ] Secure flag em cookies (HTTPS)

### CSRF Prevention
- [ ] CSRF tokens implementados
- [ ] SameSite cookie attribute usado
- [ ] Origin/Referer validation
- [ ] Double-submit cookies

### Security Headers
- [ ] Helmet.js configurado
- [ ] HSTS habilitado
- [ ] X-Frame-Options: DENY
- [ ] X-Content-Type-Options: nosniff
- [ ] X-XSS-Protection habilitado
- [ ] Referrer-Policy configurado

### Secrets Management
- [ ] Nenhum secret hardcoded
- [ ] .env no .gitignore
- [ ] Variáveis de ambiente validadas no startup
- [ ] Rotation de secrets implementada
- [ ] Secrets em vault (production)

### API Security
- [ ] HTTPS obrigatório em produção
- [ ] API keys rotacionáveis
- [ ] Rate limiting por IP/user
- [ ] Request size limits
- [ ] Timeout configurado
- [ ] Versionamento de API
- [ ] Documentação não expõe informações sensíveis

### Data Protection
- [ ] Encryption at rest para dados sensíveis
- [ ] Encryption in transit (TLS/HTTPS)
- [ ] PII identificado e protegido
- [ ] GDPR/LGPD compliance
- [ ] Backup encryption
- [ ] Secure data deletion

### Logging e Monitoring
- [ ] Logs não contêm dados sensíveis
- [ ] Eventos de segurança logados
- [ ] Anomalias monitoradas
- [ ] Alertas configurados
- [ ] Logs centralizados
- [ ] Retention policy definida

### Dependencies
- [ ] Dependências auditadas regularmente
- [ ] Vulnerabilidades conhecidas corrigidas
- [ ] Dependabot ou similar configurado
- [ ] Lockfile commitado
- [ ] Minimal dependencies

### Error Handling
- [ ] Erros não expõem stack traces em produção
- [ ] Mensagens de erro genéricas para usuários
- [ ] Detalhes logados internamente
- [ ] Graceful degradation
- [ ] Fail securely

## OWASP Top 10 (2021)

1. **Broken Access Control**
   - Implemente autorização em cada endpoint
   - Valide permissões no backend
   - Use principle of least privilege

2. **Cryptographic Failures**
   - Use HTTPS everywhere
   - Encrypt sensitive data at rest
   - Use strong encryption algorithms

3. **Injection**
   - Use parameterized queries
   - Validate and sanitize all inputs
   - Use ORM/ODM

4. **Insecure Design**
   - Threat modeling
   - Security requirements
   - Secure design patterns

5. **Security Misconfiguration**
   - Harden configurations
   - Remove default accounts
   - Keep dependencies updated

6. **Vulnerable and Outdated Components**
   - Regular dependency updates
   - Monitor CVEs
   - Use automated scanning

7. **Identification and Authentication Failures**
   - Implement MFA
   - Strong password policy
   - Secure session management

8. **Software and Data Integrity Failures**
   - Verify digital signatures
   - Use CI/CD security
   - Dependency integrity checks

9. **Security Logging and Monitoring Failures**
   - Log security events
   - Monitor for anomalies
   - Alert on suspicious activity

10. **Server-Side Request Forgery (SSRF)**
    - Validate URLs
    - Use allowlists
    - Isolate from internal network

## Recursos

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Cheat Sheets](https://cheatsheetseries.owasp.org/)
- [Node.js Security Best Practices](https://nodejs.org/en/docs/guides/security/)
- [JWT Best Practices](https://tools.ietf.org/html/rfc8725)
