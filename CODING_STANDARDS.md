# 📋 MoneyMind Coding Standards

Panduan lengkap untuk menjaga kualitas dan konsistensi kode di seluruh proyek.

## Backend (NestJS)

### 1. Struktur File & Folder

```
src/
├── modules/
│   ├── auth/
│   │   ├── auth.controller.ts
│   │   ├── auth.service.ts
│   │   ├── auth.module.ts
│   │   ├── dto/
│   │   │   ├── login.dto.ts
│   │   │   └── register.dto.ts
│   │   ├── guards/
│   │   │   └── jwt.guard.ts
│   │   └── strategies/
│   │       └── jwt.strategy.ts
│   ├── users/
│   ├── transactions/
│   └── [other modules]/
├── common/
│   ├── decorators/
│   ├── filters/
│   ├── guards/
│   ├── interceptors/
│   ├── middleware/
│   └── pipes/
├── config/
├── database/
└── main.ts
```

### 2. Naming Conventions

```typescript
// Controllers - PascalCase dengan Controller suffix
auth.controller.ts          // ✓ Benar
AuthController             // ✓ Benar

// Services - PascalCase dengan Service suffix
auth.service.ts            // ✓ Benar
AuthService                // ✓ Benar

// DTOs - PascalCase dengan Dto suffix
login.dto.ts               // ✓ Benar
LoginDto                   // ✓ Benar

// Methods & Variables - camelCase
createUser()               // ✓ Benar
userId                     // ✓ Benar

// Constants - UPPER_SNAKE_CASE
API_PREFIX = '/api/v1'     // ✓ Benar
JWT_EXPIRY = '7d'          // ✓ Benar
```

### 3. Service Layer Pattern

```typescript
@Injectable()
export class AuthService {
  constructor(
    private prisma: PrismaService,
    private jwtService: JwtService,
  ) {}

  async register(dto: RegisterDto): Promise<AuthResponse> {
    // Validasi
    const existingUser = await this.prisma.user.findUnique({
      where: { email: dto.email },
    });

    if (existingUser) {
      throw new BadRequestException('Email already registered');
    }

    // Business logic
    const user = await this.prisma.user.create({
      data: { ...dto },
    });

    return { user, tokens: this.generateTokens(user.id) };
  }
}
```

### 4. Error Handling

```typescript
// Gunakan NestJS exceptions
throw new BadRequestException('Email already registered');
throw new UnauthorizedException('Invalid credentials');
throw new ForbiddenException('Access denied');
throw new NotFoundException('User not found');
```

### 5. Environment Variables

```bash
NODE_ENV=development
PORT=3001
DATABASE_URL="postgresql://user:password@localhost:5432/moneymind_dev"
JWT_SECRET=your-secret-key-min-32-chars-long
JWT_EXPIRY=15m
JWT_REFRESH_SECRET=your-refresh-secret-key
JWT_REFRESH_EXPIRY=7d
API_PREFIX=/api/v1
CORS_ORIGIN=http://localhost:3000,http://localhost:8081
```

---

## Frontend (Flutter)

### 1. Folder Structure (Clean Architecture)

```
lib/
├── config/
│   ├── router/              # Navigation routing
│   └── theme/               # App theme & styling
├── core/
│   ├── constants/           # App constants
│   ├── extensions/          # Dart extensions
│   ├── network/             # API client & endpoints
│   ├── services/            # Shared services
│   └── utils/               # Utilities & helpers
├── features/
│   ├── auth/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   ├── dashboard/
│   ├── transactions/
│   └── [other features]/
├── shared/
│   ├── providers/           # Global providers
│   └── widgets/             # Reusable widgets
└── main.dart
```

### 2. Naming Conventions

```dart
// Files - snake_case
auth_service.dart                  // ✓ Benar
user_repository.dart               // ✓ Benar
login_page.dart                    // ✓ Benar

// Classes - PascalCase
class AuthService {}               // ✓ Benar
class UserRepository {}            // ✓ Benar
class LoginPage {}                 // ✓ Benar

// Methods & Variables - camelCase
final userName = 'John';           // ✓ Benar
void getUserData() {}              // ✓ Benar

// Constants - camelCase
const appTitle = 'MoneyMind';      // ✓ Benar
const apiTimeout = Duration(seconds: 30);
```

### 3. Widget Pattern

```dart
class LoginPage extends StatelessWidget {
  const LoginPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Login')),
      body: const LoginForm(),
    );
  }
}
```

### 4. State Management dengan Provider

```dart
// Provider
final userProvider = FutureProvider((ref) async {
  return User.fromJson({'id': '1', 'name': 'John'});
});

// Usage di Widget
class UserWidget extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final userAsync = ref.watch(userProvider);

    return userAsync.when(
      data: (user) => Text(user.name),
      loading: () => const CircularProgressIndicator(),
      error: (error, stack) => Text('Error: $error'),
    );
  }
}
```

---

## General Rules

### Code Quality
- ✓ Gunakan linting tools (eslint, dart analyzer)
- ✓ Format code sebelum commit
- ✓ Write unit tests untuk business logic
- ✓ Add comments untuk logic kompleks
- ✓ Keep functions small dan focused

### Git Commits

```bash
# Format: type(scope): description
# Types: feat, fix, docs, style, refactor, perf, test, chore

git commit -m "feat(auth): add jwt token refresh mechanism"
git commit -m "fix(dashboard): resolve chart rendering bug"
git commit -m "docs(readme): update setup instructions"
git commit -m "refactor(transaction): simplify filter logic"
```

### Testing
- Write tests untuk semua business logic
- Target coverage: minimal 80%
- Gunakan mocking untuk external dependencies

### Security
- ✓ Never commit `.env` files
- ✓ Validate & sanitize user inputs
- ✓ Use HTTPS untuk production
- ✓ Hash passwords dengan bcrypt
- ✓ Implement rate limiting
- ✓ Add CORS properly

---

## Tools & Commands

### Backend
```bash
npm run format          # Format code
npm run lint            # Lint code
npm run test            # Run tests
npm run build           # Build application
npm run start:dev       # Development mode
```

### Frontend
```bash
dart format .           # Format code
dart analyze            # Analyze code
flutter test            # Run tests
flutter build apk       # Build APK
flutter run             # Run application
```

---

**Last Updated:** 2024
**Status:** Active
