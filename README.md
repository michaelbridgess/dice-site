# 🎲 Enterprise Dual Currency Casino Platform

A **clean, maintainable** dice casino with enterprise-grade architecture:

- **🎯 Provably-Fair Dice Game** (HMAC-SHA256, cryptographic seed management)
- **💰 GAAP-Compliant Double-Entry Ledger** (FASB ASC 924 for casino accounting)
- **🪙 Dual Currency System** (Gold Coins + Stake Cash) like Stake.us model
- **🔐 Secure Wallet Operations** via Dfns API with enterprise-grade security
- **🚀 Modern Tech Stack** (Next.js 13+, GraphQL, TypeScript, Prisma)
- **💬 Real-time Features** (Live chat, balance updates, game subscriptions)

---

## 🏛️ Financial Compliance & Architecture

### Regulatory Compliance
- **🇺🇸 U.S. Standards:** GAAP → FASB ASC 924 (Entertainment—Casinos)
- **🌍 International:** IFRS 15 (Revenue from Contracts with Customers)
- **📚 Accounting Foundation:** Double-entry bookkeeping with tailored chart of accounts
- **🔍 Audit Trail:** Comprehensive logging for regulatory compliance
- **⚖️ Risk Management:** Anti-fraud detection and velocity pattern analysis  

---

## 🛠️ Clean Tech Stack & Architecture

| Layer                    | Technology                                        |
|--------------------------|---------------------------------------------------|
| **Frontend**             | Next.js 13+ (App Router) + React + TypeScript    |
| **API Layer**            | GraphQL (Apollo Server) + Real-time Subscriptions|
| **Database & ORM**       | PostgreSQL + Prisma (ACID transactions)          |
| **Wallet Infrastructure**| Dfns API + Secure Key Management                 |
| **Currency System**      | Dual Currency (GC/SC) + Multi-balance Support   |
| **Blockchain Service**   | Dfns Enterprise Wallet API                      |
| **Cache & Pub/Sub**      | Redis (rate limiting, fraud detection, chat)     |
| **Authentication**       | Supabase (with RLS policies)                     |
| **Security**             | Encrypted key storage, rate limiting, validation |
| **Monitoring**           | Financial monitoring, audit trails, compliance   |

### 🏗️ System Architecture

```text
┌─────────────────┐   GraphQL/WS   ┌──────────────────┐   SQL   ┌─────────────────┐
│ Next.js 13+     │◀──────────────▶│ Apollo Server    │◀───────▶│ PostgreSQL      │
│ • Dice Game UI  │                │ • GraphQL API    │         │ • Double-Entry  │
│ • Real-time Chat│                │ • Subscriptions  │         │ • User Data     │
│ • Wallet Mgmt   │                │ • Authentication │         │ • Audit Logs    │
└─────────────────┘                └──────────────────┘         └─────────────────┘
         ▲                                   │                           ▲
         │                                   │ HTTP/REST                 │
         │                                   ▼                           │
         │                        ┌──────────────────┐                   │
         │                        │ Python FastAPI   │                   │
         │                        │ • BlockCypher    │───────────────────┘
         │                        │ • Wallet Manager │
         │                        │ • Tx Manager     │
         │                        │ • Secure Keys    │
         │                        └──────────────────┘
         │                                   │
         │                                   │ Dfns API
         │                                   ▼
         │                        ┌──────────────────┐
         │                        │ Dfns Wallet      │
         │                        │ • Address Gen    │
         │                        │ • Transactions   │
         │                        │ • Multi-Currency │
         │                        └──────────────────┘
         │
         │ Redis Pub/Sub
         ▼
┌─────────────────┐
│ Redis Cache     │
│ • Rate Limiting │
└─────────────────┘
```

## Key Features Implemented

### Gaming Features
- **Provably Fair Dice Game** with HMAC-SHA256 verification
- **Manual & Auto Betting** with customizable settings
- **Hotkey Support** for power users (Space to bet, A/S for amounts)
- **Real-time Results** with instant balance updates
- **Fairness Verification** modal with seed management

