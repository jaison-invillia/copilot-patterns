# REST API Architecture

## Visão Geral

Arquitetura para API RESTful seguindo princípios REST e boas práticas modernas.

### Casos de Uso
- APIs públicas ou privadas
- CRUD operations
- Integração entre sistemas
- Backend para aplicações web/mobile

## Estrutura de Diretórios

```
project-root/
├── src/
│   ├── config/              # Configurações da aplicação
│   │   ├── database.ts
│   │   ├── server.ts
│   │   └── env.ts
│   ├── controllers/         # Controladores (handlers de requisições)
│   │   ├── user.controller.ts
│   │   └── auth.controller.ts
│   ├── services/            # Lógica de negócio
│   │   ├── user.service.ts
│   │   └── auth.service.ts
│   ├── repositories/        # Acesso a dados
│   │   ├── user.repository.ts
│   │   └── base.repository.ts
│   ├── models/              # Modelos de dados
│   │   ├── user.model.ts
│   │   └── token.model.ts
│   ├── dtos/                # Data Transfer Objects
│   │   ├── create-user.dto.ts
│   │   └── update-user.dto.ts
│   ├── middlewares/         # Middlewares
│   │   ├── auth.middleware.ts
│   │   ├── error.middleware.ts
│   │   └── logger.middleware.ts
│   ├── validators/          # Validadores de entrada
│   │   ├── user.validator.ts
│   │   └── schemas/
│   ├── routes/              # Definição de rotas
│   │   ├── index.ts
│   │   ├── user.routes.ts
│   │   └── auth.routes.ts
│   ├── utils/               # Utilitários
│   │   ├── logger.ts
│   │   ├── crypto.ts
│   │   └── response.ts
│   ├── types/               # Definições de tipos
│   │   ├── express.d.ts
│   │   └── custom.types.ts
│   ├── errors/              # Classes de erro customizadas
│   │   ├── app-error.ts
│   │   ├── not-found.error.ts
│   │   └── validation.error.ts
│   └── app.ts               # Configuração da aplicação
│   └── server.ts            # Entry point
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── docs/
│   ├── api/                 # Documentação da API (OpenAPI/Swagger)
│   └── architecture/        # ADRs e diagramas
├── scripts/
│   ├── seed.ts
│   └── migrate.ts
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md
```

## Componentes

### Controllers
Responsáveis por receber requisições HTTP, validar entrada e retornar respostas.

```typescript
// controllers/user.controller.ts
import { Request, Response, NextFunction } from 'express';
import { UserService } from '../services/user.service';
import { CreateUserDto } from '../dtos/create-user.dto';

export class UserController {
  constructor(private userService: UserService) {}

  async createUser(req: Request, res: Response, next: NextFunction) {
    try {
      const dto: CreateUserDto = req.body;
      const user = await this.userService.createUser(dto);
      res.status(201).json({
        success: true,
        data: user
      });
    } catch (error) {
      next(error);
    }
  }

  async getUser(req: Request, res: Response, next: NextFunction) {
    try {
      const { id } = req.params;
      const user = await this.userService.getUserById(id);
      res.json({
        success: true,
        data: user
      });
    } catch (error) {
      next(error);
    }
  }
}
```

### Services
Contêm a lógica de negócio da aplicação.

```typescript
// services/user.service.ts
import { UserRepository } from '../repositories/user.repository';
import { CreateUserDto } from '../dtos/create-user.dto';
import { NotFoundError } from '../errors/not-found.error';

export class UserService {
  constructor(private userRepository: UserRepository) {}

  async createUser(dto: CreateUserDto) {
    // Validações de negócio
    const existingUser = await this.userRepository.findByEmail(dto.email);
    if (existingUser) {
      throw new Error('Email already in use');
    }

    // Criar usuário
    return await this.userRepository.create(dto);
  }

  async getUserById(id: string) {
    const user = await this.userRepository.findById(id);
    if (!user) {
      throw new NotFoundError('User');
    }
    return user;
  }
}
```

### Repositories
Encapsulam acesso a dados e queries.

```typescript
// repositories/user.repository.ts
import { User } from '../models/user.model';

export class UserRepository {
  async create(data: Partial<User>): Promise<User> {
    // Implementação com ORM (Prisma, TypeORM, etc)
  }

  async findById(id: string): Promise<User | null> {
    // Implementação
  }

  async findByEmail(email: string): Promise<User | null> {
    // Implementação
  }

  async update(id: string, data: Partial<User>): Promise<User> {
    // Implementação
  }

  async delete(id: string): Promise<void> {
    // Implementação
  }
}
```

### Routes
Definem endpoints e conectam a middlewares e controllers.

