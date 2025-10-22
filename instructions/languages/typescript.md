# TypeScript Instructions

## Objetivo
Diretrizes para desenvolvimento em TypeScript com foco em type safety, boas práticas e código maintainable.

## Padrões

### Nomenclatura
- **Interfaces**: PascalCase com prefixo `I` opcional (ex: `IUser` ou `User`)
- **Types**: PascalCase (ex: `UserType`)
- **Enums**: PascalCase (ex: `UserRole`)
- **Variáveis/Funções**: camelCase (ex: `getUserById`)
- **Classes**: PascalCase (ex: `UserService`)
- **Constantes**: UPPER_SNAKE_CASE (ex: `MAX_RETRIES`)
- **Arquivos**: kebab-case (ex: `user-service.ts`)

### Type Safety
- Sempre use tipos explícitos em parâmetros de função
- Evite `any`; use `unknown` quando o tipo for realmente desconhecido
- Use `strict` mode no tsconfig.json
- Prefira `interface` para objetos públicos
- Use `type` para unions, intersections e tipos complexos
- Defina tipos de retorno de funções explicitamente

### Estrutura de Arquivos
```
src/
├── types/           # Definições de tipos globais
├── interfaces/      # Interfaces compartilhadas
├── models/          # Classes de domínio
├── services/        # Lógica de negócio
├── controllers/     # Controladores
├── utils/           # Utilitários
└── config/          # Configurações
```

### Convenções

#### Interfaces vs Types
```typescript
// Use interface para objetos extensíveis
interface User {
  id: string;
  name: string;
  email: string;
}

// Use type para unions e tipos complexos
type UserRole = 'admin' | 'user' | 'guest';
type ApiResponse<T> = {
  data: T;
  error?: string;
};
```

#### Generics
```typescript
// Nomes descritivos para generics
function fetchData<TData, TError = Error>(
  url: string
): Promise<ApiResponse<TData, TError>> {
  // ...
}
```

#### Null Safety
```typescript
// Use optional chaining e nullish coalescing
const userName = user?.profile?.name ?? 'Anonymous';

// Prefira undefined sobre null
function getUser(id: string): User | undefined {
  // ...
}
```

## Exemplos

### Exemplo Completo: Service com TypeScript
```typescript
// types/user.types.ts
export interface User {
  id: string;
  name: string;
  email: string;
  role: UserRole;
  createdAt: Date;
}

export type UserRole = 'admin' | 'user' | 'guest';

export interface CreateUserDto {
  name: string;
  email: string;
  role?: UserRole;
}

export interface UpdateUserDto {
  name?: string;
  email?: string;
  role?: UserRole;
}

// services/user.service.ts
import { User, CreateUserDto, UpdateUserDto } from '../types/user.types';

export class UserService {
  async createUser(dto: CreateUserDto): Promise<User> {
    // Implementação
  }

  async getUserById(id: string): Promise<User | undefined> {
    // Implementação
  }

  async updateUser(id: string, dto: UpdateUserDto): Promise<User> {
    // Implementação
  }

  async deleteUser(id: string): Promise<void> {
    // Implementação
  }
}
```

### Exemplo: Error Handling com Types
```typescript
// types/errors.types.ts
export class AppError extends Error {
  constructor(
    message: string,
    public code: string,
    public statusCode: number = 500
  ) {
    super(message);
    this.name = 'AppError';
  }
}

export class NotFoundError extends AppError {
  constructor(resource: string) {
    super(`${resource} not found`, 'NOT_FOUND', 404);
    this.name = 'NotFoundError';
  }
}

// Uso
if (!user) {
  throw new NotFoundError('User');
}
```

## Anti-padrões

### ❌ Evitar
```typescript
// Não use any
function processData(data: any) {
  return data.value;
}

// Não ignore erros do TypeScript com @ts-ignore
// @ts-ignore
const result = someUntypedFunction();

// Não use tipos implícitos em funções públicas
function calculateTotal(items) {
  return items.reduce((sum, item) => sum + item.price, 0);
}

// Não use type assertion sem necessidade
const user = response.data as User; // Pode quebrar em runtime
```

### ✅ Fazer
```typescript
// Use tipos específicos ou unknown
function processData(data: unknown) {
  if (isValidData(data)) {
    return data.value;
  }
  throw new Error('Invalid data');
}

// Comente o porquê se realmente precisar de ts-ignore
// TODO: Fix type after updating library
// @ts-expect-error: Library types are outdated
const result = someUntypedFunction();

// Use tipos explícitos
interface Item {
  price: number;
}

function calculateTotal(items: Item[]): number {
  return items.reduce((sum, item) => sum + item.price, 0);
}

// Use type guards
function isUser(obj: unknown): obj is User {
  return (
    typeof obj === 'object' &&
    obj !== null &&
    'id' in obj &&
    'name' in obj
  );
}
```

## Configuração Recomendada

### tsconfig.json
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "lib": ["ES2020"],
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true,
    "declaration": true,
    "declarationMap": true,
    "sourceMap": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist", "**/*.test.ts"]
}
```

## Checklist

- [ ] tsconfig.json configurado com strict mode
- [ ] Todos os parâmetros de função têm tipos explícitos
- [ ] Tipos de retorno de funções públicas são explícitos
- [ ] Não há uso de `any` sem justificativa documentada
- [ ] Interfaces e types estão em arquivos separados e organizados
- [ ] Enums ou string literals para valores constantes
- [ ] Type guards para validações de tipo em runtime
- [ ] Null/undefined handling apropriado
- [ ] Generics usados quando apropriado
- [ ] Código compila sem erros do TypeScript

## Recursos
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/)
- [Effective TypeScript](https://effectivetypescript.com/)
