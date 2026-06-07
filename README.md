#ERRORBASE

The Self-Hosted Firebase Alternative | Complete Backend Platform

<div align="center">
  <img src="https://img.shields.io/badge/Status-Production_Ready-00C853?style=for-the-badge&logo=checkmark">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows%20%7C%20Mac-0078D4?style=for-the-badge&logo=windows">
  <img src="https://img.shields.io/badge/Backend-Node.js%20%7C%20TypeScript-339933?style=for-the-badge&logo=nodedotjs">
  <img src="https://img.shields.io/badge/Database-PostgreSQL-4169E1?style=for-the-badge&logo=postgresql">
  <img src="https://img.shields.io/badge/Frontend-React%20%7C%20Tailwind-61DAFB?style=for-the-badge&logo=react">
  <img src="https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker">

https://img.shields.io/badge/Telegram-@ERROR0101risback-26A5E4?style=for-the-badge&logo=telegram
https://img.shields.io/badge/GitHub-ERROR0101r-181717?style=for-the-badge&logo=github

  <p><strong>Developer: @ERROR0101risback</strong></p>
  <p><em>Version: 1.0.0 | Production Ready</em></p>
</div>

---

📋 TABLE OF CONTENTS

· Why ErrorBase?
· Features
· Quick Setup
· Tech Stack
· Project Structure
· Configuration Guide
· Docker Deployment
· API Endpoints
· Dashboard Guide
· Security Features
· Row Level Security
· Environment Variables
· Commands List
· Step by Step Tutorial
· Report Bugs
· Developer Contact
· License

---

WHY ERRORBASE?

```
⚠️ THE PROBLEM WITH FIREBASE / SUPA BASE CLOUD ⚠️

When you use cloud backend services:
• Your data lives on SOMEONE ELSE'S servers
• You pay for EVERY API request and EVERY GB of storage
• Your app can be rate-limited or banned without warning
• Your user data can be mined for AI training
• Vendor lock-in makes migration nearly impossible
• You have ZERO control over security patches
• Offline or air-gapped deployment is IMPOSSIBLE

✅ HOW ERRORBASE SOLVES THIS

With ErrorBase (Self-Hosted):
✓ Your data stays on YOUR infrastructure
✓ Pay ZERO dollars for API calls and storage
✓ Complete control over rate limits and quotas
✓ No third-party access to user data ever
✓ Full PostgreSQL access and backups
✓ Works offline, air-gapped, or on-premise
✓ You control security updates
✓ No vendor lock-in - it's just PostgreSQL
✓ Deploy on any VPS, dedicated server, or Raspberry Pi
```

Feature Firebase Supabase Cloud ErrorBase
Self-Hosted ❌ ⚠️ Limited ✅ Free
Data Ownership ❌ ❌ ✅ 100% Yours
Cost for 100K requests $0.60 $0.25 $0.00
Cost for 100GB storage $15.00 $20.00 $0.00
Vendor Lock-in ❌ Yes ⚠️ Partial ✅ No
Offline Capable ❌ No ⚠️ Limited ✅ Yes
Row Level Security ❌ No ✅ Yes ✅ Yes
Custom SQL ❌ No ✅ Yes ✅ Yes
Local Development ⚠️ Emulator ⚠️ Limited ✅ Full
GDPR Compliance ⚠️ Complex ⚠️ Complex ✅ Simple

---

FEATURES

Category Features
🗄️ Database PostgreSQL connection pool, Schema reflection, Auto-migrations, Row-Level Security (RLS), Foreign key relationships
📡 Auto-Generated REST API Dynamic endpoints for any table, Filtering (eq, ne, gt, lt, like, in), Pagination (limit/offset), Field selection, Stored procedure calls
🔐 Authentication System Email/Password signup, JWT with refresh tokens, Password reset flow, Rate limiting (5 attempts/minute), HTTP-only cookies, bcrypt hashing (10+ rounds)
⚡ Realtime Subscriptions WebSocket connections, Presence channels, Broadcast messages, Postgres CDC (INSERT/UPDATE/DELETE)
📁 File Storage S3-compatible API, Bucket management, File upload/download, MIME type validation, 50MB default limit, Delete operations
🖥️ Admin Dashboard Table browser with CRUD, SQL editor with syntax highlighting, User management, API logs and metrics, Storage browser, Dark/Light theme toggle
🛡️ Security Helmet.js security headers, CORS protection, Input sanitization, CSRF protection, Rate limiting per IP, Request/response logging

