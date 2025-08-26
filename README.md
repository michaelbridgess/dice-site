# 🎲 Enterprise Dual Currency Casino Platform

A **clean, maintainable** dice casino with enterprise-grade architecture:

- **🎯 Provably-Fair Dice Game** (HMAC-SHA256, cryptographic seed management)
- **💰 GAAP-Compliant Double-Entry Ledger** (FASB ASC 924 for casino accounting)
- **🪙 Dual Currency System** (Gold Coins + dice Cash) like Stake.us model
- **🔐 Secure Wallet Operations** fireblocks
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

## 🛠️ onitoring, audit trails, compliance   |

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
         │                       
         │                                   │ fireblocks API
         │                                   ▼
         │                        ┌──────────────────┐
         │                        │ Fireblocks Wallet      │
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

tional features
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