### Financial System
- **Double-Entry Ledger** (GAAP/FASB ASC 924 compliant)
- **Dual Currency System** (Gold Coins + Stake Cash)
- **Secure Wallet Management** via Dfns enterprise API
- **Multi-Currency Balance Tracking** with real-time updates
- **Comprehensive Audit Trail** for compliance
- **Stake.us Model Implementation** (GC purchasable, SC redeemable)

### Security & Compliance
- **Rate Limiting** with Redis-based fraud detection
- **Encrypted Key Storage** with secure wallet management
- **Input Validation** with Zod schemas
- **Anti-Fraud Detection** with velocity pattern analysis
- **Comprehensive Monitoring** with alerting

### Social Features
- **Real-time Chat** with Supabase integration
- **User Presence** indicators
- **Typing Indicators** and message persistence
- **Online User Display** with avatars

## Recent Improvements

### 🪙 Dual Currency System Implementation
- **Complete BlockCypher Removal** - Migrated to Dfns enterprise wallet API
- **Dual Currency Support** - Gold Coins (GC) and Stake Cash (SC) like Stake.us
- **Multi-Currency Balance Management** - Separate balances per currency type
- **Real-time Currency Switching** - Seamless play mode toggle in game interface
- **Clean UI Integration** - Removed all Bitcoin/BTC references from game

### 🎮 Game Interface Enhancements
- **Unified Play Mode Control** - Single toggle for Standard (GC) vs Promotional (SC)
- **Real-time Balance Updates** - Live balance display with currency formatting
- **Removed Duplicate Controls** - Clean, single-source-of-truth architecture
- **Enhanced User Experience** - Smooth currency switching without page reload

### 🏗️ Architecture Improvements
- **Dfns Integration** - Enterprise-grade wallet security and management
- **Prisma Schema Updates** - Multi-currency support with proper relations
- **GraphQL Enhancements** - Dual currency queries and mutations
- **Type Safety** - Full TypeScript coverage for currency operations

## Getting Started

### Prerequisites
- Node.js 18+ LTS
- PostgreSQL 14+
- Redis 6+ (optional for advanced features)
- Dfns API account (for wallet operations)

### Environment Setup
```bash
# Core environment
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_key
DATABASE_URL=postgresql://user:pass@localhost:5432/casino

# Dfns Wallet Integration
DFNS_APP_ID=your_dfns_app_id
DFNS_AUTH_TOKEN=your_dfns_auth_token
DFNS_BASE_URL=https://api.dfns.co
DFNS_WALLET_ID=your_dfns_wallet_id

# Optional features
REDIS_URL=redis://localhost:6379
```

### Quick Start
```bash
# Install dependencies
npm install
cd python-blockcypher && pip install -r requirements.txt

# Start services
npm run dev          # Frontend (port 3000)
npm run server:dev   # GraphQL API (port 4000)
cd python-blockcypher && python src/api_service.py  # BlockCypher service (port 8000)
```

## Project Structure

```
├── app/                    # Next.js 13+ app directory
├── components/             # React components
│   ├── game-interface/     # Dice game UI
│   ├── Chat/              # Real-time chat
│   └── ui/                # Reusable UI components
├── hooks/                 # Custom React hooks
├── lib/                   # Core business logic
│   ├── graphql/           # GraphQL resolvers & schema
│   ├── ledger/            # Double-entry accounting
│   ├── security/          # Rate limiting & fraud detection
│   ├── monitoring/        # Financial monitoring
│   └── audit/             # Compliance & audit trails
├── python-blockcypher/    # Python microservice
│   └── src/
│       ├── api_service.py     # Clean FastAPI service
│       ├── wallet_manager.py  # Wallet operations
│       ├── transaction_manager.py # Transaction handling
│       ├── models.py          # Pydantic models
│       └── utils.py           # Utility functions
└── prisma/                # Database schema & migrations
```

## Next Steps

1. **Enhanced Deposit Flow** - Implement more sophisticated deposit handling
2. **BlockCypher Decoupling** - Reduce database dependencies in blockchain service
3. **Advanced Analytics** - Player behavior and financial reporting
4. **Mobile Optimization** - Responsive design improvements
5. **Multi-Game Support** - Extend platform for additional games

---

**Built with ❤️ for maintainability, security, and compliance.**
