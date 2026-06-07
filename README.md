
# ERRORBASE

### The Self-Hosted Firebase Alternative | Complete Backend Platform

<div align="center">
  <img src="https://img.shields.io/badge/Status-Production_Ready-00C853?style=for-the-badge">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows%20%7C%20Mac-0078D4?style=for-the-badge">
  <img src="https://img.shields.io/badge/Backend-Node.js%20%7C%20TypeScript-339933?style=for-the-badge">
  <img src="https://img.shields.io/badge/Database-PostgreSQL-4169E1?style=for-the-badge">
  <img src="https://img.shields.io/badge/Frontend-React%20%7C%20Tailwind-61DAFB?style=for-the-badge">
  <img src="https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge">

  [![Telegram](https://img.shields.io/badge/Telegram-@ERROR0101risback-26A5E4?style=for-the-badge)](https://t.me/ERROR0101risback)
  [![Instagram](https://img.shields.io/badge/Instagram-@fahad0101r-E4405F?style=for-the-badge)](https://instagram.com/fahad0101r)
  [![GitHub](https://img.shields.io/badge/GitHub-ERROR0101r-181717?style=for-the-badge)](https://github.com/ERROR0101r)

  <p><strong>Developer: @ERROR0101risback</strong></p>
  <p><em>Version: 1.0.0 | Production Ready</em></p>
</div>

---

## 📋 TABLE OF CONTENTS

- [Why ErrorBase?](#why-errorbase)
- [Features](#features)
- [Quick Setup](#quick-setup)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Configuration Guide](#configuration-guide)
- [Docker Deployment](#docker-deployment)
- [API Endpoints](#api-endpoints)
- [Dashboard Guide](#dashboard-guide)
- [Security Features](#security-features)
- [Environment Variables](#environment-variables)
- [Commands List](#commands-list)
- [Step by Step Tutorial](#step-by-step-tutorial)
- [Report Bugs](#report-bugs)
- [Developer Contact](#developer-contact)
- [License](#license)

---

## WHY ERRORBASE?

**The Problem with Firebase / Supabase Cloud:**

- Your data lives on someone else's servers
- You pay for every API request and every GB of storage
- Your app can be rate-limited or banned without warning
- Your user data can be mined for AI training
- Vendor lock-in makes migration nearly impossible
- Offline or air-gapped deployment is impossible

**How ErrorBase Solves This:**

- Your data stays on YOUR infrastructure
- Pay ZERO dollars for API calls and storage
- Complete control over rate limits and quotas
- No third-party access to user data ever
- Full PostgreSQL access and backups
- Works offline, air-gapped, or on-premise

**Comparison:**

| Feature | Firebase | Supabase Cloud | ErrorBase |
|---------|----------|----------------|-----------|
| Self-Hosted | No | Limited | Yes Free |
| Data Ownership | No | No | Yes 100% |
| Cost for 100K requests | $0.60 | $0.25 | $0.00 |
| Vendor Lock-in | Yes | Partial | No |
| Offline Capable | No | Limited | Yes |
| Row Level Security | No | Yes | Yes |

---

## FEATURES

**🗄️ Database Layer**
- PostgreSQL connection pool manager
- Schema reflection for tables, columns, relationships
- Auto-migration system for initial setup
- Row-Level Security (RLS) simulation with middleware

**📡 Auto-Generated REST API**
- GET /api/rest/v1/{table} - List records with filters
- POST /api/rest/v1/{table} - Insert record
- PATCH /api/rest/v1/{table} - Update record(s)
- DELETE /api/rest/v1/{table} - Delete record(s)
- GET /api/rest/v1/rpc/{function} - Call stored procedures
- Query params: select, order, limit, offset
- Filters: eq, ne, gt, lt, gte, lte, like, ilike, in, is

**🔐 Authentication System**
- POST /auth/v1/signup - Email/password registration
- POST /auth/v1/signin - Login with JWT issuance
- GET /auth/v1/user - Get current user profile
- POST /auth/v1/refresh - Token refresh endpoint
- POST /auth/v1/logout - Invalidate tokens
- Password reset flow with email
- Rate limiting: 5 attempts per minute per IP

**⚡ Realtime Subscriptions**
- WebSocket endpoint: /realtime/v1/websocket
- Channel types: presence, broadcast, postgres_changes
- Listen to INSERT/UPDATE/DELETE on specific tables
- Broadcast messages between connected clients
- Presence tracking for online users

**📁 File Storage**
- POST /storage/v1/bucket - Create bucket
- GET /storage/v1/bucket/{name}/list - List objects
- PUT /storage/v1/bucket/{name}/upload - Upload file
- GET /storage/v1/bucket/{name}/download/{path} - Download
- DELETE /storage/v1/bucket/{name}/delete/{path} - Delete
- File size limit: 50MB default
- MIME type validation for images, PDFs, videos

**🖥️ Admin Dashboard**
- Project overview with API keys and URL
- Table browser with CRUD operations
- SQL editor with syntax highlighting
- Auth users management
- API logs and metrics
- Storage browser
- Dark/light theme toggle

**🛡️ Security Features**
- All passwords hashed with bcrypt (10+ rounds)
- JWT stored in HTTP-only cookies
- CSRF protection on state-changing endpoints
- Helmet.js for security headers
- Input sanitization for all SQL queries
- CORS properly configured
- Rate limiting per user/IP

---

## QUICK SETUP

**One Command Setup:**

```bash
git clone https://github.com/ERROR0101r/errorbase.git
cd errorbase
```

Docker Setup (Recommended):

```bash
# Start everything
docker-compose up -d

# Check if running
docker-compose ps

# View logs
docker-compose logs -f

# Stop everything
docker-compose down

# Stop and delete volumes (reset database)
docker-compose down -v
```

Access Services:

```
Dashboard:    http://localhost:5173
API Server:   http://localhost:3000
PostgreSQL:   localhost:5432
pgAdmin:      http://localhost:5050
```

Manual Setup (Without Docker):

```bash
# Backend
cd server
cp .env.example .env
# Edit .env with your database credentials
npm install
npm run migrate
npm run dev

# Dashboard (open new terminal)
cd dashboard
npm install
npm run dev
```

---

TECH STACK

Backend Server

· Runtime: Node.js (v20+)
· Language: TypeScript (v5+)
· Framework: Express (v4)
· Database Driver: pg (v8+)
· Authentication: jsonwebtoken, bcrypt
· Realtime: Socket.io (v4)
· File Upload: Multer
· Logging: Winston
· Security: Helmet, cors, express-rate-limit

Frontend Dashboard

· Framework: React (v18)
· Language: TypeScript
· Styling: TailwindCSS
· Components: Shadcn/ui
· State: TanStack Query
· HTTP Client: Axios
· Build Tool: Vite
· Code Editor: Monaco Editor

Database

· Primary: PostgreSQL 15
· Management: pgAdmin 4
· Migration: Custom migration system

Infrastructure

· Container: Docker + Docker Compose
· Proxy: Nginx (production)
· SSL: Let's Encrypt (optional)

---

PROJECT STRUCTURE

```
errorbase/
│
├── server/
│   ├── src/
│   │   ├── config/
│   │   │   ├── database.ts
│   │   │   ├── jwt.ts
│   │   │   └── env.ts
│   │   ├── controllers/
│   │   │   ├── auth.controller.ts
│   │   │   ├── rest.controller.ts
│   │   │   ├── storage.controller.ts
│   │   │   └── realtime.controller.ts
│   │   ├── middleware/
│   │   │   ├── auth.middleware.ts
│   │   │   ├── rls.middleware.ts
│   │   │   ├── rate-limit.ts
│   │   │   └── validation.ts
│   │   ├── models/
│   │   │   ├── user.model.ts
│   │   │   └── session.model.ts
│   │   ├── routes/
│   │   │   ├── auth.routes.ts
│   │   │   ├── rest.routes.ts
│   │   │   ├── storage.routes.ts
│   │   │   └── realtime.routes.ts
│   │   ├── services/
│   │   │   ├── db.service.ts
│   │   │   ├── auth.service.ts
│   │   │   ├── storage.service.ts
│   │   │   └── realtime.service.ts
│   │   ├── utils/
│   │   │   ├── logger.ts
│   │   │   └── helpers.ts
│   │   └── index.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── .env.example
│
├── dashboard/
│   ├── src/
│   │   ├── components/
│   │   │   ├── TableBrowser.tsx
│   │   │   ├── SQLEditor.tsx
│   │   │   ├── StorageBrowser.tsx
│   │   │   ├── UserManager.tsx
│   │   │   ├── LogViewer.tsx
│   │   │   └── Layout.tsx
│   │   ├── pages/
│   │   │   ├── Dashboard.tsx
│   │   │   ├── Tables.tsx
│   │   │   ├── SQL.tsx
│   │   │   ├── Auth.tsx
│   │   │   ├── Storage.tsx
│   │   │   ├── Logs.tsx
│   │   │   └── Settings.tsx
│   │   ├── hooks/
│   │   │   ├── useAuth.ts
│   │   │   ├── useTables.ts
│   │   │   └── useRealtime.ts
│   │   ├── lib/
│   │   │   ├── api.ts
│   │   │   └── utils.ts
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── package.json
│   └── vite.config.ts
│
├── docker-compose.yml
├── docker-compose.prod.yml
├── .env.example
├── schema.sql
├── openapi.yaml
└── README.md
```

---

CONFIGURATION GUIDE

⚠️ IMPORTANT: Change These Values Before Production!

.env file (server/.env):

```env
# ==================== SERVER ====================
PORT=3000
NODE_ENV=production

# ==================== DATABASE ====================
DB_HOST=postgres
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=CHANGE_THIS_STRONG_PASSWORD
DB_NAME=errorbase
DB_POOL_MIN=2
DB_POOL_MAX=10

# ==================== JWT SECURITY ====================
# Generate with: node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
JWT_SECRET=GENERATE_RANDOM_64_CHAR_STRING_HERE
JWT_EXPIRY=7d
REFRESH_TOKEN_SECRET=ANOTHER_RANDOM_64_CHAR_STRING_HERE
REFRESH_TOKEN_EXPIRY=30d
SALT_ROUNDS=10

# ==================== CORS ====================
CORS_ORIGIN=http://localhost:5173,https://yourdomain.com

# ==================== STORAGE ====================
STORAGE_PATH=./uploads
MAX_FILE_SIZE=52428800
ALLOWED_MIME_TYPES=image/jpeg,image/png,image/gif,application/pdf,video/mp4

# ==================== RATE LIMITING ====================
RATE_LIMIT_WINDOW_MS=60000
RATE_LIMIT_MAX_REQUESTS=100
AUTH_RATE_LIMIT_MAX=5

# ==================== LOGGING ====================
LOG_LEVEL=info
LOG_DIR=./logs

# ==================== REALTIME ====================
WS_HEARTBEAT_INTERVAL=30000
MAX_WS_CONNECTIONS=10000
```

How to Generate Secure Secrets:

```bash
# Method 1: OpenSSL (Linux/Mac/WSL)
openssl rand -hex 32

# Method 2: Node.js
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"

# Method 3: PowerShell (Windows)
[Convert]::ToBase64String([System.Security.Cryptography.RandomNumberGenerator]::GetBytes(32))
```

---

DOCKER DEPLOYMENT

docker-compose.yml:

```yaml
version: '3.8'

services:
  postgres:
    image: postgres:15-alpine
    container_name: errorbase-postgres
    environment:
      POSTGRES_USER: ${DB_USER:-postgres}
      POSTGRES_PASSWORD: ${DB_PASSWORD:-errorbase123}
      POSTGRES_DB: ${DB_NAME:-errorbase}
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./schema.sql:/docker-entrypoint-initdb.d/schema.sql
    ports:
      - "5432:5432"
    networks:
      - errorbase-network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      interval: 10s
      timeout: 5s
      retries: 5

  pgadmin:
    image: dpage/pgadmin4:latest
    container_name: errorbase-pgadmin
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@errorbase.com
      PGADMIN_DEFAULT_PASSWORD: admin
    ports:
      - "5050:80"
    networks:
      - errorbase-network
    depends_on:
      - postgres

  backend:
    build: ./server
    container_name: errorbase-backend
    environment:
      DB_HOST: postgres
      DB_PORT: 5432
      DB_USER: ${DB_USER:-postgres}
      DB_PASSWORD: ${DB_PASSWORD:-errorbase123}
      DB_NAME: ${DB_NAME:-errorbase}
      JWT_SECRET: ${JWT_SECRET}
      REFRESH_TOKEN_SECRET: ${REFRESH_TOKEN_SECRET}
    ports:
      - "3000:3000"
    volumes:
      - ./server:/app
      - /app/node_modules
      - uploads:/app/uploads
    networks:
      - errorbase-network
    depends_on:
      postgres:
        condition: service_healthy
    command: npm run dev

  dashboard:
    build: ./dashboard
    container_name: errorbase-dashboard
    ports:
      - "5173:5173"
    volumes:
      - ./dashboard:/app
      - /app/node_modules
    networks:
      - errorbase-network
    depends_on:
      - backend
    environment:
      VITE_API_URL: http://localhost:3000

volumes:
  postgres_data:
  uploads:

networks:
  errorbase-network:
    driver: bridge
```

Production Commands:

```bash
# Build and start production stack
docker-compose -f docker-compose.prod.yml up -d

# Scale backend instances
docker-compose up -d --scale backend=3

# Backup database
docker exec errorbase-postgres pg_dump -U postgres errorbase > backup.sql

# Restore database
cat backup.sql | docker exec -i errorbase-postgres psql -U postgres errorbase

# View logs
docker-compose logs -f backend

# Restart a specific service
docker-compose restart backend
```

---

API ENDPOINTS

Auto-Generated REST API

```
GET    /api/rest/v1/{table}              List records with filters
GET    /api/rest/v1/{table}/{id}         Get single record
POST   /api/rest/v1/{table}              Insert record
PATCH  /api/rest/v1/{table}              Update record(s)
DELETE /api/rest/v1/{table}              Delete record(s)
GET    /api/rest/v1/rpc/{function}       Call stored procedure
```

Query Parameters

```
select=col1,col2                         Select specific fields
order=column.desc                        Sort order
limit=100                                Limit results
offset=0                                 Pagination offset

Filters:
column=eq.value                          Equal to
column=ne.value                          Not equal to
column=gt.value                          Greater than
column=lt.value                          Less than
column=gte.value                         Greater than or equal
column=lte.value                         Less than or equal
column=like.*value*                      Contains pattern
column=ilike.*value*                     Case-insensitive contains
column=in.1,2,3                          In array
column=is.null                           Is NULL
```

cURL Examples

```bash
# Get all users
curl http://localhost:3000/api/rest/v1/users

# Get users with pagination
curl "http://localhost:3000/api/rest/v1/users?limit=10&offset=0"

# Filter users by age
curl "http://localhost:3000/api/rest/v1/users?age=gt.18"

# Search users by name
curl "http://localhost:3000/api/rest/v1/users?name=like.*john*"

# Select specific fields
curl "http://localhost:3000/api/rest/v1/users?select=id,email"

# Create record
curl -X POST http://localhost:3000/api/rest/v1/products \
  -H "Content-Type: application/json" \
  -d '{"name":"Laptop","price":999,"stock":10}'

# Update record
curl -X PATCH http://localhost:3000/api/rest/v1/products?id=eq.1 \
  -H "Content-Type: application/json" \
  -d '{"price":899}'

# Delete record
curl -X DELETE "http://localhost:3000/api/rest/v1/products?id=eq.1"
```

Authentication API

```
POST   /auth/v1/signup                    Register new user
POST   /auth/v1/signin                    Login (returns JWT cookie)
GET    /auth/v1/user                      Get current user profile
POST   /auth/v1/refresh                   Refresh JWT token
POST   /auth/v1/logout                    Logout user
POST   /auth/v1/reset-password            Request password reset
POST   /auth/v1/update-password           Update password with token
```

Auth cURL Examples

```bash
# Signup
curl -X POST http://localhost:3000/auth/v1/signup \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"SecurePass123!"}'

# Signin
curl -X POST http://localhost:3000/auth/v1/signin \
  -H "Content-Type: application/json" \
  -c cookies.txt \
  -d '{"email":"user@example.com","password":"SecurePass123!"}'

# Get current user (with cookie)
curl http://localhost:3000/auth/v1/user -b cookies.txt

# Refresh token
curl -X POST http://localhost:3000/auth/v1/refresh -b cookies.txt

# Logout
curl -X POST http://localhost:3000/auth/v1/logout -b cookies.txt
```

Storage API

```
POST   /storage/v1/bucket                 Create new bucket
GET    /storage/v1/bucket                 List all buckets
DELETE /storage/v1/bucket/{name}          Delete empty bucket
GET    /storage/v1/bucket/{name}/list     List objects in bucket
PUT    /storage/v1/bucket/{name}/upload   Upload file
GET    /storage/v1/bucket/{name}/download/{path}  Download file
DELETE /storage/v1/bucket/{name}/delete/{path}    Delete file
POST   /storage/v1/bucket/{name}/move     Move/copy file
```

Storage cURL Examples

```bash
# Create bucket
curl -X POST http://localhost:3000/storage/v1/bucket \
  -H "Content-Type: application/json" \
  -d '{"name":"avatars","public":true}'

# Upload file
curl -X PUT http://localhost:3000/storage/v1/bucket/avatars/upload \
  -F "file=@profile.jpg" \
  -F "path=users/123/avatar.jpg"

# List files
curl http://localhost:3000/storage/v1/bucket/avatars/list?path=users/123

# Download file
curl http://localhost:3000/storage/v1/bucket/avatars/download/users/123/avatar.jpg -o avatar.jpg

# Delete file
curl -X DELETE "http://localhost:3000/storage/v1/bucket/avatars/delete/users/123/avatar.jpg"
```

Realtime WebSocket

```javascript
// Connect to WebSocket
const ws = new WebSocket('ws://localhost:3000/realtime/v1/websocket');

// Authentication (send JWT after connect)
ws.onopen = () => {
  ws.send(JSON.stringify({
    type: 'auth',
    token: 'your-jwt-token'
  }));
};

// Subscribe to table changes
ws.send(JSON.stringify({
  type: 'subscribe',
  channel: 'users_changes',
  table: 'users',
  event: '*'
}));

// Presence channel (track online users)
ws.send(JSON.stringify({
  type: 'presence',
  channel: 'chat_room',
  state: { user_id: 123, name: 'John' }
}));

// Broadcast message
ws.send(JSON.stringify({
  type: 'broadcast',
  channel: 'chat_room',
  event: 'message',
  payload: { text: 'Hello everyone!' }
}));

// Listen for messages
ws.onmessage = (event) => {
  const data = JSON.parse(event.data);
  console.log('Received:', data);
};

// Unsubscribe
ws.send(JSON.stringify({
  type: 'unsubscribe',
  channel: 'users_changes'
}));
```

---

DASHBOARD GUIDE

Pages Overview

· / - Overview with API keys, project URL, system metrics
· /tables - Table browser with CRUD operations, filter, sort, paginate
· /sql - SQL editor with syntax highlighting, save queries, export results
· /auth - View/manage users, reset passwords, assign roles
· /storage - Browse buckets, upload/download files, manage folders
· /logs - View request/response logs, filter by status/endpoint
· /settings - Configure CORS, API keys, rate limits, theme

Dashboard Features

· Table Browser: View any table with pagination, click "Add Record" to insert, double-click cell to edit, click "Delete" row to remove, filter columns with search, sort by any column, export to CSV/JSON
· SQL Editor: Monaco editor with syntax highlighting, run SELECT/INSERT/UPDATE/DELETE, save frequently used queries, export query results, view query execution time
· Storage Browser: Drag & drop file upload, create/delete folders, preview images, generate signed URLs, set file as public/private
· User Management: View all registered users, reset user password, enable/disable accounts, assign admin role, view login history

---

SECURITY FEATURES

Security Architecture Layers

Layer 1 - Network Security

· HTTPS enforcement (production)
· CORS with strict origin validation
· Docker network isolation

Layer 2 - Authentication

· bcrypt password hashing (10+ rounds)
· JWT stored in HTTP-only cookies
· Refresh token rotation
· Session invalidation on logout

Layer 3 - Request Security

· Rate limiting (100 req/min per IP)
· Auth rate limiting (5 attempts/min)
· Helmet.js security headers
· Request size limits

Layer 4 - Database Security

· Parameterized queries (no SQL injection)
· Row Level Security (RLS) middleware
· Connection pooling with limits
· Query timeout protection

Layer 5 - File Security

· MIME type validation
· File size limits (50MB default)
· Filename sanitization

Layer 6 - Logging & Monitoring

· Winston request/response logging
· Failed login tracking
· API usage metrics
· Audit trails for admin actions

Row Level Security Implementation

```sql
-- RLS policies in PostgreSQL
CREATE POLICY user_own_data ON users
    USING (user_id = current_setting('app.current_user_id')::uuid);

CREATE POLICY admin_all_access ON users
    USING (current_setting('app.user_role') = 'admin');
```

```typescript
// RLS Middleware
export const rlsMiddleware = async (req, res, next) => {
  if (req.user) {
    await db.query(`
      SET app.current_user_id = '${req.user.id}';
      SET app.user_role = '${req.user.role}';
    `);
  }
  next();
};
```

---

ENVIRONMENT VARIABLES

```env
# ==================== SERVER CONFIGURATION ====================
PORT=3000
NODE_ENV=production
HOST=0.0.0.0

# ==================== DATABASE ====================
DB_HOST=postgres
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=errorbase123
DB_NAME=errorbase
DB_POOL_MIN=2
DB_POOL_MAX=10
DB_POOL_IDLE_TIMEOUT=30000
DB_CONNECTION_TIMEOUT=2000
DB_SSL=false

# ==================== JWT AUTHENTICATION ====================
JWT_SECRET=your-super-secret-key-change-this
JWT_EXPIRY=7d
REFRESH_TOKEN_SECRET=another-secret-key-for-refresh
REFRESH_TOKEN_EXPIRY=30d
SALT_ROUNDS=10

# ==================== CORS ====================
CORS_ORIGIN=http://localhost:5173,https://yourdomain.com
CORS_CREDENTIALS=true
CORS_MAX_AGE=86400

# ==================== FILE STORAGE ====================
STORAGE_TYPE=local
STORAGE_PATH=./uploads
MAX_FILE_SIZE=52428800
ALLOWED_MIME_TYPES=image/jpeg,image/png,image/gif,application/pdf,video/mp4

# S3 Compatible (optional)
S3_ENDPOINT=https://s3.amazonaws.com
S3_ACCESS_KEY=your-access-key
S3_SECRET_KEY=your-secret-key
S3_BUCKET=errorbase-storage
S3_REGION=us-east-1

# ==================== RATE LIMITING ====================
RATE_LIMIT_WINDOW_MS=60000
RATE_LIMIT_MAX_REQUESTS=100
AUTH_RATE_LIMIT_WINDOW_MS=60000
AUTH_RATE_LIMIT_MAX=5

# ==================== REALTIME WEBSOCKET ====================
WS_PATH=/realtime/v1
WS_HEARTBEAT_INTERVAL=30000
WS_MAX_CONNECTIONS=10000
WS_MESSAGE_SIZE_LIMIT=1048576

# ==================== LOGGING ====================
LOG_LEVEL=info
LOG_DIR=./logs
LOG_MAX_FILES=30
LOG_MAX_SIZE=10485760

# ==================== EMAIL (for password reset) ====================
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password
SMTP_FROM=noreply@errorbase.com
EMAIL_RESET_URL=http://localhost:5173/reset-password

# ==================== ADMIN DASHBOARD ====================
ADMIN_API_KEY=change-this-admin-key
DASHBOARD_SESSION_TIMEOUT=3600000

# ==================== SECURITY ====================
HELMET_ENABLED=true
COMPRESSION_ENABLED=true
TRUST_PROXY=false
RATE_LIMITER_ENABLED=true

# ==================== FEATURE FLAGS ====================
ENABLE_REALTIME=true
ENABLE_STORAGE=true
ENABLE_AUTO_API=true
ENABLE_SQL_EDITOR=true
```

---

COMMANDS LIST

Docker Commands

```bash
docker-compose up -d                      Start all services in background
docker-compose down                       Stop all services
docker-compose down -v                    Stop and delete volumes (reset DB)
docker-compose logs -f                    View live logs
docker-compose logs backend               View only backend logs
docker-compose restart                    Restart all services
docker-compose ps                         Check service status
docker-compose exec backend bash          Open shell in backend container
docker-compose exec postgres psql -U postgres  Open PostgreSQL shell
```

NPM Commands (Backend)

```bash
npm run dev                               Start development with hot reload
npm run build                             Build TypeScript to JavaScript
npm start                                 Start production server
npm run migrate                           Run database migrations
npm run migrate:reset                     Reset and rerun migrations
npm run test                              Run tests
npm run lint                              Run ESLint
npm run format                            Format code with Prettier
```

NPM Commands (Dashboard)

```bash
npm run dev                               Start Vite dev server
npm run build                             Build for production
npm run preview                           Preview production build
npm run lint                              Run ESLint
npm run type-check                        Run TypeScript type checking
```

Database Commands

```bash
psql -U postgres -d errorbase             Connect to database
\dt                                       List all tables
\d table_name                             Describe table schema
SELECT * FROM users;                      Query users
pg_dump -U postgres errorbase > backup.sql    Backup database
psql -U postgres errorbase < backup.sql       Restore database
```

---

STEP BY STEP TUTORIAL

Complete Setup Guide

```bash
# Step 1: Clone the repository
git clone https://github.com/ERROR0101r/errorbase.git
cd errorbase

# Step 2: Copy environment configuration
cp .env.example .env

# Step 3: Edit .env with your values
# - Change DB_PASSWORD to a strong password
# - Generate and set JWT_SECRET
# - Set CORS_ORIGIN to your dashboard URL
nano .env

# Step 4: Start with Docker
docker-compose up -d

# Step 5: Wait for services to be ready (about 30 seconds)
docker-compose ps

# Step 6: Create your first user
curl -X POST http://localhost:3000/auth/v1/signup \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@errorbase.com","password":"AdminPass123!"}'

# Step 7: Login to get your session
curl -X POST http://localhost:3000/auth/v1/signin \
  -H "Content-Type: application/json" \
  -c cookies.txt \
  -d '{"email":"admin@errorbase.com","password":"AdminPass123!"}'

# Step 8: Create a test table
curl -X POST http://localhost:3000/api/rest/v1/todos \
  -H "Content-Type: application/json" \
  -b cookies.txt \
  -d '{"title":"Learn ErrorBase","completed":false}'

# Step 9: Query your data
curl "http://localhost:3000/api/rest/v1/todos?select=id,title,completed" -b cookies.txt

# Step 10: Open the dashboard
# Open http://localhost:5173 in your browser

# Step 11: Upload a file
curl -X PUT http://localhost:3000/storage/v1/bucket/files/upload \
  -F "file=@test.jpg" \
  -b cookies.txt
```

Example Application Flow

```javascript
// Frontend React example
import { useEffect, useState } from 'react';

function App() {
  const [todos, setTodos] = useState([]);
  const [ws, setWs] = useState(null);

  // Fetch todos via REST API
  useEffect(() => {
    fetch('http://localhost:3000/api/rest/v1/todos?select=id,title,completed')
      .then(res => res.json())
      .then(setTodos);
  }, []);

  // Connect to WebSocket for realtime updates
  useEffect(() => {
    const socket = new WebSocket('ws://localhost:3000/realtime/v1/websocket');
    
    socket.onopen = () => {
      socket.send(JSON.stringify({
        type: 'subscribe',
        table: 'todos',
        event: '*'
      }));
    };
    
    socket.onmessage = (event) => {
      const data = JSON.parse(event.data);
      if (data.type === 'insert') {
        setTodos(prev => [...prev, data.record]);
      }
    };
    
    setWs(socket);
    return () => socket.close();
  }, []);

  // Add new todo
  const addTodo = async (title) => {
    await fetch('http://localhost:3000/api/rest/v1/todos', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ title, completed: false })
    });
  };

  return (
    <div>
      <h1>My Todos</h1>
      <input onKeyPress={(e) => e.key === 'Enter' && addTodo(e.target.value)} />
      {todos.map(todo => (
        <div key={todo.id}>{todo.title}</div>
      ))}
    </div>
  );
}
```

---

REPORT BUGS

```
If you find any bug, issue, or problem:

1. Check the logs: docker-compose logs backend
2. Check if PostgreSQL is running: docker-compose exec postgres pg_isready
3. Check if ports are available: netstat -tulpn | grep -E '3000|5432|5173'
4. Verify your .env configuration
5. Contact developer with:
   - Error message
   - Steps to reproduce
   - Log output
   - OS and Docker version

Your reports help improve ErrorBase!
```

---

DEVELOPER CONTACT

<div align="center">
  <p><strong>Name:</strong> ERROR0101risback / Fahad</p>
  <p>
    <a href="https://t.me/ERROR0101risback">Telegram</a> •
    <a href="https://instagram.com/fahad0101r">Instagram</a> •
    <a href="https://github.com/ERROR0101r">GitHub</a>
  </p>
</div>

---

REPOSITORY

· GitHub: https://github.com/ERROR0101r/errorbase
· Download ZIP: https://github.com/ERROR0101r/errorbase/archive/refs/heads/main.zip
· Issues: https://github.com/ERROR0101r/errorbase/issues

---

LICENSE

```
MIT License

Copyright (c) 2026 ERROR0101risback

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

<div align="center">
  <h3>🚀 One Deployment. Full Backend. Complete Control. 🚀</h3>
  <p><i>Made with ❤️ in Kashmir by @ERROR0101risback</i></p>

  <p>
    <a href="https://t.me/ERROR0101risback">Telegram</a> •
    <a href="https://instagram.com/fahad0101r">Instagram</a> •
    <a href="https://github.com/ERROR0101r">GitHub</a>
  </p>

  <p>© 2026 ErrorBase | Version 1.0.0 Stable</p>
  <p>Self-Hosted Firebase Alternative | PostgreSQL | REST API | Realtime | Storage</p>
</div>