---

QUICK SETUP

One Command Setup:

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
```

Services Running:

Service URL Description
Dashboard http://localhost:5173 React admin interface
API Server http://localhost:3000 REST + WebSocket
PostgreSQL localhost:5432 Database
pgAdmin http://localhost:5050 Database management

Manual Setup (Without Docker):

Backend:

```bash
cd server
cp .env.example .env
# Edit .env with your database credentials
npm install
npm run migrate
npm run dev
```

Dashboard:

```bash
cd dashboard
npm install
npm run dev
```

---

TECH STACK

```
ERRORBASE TECH STACK
│
├── Backend Server
│   ├── Runtime: Node.js (v20+)
│   ├── Language: TypeScript (v5+)
│   ├── Framework: Express (v4)
│   ├── Database Driver: pg (v8+)
│   ├── Authentication: jsonwebtoken, bcrypt
│   ├── Realtime: Socket.io (v4)
│   ├── File Upload: Multer
│   ├── Logging: Winston
│   └── Security: Helmet, cors, express-rate-limit
│
├── Frontend Dashboard
│   ├── Framework: React (v18)
│   ├── Language: TypeScript
│   ├── Styling: TailwindCSS
│   ├── Components: Shadcn/ui
│   ├── State: TanStack Query
│   ├── HTTP Client: Axios
│   ├── Build Tool: Vite
│   └── Code Editor: Monaco Editor
│
├── Database
│   ├── Primary: PostgreSQL 15
│   ├── Management: pgAdmin 4
│   └── Migration: Custom migration system
│
└── Infrastructure
    ├── Container: Docker + Docker Compose
    ├── Proxy: Nginx (production)
    └── SSL: Let's Encrypt (optional)
```

---

PROJECT STRUCTURE

```
errorbase/
│
├── server/                              # Backend API Server
│   ├── src/
│   │   ├── config/
│   │   │   ├── database.ts             # PostgreSQL connection pool
│   │   │   ├── jwt.ts                  # JWT configuration
│   │   │   └── env.ts                  # Environment variables
│   │   │
│   │   ├── controllers/
│   │   │   ├── auth.controller.ts      # Signup, login, refresh
│   │   │   ├── rest.controller.ts      # Dynamic table endpoints
│   │   │   ├── storage.controller.ts   # File upload/download
│   │   │   └── realtime.controller.ts  # WebSocket handlers
│   │   │
│   │   ├── middleware/
│   │   │   ├── auth.middleware.ts      # JWT verification
│   │   │   ├── rls.middleware.ts       # Row Level Security
│   │   │   ├── rate-limit.ts           # Rate limiting
│   │   │   └── validation.ts           # Input validation
│   │   │
│   │   ├── models/
│   │   │   ├── user.model.ts           # User schema
│   │   │   └── session.model.ts        # Session management
│   │   │
│   │   ├── routes/
│   │   │   ├── auth.routes.ts          # /auth/v1/*
│   │   │   ├── rest.routes.ts          # /api/rest/v1/*
│   │   │   ├── storage.routes.ts       # /storage/v1/*
│   │   │   └── realtime.routes.ts      # WebSocket endpoint
│   │   │
│   │   ├── services/
│   │   │   ├── db.service.ts           # Schema reflection
│   │   │   ├── auth.service.ts         # Authentication logic
│   │   │   ├── storage.service.ts      # File operations
│   │   │   └── realtime.service.ts     # WebSocket pub/sub
│   │   │
│   │   ├── utils/
│   │   │   ├── logger.ts               # Winston logging
│   │   │   └── helpers.ts              # Utility functions
│   │   │
│   │   └── index.ts                    # Application entry point
│   │
│   ├── package.json
│   ├── tsconfig.json
│   └── .env.example
│
├── dashboard/                           # Frontend Admin Dashboard
│   ├── src/
│   │   ├── components/
│   │   │   ├── TableBrowser.tsx        # CRUD table interface
│   │   │   ├── SQLEditor.tsx           # Monaco SQL editor
│   │   │   ├── StorageBrowser.tsx      # File manager
│   │   │   ├── UserManager.tsx         # Auth user management
│   │   │   ├── LogViewer.tsx           # API logs viewer
│   │   │   └── Layout.tsx              # Sidebar + header
│   │   │
│   │   ├── pages/
│   │   │   ├── Dashboard.tsx           # Overview + metrics
│   │   │   ├── Tables.tsx              # Table browser page
│   │   │   ├── SQL.tsx                 # SQL editor page
│   │   │   ├── Auth.tsx                # Users management
│   │   │   ├── Storage.tsx             # Storage management
│   │   │   ├── Logs.tsx                # API logs page
│   │   │   └── Settings.tsx            # Project settings
│   │   │
│   │   ├── hooks/
│   │   │   ├── useAuth.ts              # Authentication hook
│   │   │   ├── useTables.ts            # Table data hook
│   │   │   └── useRealtime.ts          # WebSocket hook
│   │   │
│   │   ├── lib/
│   │   │   ├── api.ts                  # Axios client
│   │   │   └── utils.ts                # Helper functions
│   │   │
│   │   ├── App.tsx                     # Router + theme
│   │   └── main.tsx                    # Entry point
│   │
│   ├── package.json
│   └── vite.config.ts
│
├── docker-compose.yml                   # Complete stack
├── docker-compose.prod.yml              # Production setup
├── .env.example                         # Environment template
├── schema.sql                           # Initial database schema
├── openapi.yaml                         # API documentation
└── README.md                            # This file
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

