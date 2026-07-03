# MoneyMind 💰

**MoneyMind** adalah aplikasi manajemen keuangan pribadi yang komprehensif dengan fitur analytics, budgeting, saving goals, dan AI Assistant.

## 🎯 Fitur Utama

- 💳 **Tracking Transaksi** - Catat pemasukan & pengeluaran
- 📊 **Dashboard Analytics** - Visualisasi data keuangan Anda
- 🎯 **Budget Planning** - Rencanakan dan monitor budget
- 🏦 **Saving Goals** - Kelola target tabungan
- 💬 **Hutang Piutang** - Catat utang dan piutang
- 📈 **Laporan Finansial** - Generate laporan detail
- 🤖 **AI Assistant** - Tips & rekomendasi keuangan
- 👨‍💼 **Admin Panel** - Manajemen sistem

## 🛠️ Tech Stack

### Frontend
- **Framework**: Flutter 3.x
- **State Management**: Provider / Riverpod
- **HTTP Client**: Dio
- **Local Storage**: Hive / SQLite
- **Charts**: FL Chart

### Backend
- **Framework**: NestJS 10.x
- **Database**: PostgreSQL 15
- **ORM**: Prisma
- **Authentication**: JWT + Refresh Token
- **Documentation**: Swagger/OpenAPI

### DevOps
- **Containerization**: Docker & Docker Compose
- **CI/CD**: GitHub Actions
- **Environment Management**: dotenv

## 📁 Struktur Proyek

```
moneymind/
├── backend/                    # NestJS Backend
│   ├── src/
│   │   ├── auth/              # Authentication module
│   │   ├── users/             # User management
│   │   ├── transactions/      # Transaction module
│   │   ├── budget/            # Budget module
│   │   ├── savings/           # Savings goals
│   │   ├── debts/             # Debt management
│   │   ├── reports/           # Reports generation
│   │   ├── ai-assistant/      # AI features
│   │   ├── admin/             # Admin features
│   │   ├── common/            # Shared utilities
│   │   └── main.ts
│   ├── prisma/                # Database schema
│   ├── .env.example
│   ├── docker-compose.yml
│   └── package.json
│
├── frontend/                   # Flutter Frontend
│   ├── lib/
│   │   ├── features/          # Feature modules
│   │   │   ├── auth/
│   │   │   ├── dashboard/
│   │   │   ├── transactions/
│   │   │   ├── budget/
│   │   │   ├── savings/
│   │   │   ├── debts/
│   │   │   └── reports/
│   │   ├── core/              # Core utilities
│   │   │   ├── constants/
│   │   │   ├── services/
│   │   │   ├── providers/
│   │   │   └── theme/
│   │   ├── shared/            # Shared widgets
│   │   └── main.dart
│   ├── pubspec.yaml
│   └── analysis_options.yaml
│
├── .github/
│   └── workflows/             # CI/CD pipelines
│
├── docs/                      # Documentation
├── docker-compose.yml         # Main compose file
├── .env.example              # Environment template
└── CODING_STANDARDS.md       # Coding guidelines
```

## 🚀 Quick Start

### Prerequisites
- Flutter 3.x
- Node.js 18.x
- PostgreSQL 15
- Docker & Docker Compose

### Setup Backend
```bash
cd backend
cp .env.example .env
npm install
npx prisma migrate dev
npm run start:dev
```

### Setup Frontend
```bash
cd frontend
flutter pub get
flutter run
```

### Docker Setup
```bash
docker-compose up -d
```

## 📋 Development Roadmap

- [x] **Prompt 01** - Project Foundation
- [ ] **Prompt 02** - Authentication
- [ ] **Prompt 03** - Database
- [ ] **Prompt 04** - Dashboard
- [ ] **Prompt 05** - Transaksi
- [ ] **Prompt 06** - Budget
- [ ] **Prompt 07** - Tabungan
- [ ] **Prompt 08** - Hutang Piutang
- [ ] **Prompt 09** - Laporan
- [ ] **Prompt 10** - AI Assistant
- [ ] **Prompt 11** - Admin Panel
- [ ] **Prompt 12** - Deployment
- [ ] **Prompt 13** - Testing
- [ ] **Prompt 14** - Production Ready

## 📝 Documentation

- [Backend Setup](./backend/README.md)
- [Frontend Setup](./frontend/README.md)
- [Coding Standards](./CODING_STANDARDS.md)
- [API Documentation](./docs/API.md)
- [Database Schema](./docs/DATABASE.md)

## 🤝 Contributing

Lihat [CODING_STANDARDS.md](./CODING_STANDARDS.md) untuk panduan development.

## 📄 License

MIT License - Silakan gunakan untuk keperluan pribadi atau komersial.

---

**Made with ❤️ by MoneyMind Team**