```typescript
// routes/user.routes.ts
import { Router } from 'express';
import { UserController } from '../controllers/user.controller';
import { authMiddleware } from '../middlewares/auth.middleware';
import { validateDto } from '../middlewares/validate.middleware';
import { CreateUserDto } from '../dtos/create-user.dto';

const router = Router();
const userController = new UserController();

router.post(
  '/users',
  validateDto(CreateUserDto),
  userController.createUser.bind(userController)
);

router.get(
  '/users/:id',
  authMiddleware,
  userController.getUser.bind(userController)
);

export default router;
```

## Fluxo de Dados

```
Request
  ↓
Middlewares (Auth, Validation, Logging)
  ↓
Router
  ↓
Controller (Validation, Transformation)
  ↓
Service (Business Logic)
  ↓
Repository (Data Access)
  ↓
Database
  ↓
Repository
  ↓
Service
  ↓
Controller (Response Formatting)
  ↓
Response
```

## Stack Tecnológico Recomendado

### Runtime & Framework
- **Node.js** com **Express.js** ou **Fastify**
- **TypeScript** para type safety

### Database
- **PostgreSQL** para dados relacionais
- **Redis** para cache
- **MongoDB** para dados não estruturados (opcional)

### ORM/Query Builder
- **Prisma** (recomendado)
- **TypeORM**
- **Knex.js**

### Validação
- **Zod** (recomendado)
- **Joi**
- **class-validator**

### Autenticação
- **JWT** para tokens
- **bcrypt** para hashing de senhas
- **Passport.js** para estratégias de auth

### Logging
- **Winston** ou **Pino**

### Testing
- **Jest** para testes
- **Supertest** para testes de API

### Documentação
- **Swagger/OpenAPI**
- **Postman Collections**

## Escalabilidade

### Horizontal Scaling
```
Load Balancer (Nginx/AWS ALB)
  ↓
API Instance 1 ← → Redis Cache
API Instance 2 ← ↓
API Instance N ← ↓
  ↓
Database (Primary)
  ↓
Database (Replica) - Read Only
```

### Performance Optimizations
1. **Caching**: Redis para dados frequentes
2. **Database Indexing**: Índices em colunas de busca
3. **Connection Pooling**: Pool de conexões ao DB
4. **Rate Limiting**: Limitar requisições por cliente
5. **Compression**: Gzip/Brotli para respostas
6. **Pagination**: Limitar resultados de queries
7. **Lazy Loading**: Carregar dados relacionados sob demanda

## Segurança

### Checklist de Segurança
- [ ] HTTPS obrigatório em produção
- [ ] Autenticação JWT com refresh tokens
- [ ] Rate limiting e throttling
- [ ] Input validation e sanitization
- [ ] SQL injection prevention (use ORM)
- [ ] XSS protection
- [ ] CORS configurado corretamente
- [ ] Helmet.js para headers de segurança
- [ ] Secrets em variáveis de ambiente
- [ ] Logging de eventos de segurança
- [ ] Versionamento de API (/v1, /v2)

## Exemplos de Configuração

### Environment Variables
```env
# Server
NODE_ENV=production
PORT=3000
API_VERSION=v1

# Database
DATABASE_URL=postgresql://user:pass@localhost:5432/mydb
REDIS_URL=redis://localhost:6379

# Auth
JWT_SECRET=your-secret-key
JWT_EXPIRES_IN=7d
REFRESH_TOKEN_SECRET=your-refresh-secret

# External Services
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
```

### API Response Format
```typescript
// Success Response
{
  "success": true,
  "data": {
    "id": "123",
    "name": "John Doe"
  },
  "meta": {
    "timestamp": "2024-01-01T00:00:00Z",
    "version": "v1"
  }
}

// Error Response
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid email format",
    "details": [
      {
        "field": "email",
        "message": "Must be a valid email"
      }
    ]
  },
  "meta": {
    "timestamp": "2024-01-01T00:00:00Z",
    "version": "v1"
  }
}
```

## Boas Práticas

1. **Use Dependency Injection**: Facilita testes e manutenção
2. **Separe Concerns**: Uma responsabilidade por classe
3. **Error Handling Centralizado**: Middleware de erro global
4. **Logging Estruturado**: JSON logs para parsing fácil
5. **Versionamento de API**: Prepare para mudanças futuras
6. **Documentação Automática**: Gere docs do código
7. **Health Checks**: Endpoint /health para monitoramento
8. **Graceful Shutdown**: Feche conexões adequadamente
9. **Database Migrations**: Versione mudanças no schema
10. **CI/CD**: Automatize testes e deploy

## Recursos
- [REST API Best Practices](https://restfulapi.net/)
- [Express.js Documentation](https://expressjs.com/)
- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)