Development Environment:

```yaml
# docker-compose.yml
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

Production Deployment:

```bash
# Build and start production stack
docker-compose -f docker-compose.prod.yml up -d

# With SSL/TLS (using nginx as reverse proxy)
docker-compose -f docker-compose.ssl.yml up -d

# Scale backend instances
docker-compose up -d --scale backend=3

# Backup database
docker exec errorbase-postgres pg_dump -U postgres errorbase > backup.sql

# Restore database
cat backup.sql | docker exec -i errorbase-postgres psql -U postgres errorbase
```

---

API ENDPOINTS

🗄️ Auto-Generated REST API

Method Endpoint Description Auth
GET /api/rest/v1/{table} List records with filters Optional
GET /api/rest/v1/{table}/{id} Get single record Optional
POST /api/rest/v1/{table} Insert record Optional
PATCH /api/rest/v1/{table} Update record(s) Optional
DELETE /api/rest/v1/{table} Delete record(s) Optional
GET /api/rest/v1/rpc/{function} Call stored procedure Optional

Query Parameters:

```
GET /api/rest/v1/users?select=id,email,name&order=created_at.desc&limit=10&offset=20

# Filters
?column=eq.value      # Equal to
?column=ne.value      # Not equal to
?column=gt.value      # Greater than
?column=lt.value      # Less than
?column=gte.value     # Greater than or equal
?column=lte.value     # Less than or equal
?column=like.*value*  # Contains pattern
?column=ilike.*value* # Case-insensitive contains
?column=in.1,2,3      # In array
?column=is.null       # Is NULL
?column=is.not.null   # Is NOT NULL
```

Examples:

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

🔐 Authentication API

Method Endpoint Description
POST /auth/v1/signup Register new user
POST /auth/v1/signin Login (returns JWT cookie)
GET /auth/v1/user Get current user profile
POST /auth/v1/refresh Refresh JWT token
POST /auth/v1/logout Logout user
POST /auth/v1/reset-password Request password reset
POST /auth/v1/update-password Update password with token

Examples:

```bash
# Signup
curl -X POST http://localhost:3000/auth/v1/signup \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "SecurePass123!",
    "metadata": {"name": "John Doe"}
  }'

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

📁 Storage API

