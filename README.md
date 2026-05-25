# 🚀 TeamPulse — Team Analytics Dashboard

A full-featured Next.js 14 analytics dashboard with JWT auth, Redux Toolkit, and json-server mock API.

---

## ✨ Features

### Authentication
- JWT-based login & signup with **HTTP-only cookie** storage
- **Next.js Middleware** for route protection (protected `/dashboard/*`)
- Auto-redirect: authenticated users → dashboard, unauthenticated → login
- Token verification on every protected request

### Employee Management
- Full CRUD: Create, Read, Update, Delete employees
- **Debounced search** (450ms) by employee name
- **Server-side filters**: department, status
- **Pagination** with page controls
- **Zod validation** on all form fields
- Modal-based edit/add forms with proper error display

### Analytics & Charts (Recharts)
- Revenue vs Expenses vs Profit — Area chart (full year)
- User Growth Trend — Line chart
- Acquisition vs Churn — Bar chart
- Department Headcount — Pie/Donut chart
- Performance Distribution — Progress bars
- Stat cards on overview page

### Tech Stack
- **Next.js 14** (App Router, Server Components)
- **Redux Toolkit** — global state (auth, employees, analytics)
- **React Hook Form + Zod** — form validation
- **json-server** — mock REST API with pagination headers
- **Axios** — API client with JWT interceptors
- **Recharts** — all charts
- **jose** — JWT sign/verify (Edge-compatible)
- **TypeScript** throughout

---

## 📁 Project Structure

```
src/
├── app/
│   ├── api/auth/          # Next.js API Routes (login, signup)
│   ├── auth/login/        # Login page
│   ├── auth/signup/       # Signup page
│   └── dashboard/
│       ├── layout.tsx     # Sidebar layout (protected)
│       ├── page.tsx       # Overview with stat cards + mini charts
│       ├── employees/     # Employee listing + CRUD
│       └── analytics/     # Full analytics page
├── components/
│   ├── ReduxProvider.tsx  # Client-side Redux setup
│   └── employees/
│       └── EmployeeModal.tsx  # Edit/Add modal
├── hooks/
│   └── useDebounce.ts     # Custom debounce hook
├── lib/
│   ├── jwt.ts             # JWT sign/verify (jose)
│   └── apiClient.ts       # Axios instance with interceptors
├── store/
│   ├── index.ts           # configureStore + typed hooks
│   └── slices/
│       ├── authSlice.ts   # Auth state + thunks
│       ├── employeeSlice.ts  # Employee CRUD + filters
│       └── analyticsSlice.ts # Charts data
├── types/
│   └── index.ts           # All TypeScript interfaces
└── middleware.ts           # JWT route protection (Edge Runtime)
```

---

## 🏁 Getting Started

### 1. Install dependencies
```bash
npm install
```

### 2. Run json-server (mock API) + Next.js dev in parallel
```bash
npm run dev:full
```

Or separately:
```bash
# Terminal 1 — json-server on :3001
npm run server

# Terminal 2 — Next.js on :3000
npm run dev
```

### 3. Open the app
```
http://localhost:3000
```

### 4. Demo credentials
```
Email:    admin@techcorp.in
Password: Admin@123
```

---

## 🔐 JWT Flow

1. **Login/Signup** → POST `/api/auth/login` (Next.js API route)
2. API route validates credentials against json-server `/users`
3. Signs a JWT with `jose` (Edge-compatible), returns `{ token, user }`
4. Redux stores token in state + `js-cookie` sets `auth_token` cookie
5. **Next.js Middleware** intercepts every `/dashboard/*` request, verifies JWT
6. Axios interceptor attaches `Bearer token` to all API calls
7. **Logout** clears cookie + Redux state, redirects to login

---

## 📊 Mock Data (db.json)

- 15 employees across Engineering, Product, Design, Analytics, Marketing, Sales, HR
- 12 months of revenue/expenses/profit data
- 12 months of user growth/churn data
- 1 admin user (add more via signup)

json-server supports pagination via `?_page=1&_limit=8` and filtering via `?department=Engineering`.

---

## 🎨 Design

- **Dark theme** with CSS variables throughout
- **Syne** (display) + **DM Sans** (body) fonts
- Glass morphism cards with border glow
- Smooth animations and skeleton loaders
- Fully responsive layout (mobile: sidebar hidden)

---

## 🗂 Key Interview Points

| Feature | Implementation |
|---|---|
| Auth | JWT via jose, stored in cookie, Next.js middleware |
| Protected routes | `middleware.ts` — verifyToken on every request |
| State management | Redux Toolkit with typed hooks |
| Async actions | `createAsyncThunk` for all API calls |
| Form validation | react-hook-form + Zod schemas |
| Debounce | Custom `useDebounce` hook, 450ms |
| Pagination | Server-side via json-server `_page/_limit` |
| Filters | Controlled in Redux, refetch on change |
| Charts | Recharts — Area, Bar, Line, Pie |
