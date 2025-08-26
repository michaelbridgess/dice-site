# Database Setup Guide

## Current Status
The Fireblocks wallet integration is **architecturally complete** with all code changes made:
- ✅ Prisma schema updated with wallet models
- ✅ GraphQL resolvers refactored for wallet separation (REST for wallet ops)
- ✅ API routes created for Fireblocks integration
- ⏳ **Database migration pending** (requires database connection)

## Quick Setup Options

### Option 1: Docker PostgreSQL (Recommended)
```bash
# Start PostgreSQL with Docker
docker run --name casino-postgres -e POSTGRES_PASSWORD=password123 -e POSTGRES_DB=casino_db -p 5432:5432 -d postgres:15

# Create .env.local file
echo 'DATABASE_URL="postgresql://postgres:password123@localhost:5432/casino_db"' > .env.local
```

### Option 2: Local PostgreSQL Installation
1. Install PostgreSQL from https://www.postgresql.org/download/
2. Create database: `createdb casino_db`
3. Create `.env.local`:
```
DATABASE_URL="postgresql://postgres:your_password@localhost:5432/casino_db"
```

### Option 3: Cloud Database (Supabase/Neon)
1. Create free database at https://supabase.com or https://neon.tech
2. Copy connection string to `.env.local`:
```
DATABASE_URL="your_cloud_database_url_here"
```

## After Database Setup
```bash
# Run the migration to create tables
pnpm run db:migrate --name initial-setup

# Generate Prisma client with new models
pnpm run db:generate
```

## Environment Variables Needed
Create `.env.local` with:
```bash
# Database
DATABASE_URL="postgresql://postgres:password123@localhost:5432/casino_db"

# Fireblocks Wallet (get from Fireblocks dashboard)
FIREBLOCKS_API_KEY=your_fireblocks_api_key
FIREBLOCKS_SECRET_PATH=/absolute/path/to/fireblocks_secret.pem
# Or inline key
# FIREBLOCKS_SECRET_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----"
FIREBLOCKS_BASE_PATH=https://sandbox-api.fireblocks.io
FIREBLOCKS_VAULT_ACCOUNT_ID=0
NEXT_PUBLIC_FIREBLOCKS_DEFAULT_ASSET=ETH_TEST5

# Other required variables
JWT_SECRET="your-jwt-secret-key-here"
NEXTAUTH_URL="http://localhost:3000"
```

## What's Ready
- All Dfns code removed 
- Fireblocks integration code complete 
- Database schema updated 
- GraphQL resolvers updated 
- API routes created 

**Next Step**: Choose a database option above and run the migration!