Method Endpoint Description
POST /storage/v1/bucket Create new bucket
GET /storage/v1/bucket List all buckets
DELETE /storage/v1/bucket/{name} Delete empty bucket
GET /storage/v1/bucket/{name}/list List objects in bucket
PUT /storage/v1/bucket/{name}/upload Upload file
GET /storage/v1/bucket/{name}/download/{path} Download file
DELETE /storage/v1/bucket/{name}/delete/{path} Delete file
POST /storage/v1/bucket/{name}/move Move/copy file

Examples:

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

⚡ Realtime WebSocket

```javascript
// Connect to WebSocket
const ws = new WebSocket('ws://localhost:3000/realtime/v1/websocket');

// Authentication (send JWT after connect)
ws.on('open', () => {
  ws.send(JSON.stringify({
    type: 'auth',
    token: 'your-jwt-token'
  }));
});

// Subscribe to table changes
ws.send(JSON.stringify({
  type: 'subscribe',
  channel: 'users_changes',
  table: 'users',
  event: '*'  // INSERT, UPDATE, DELETE, or *
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
  payload: { text: 'Hello everyone!', user: 'John' }
}));

// Listen for messages
ws.onmessage = (event) => {
  const data = JSON.parse(event.data);
  console.log('Received:', data);
  
  if (data.type === 'insert') {
    console.log('New record:', data.record);
  }
};

// Unsubscribe
ws.send(JSON.stringify({
  type: 'unsubscribe',
  channel: 'users_changes'
}));
```

---

DASHBOARD GUIDE

Pages Overview:

Page Route Functionality
Overview / API keys, project URL, system metrics, recent activity
Table Browser /tables Browse any table, CRUD operations, filter/sort/paginate
SQL Editor /sql Run custom SQL with syntax highlighting, save queries, export results
Auth Users /auth View/manage users, reset passwords, assign roles
Storage /storage Browse buckets, upload/download files, manage folders
API Logs /logs View request/response logs, filter by status/endpoint
Settings /settings Configure CORS, API keys, rate limits, theme

Dashboard Features:

```javascript
// Table Browser - CRUD Operations
- View any table with pagination
- Click "Add Record" to insert
- Double-click cell to edit
- Click "Delete" row to remove
- Filter columns with search
- Sort by any column
- Export to CSV/JSON

// SQL Editor
- Monaco editor with syntax highlighting
- Run SELECT, INSERT, UPDATE, DELETE
- Save frequently used queries
- Export query results
- View query execution time

// Storage Browser
- Drag & drop file upload
- Create/delete folders
- Preview images
- Generate signed URLs
- Set file as public/private

// User Management
- View all registered users
- Reset user password
- Enable/disable accounts
- Assign admin role
- View login history
```

---

SECURITY FEATURES

```
┌─────────────────────────────────────────────────────────────────┐
│                      SECURITY ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Layer 1: Network Security                                      │
│  ├── HTTPS enforcement (production)                             │
│  ├── CORS with strict origin validation                         │
│  └── Docker network isolation                                   │
│                                                                  │
│  Layer 2: Authentication                                        │
│  ├── bcrypt password hashing (10+ rounds)                       │
│  ├── JWT stored in HTTP-only cookies                            │
│  ├── Refresh token rotation                                     │
│  └── Session invalidation on logout                             │
│                                                                  │
│  Layer 3: Request Security                                      │
│  ├── Rate limiting (100 req/min per IP)                         │
│  ├── Auth rate limiting (5 attempts/min)                        │
│  ├── Helmet.js security headers                                 │
│  └── Request size limits                                        │
│                                                                  │
│  Layer 4: Database Security                                     │
│  ├── Parameterized queries (no SQL injection)                   │
│  ├── Row Level Security (RLS) middleware                        │
│  ├── Connection pooling with limits                             │
│  └── Query timeout protection                                   │
│                                                                  │
│  Layer 5: File Security                                         │
│  ├── MIME type validation                                       │
│  ├── File size limits (50MB default)                            │
│  ├── Filename sanitization                                      │
│  └── Virus scanning (optional integration)                      │
│                                                                  │
│  Layer 6: Logging & Monitoring                                  │
│  ├── Winston request/response logging                           │
│  ├── Failed login tracking                                      │
│  ├── API usage metrics                                          │
│  └── Audit trails for admin actions                             │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

Row Level Security (RLS) Implementation:

```sql
-- RLS policies in PostgreSQL
CREATE POLICY user_own_data ON users
    USING (user_id = current_setting('app.current_user_id')::uuid);

CREATE POLICY admin_all_access ON users
    USING (current_setting('app.user_role') = 'admin');

CREATE POLICY team_members ON team_members
    USING (team_id IN (
        SELECT team_id FROM team_members 
        WHERE user_id = current_setting('app.current_user_id')::uuid
    ));
```

```typescript
// RLS Middleware (server/src/middleware/rls.middleware.ts)
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

Complete Reference:

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
STORAGE_TYPE=local  # local or s3
STORAGE_PATH=./uploads
MAX_FILE_SIZE=52428800  # 50MB in bytes
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
WS_MESSAGE_SIZE_LIMIT=1048576  # 1MB

# ==================== LOGGING ====================
LOG_LEVEL=info
LOG_DIR=./logs
LOG_MAX_FILES=30
LOG_MAX_SIZE=10485760  # 10MB

# ==================== EMAIL (for password reset) ====================
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password
SMTP_FROM=noreply@errorbase.com
EMAIL_RESET_URL=http://localhost:5173/reset-password

# ==================== ADMIN DASHBOARD ====================
ADMIN_API_KEY=change-this-admin-key
DASHBOARD_SESSION_TIMEOUT=3600000  # 1 hour

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

Docker Commands:

Command Description
docker-compose up -d Start all services in background
docker-compose down Stop all services
docker-compose down -v Stop and delete volumes (reset DB)
docker-compose logs -f View live logs
docker-compose logs backend View only backend logs
docker-compose restart Restart all services
docker-compose ps Check service status
docker-compose exec backend bash Open shell in backend container
docker-compose exec postgres psql -U postgres Open PostgreSQL shell

NPM Commands (Backend):

Command Description
npm run dev Start development with hot reload
npm run build Build TypeScript to JavaScript
npm start Start production server
npm run migrate Run database migrations
npm run migrate:reset Reset and rerun migrations
npm run test Run tests
npm run lint Run ESLint
npm run format Format code with Prettier

NPM Commands (Dashboard):

Command Description
npm run dev Start Vite dev server
npm run build Build for production
npm run preview Preview production build
npm run lint Run ESLint
npm run type-check Run TypeScript type checking

Database Commands:

Command Description
psql -U postgres -d errorbase Connect to database
\dt List all tables
\d table_name Describe table schema
SELECT * FROM users; Query users
pg_dump -U postgres errorbase > backup.sql Backup database
psql -U postgres errorbase < backup.sql Restore database

---

STEP BY STEP TUTORIAL

Complete Setup Guide:

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
# You should be automatically logged in from the cookie

# Step 11: Upload a file
curl -X PUT http://localhost:3000/storage/v1/bucket/files/upload \
  -F "file=@test.jpg" \
  -b cookies.txt

# Step 12: Test realtime (open two terminals)
# Terminal 1 - Listen for changes
# Terminal 2 - Insert data and watch Terminal 1 receive it
```

Example Application Flow:

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
    <a href="https://t.me/ERROR0101risback"><img src="https://img.shields.io/badge/Telegram-@ERROR0101risback-26A5E4?style=flat-square&logo=telegram"></a>
    <a href="https://instagram.com/fahad0101r"><img src="https://img.shields.io/badge/Instagram-@fahad0101r-E4405F?style=flat-square&logo=instagram"></a>
    <a href="https://github.com/ERROR0101r"><img src="https://img.shields.io/badge/GitHub-ERROR0101r-181717?style=flat-square&logo=github"></a>
  </p>

  <p>© 2026 ErrorBase | Version 1.0.0 Stable</p>
  <p>Self-Hosted Firebase Alternative | PostgreSQL | REST API | Realtime | Storage</p>
</div>