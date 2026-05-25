# 🚀 TeamPulse — Team Analytics Dashboard

A modern **production-style analytics dashboard** built with **Next.js 14**, featuring secure JWT authentication, employee management, interactive analytics, and scalable frontend architecture.

Designed to simulate a real-world internal admin platform used by organizations to manage teams, monitor employee performance, and visualize business insights.

---

# 🌟 Features

## 🔐 Authentication & Authorization

- JWT-based authentication flow
- Secure route protection using **Next.js Middleware**
- Login & Signup forms with validation
- Persistent sessions using cookies
- Automatic redirects based on auth state
- Token verification on protected routes

---

## 👥 Employee Management

- Full CRUD operations
- Debounced employee search
- Department & status filters
- Server-side pagination
- Form validation with Zod
- Modal-based add/edit forms
- Dynamic performance tracking

---

## 📊 Analytics Dashboard

### Revenue Analytics
- Revenue vs Expenses tracking
- Profit monitoring
- Monthly business growth trends

### User Metrics
- Active users
- New user acquisition
- Churn analytics

### Team Insights
- Department-wise employee distribution
- Employee performance tracking
- Organization overview cards

---

## 🎨 UI / UX Highlights

- Fully responsive dashboard
- Modern dark-themed interface
- Glassmorphism design system
- Skeleton loaders
- Smooth animations
- Reusable component architecture
- Typography using **Syne** & **DM Sans**

---

# 🛠 Tech Stack

| Category | Technology |
|---|---|
| Framework | Next.js 14 |
| Language | TypeScript |
| Styling | Tailwind CSS + Custom CSS |
| State Management | Redux Toolkit |
| Forms | React Hook Form |
| Validation | Zod |
| Charts | Recharts |
| Authentication | JWT + jose |
| Mock Backend | json-server |
| API Client | Axios |
| Routing Protection | Middleware |

---

# 📁 Project Structure

```bash
src/
├── app/
│   ├── api/
│   │   └── auth/
│   │       ├── login/
│   │       └── signup/
│   │
│   ├── auth/
│   │   ├── login/
│   │   └── signup/
│   │
│   └── dashboard/
│       ├── analytics/
│       ├── employees/
│       ├── layout.tsx
│       └── page.tsx
│
├── components/
│   ├── employees/
│   └── ReduxProvider.tsx
│
├── hooks/
│   └── useDebounce.ts
│
├── lib/
│   ├── apiClient.ts
│   └── jwt.ts
│
├── store/
│   ├── index.ts
│   └── slices/
│       ├── authSlice.ts
│       ├── employeeSlice.ts
│       └── analyticsSlice.ts
│
├── types/
│   └── index.ts
│
└── middleware.ts
```

---

# 🏗 Architecture Explanation

The application follows a **feature-based scalable architecture** where logic is separated into dedicated modules.

---

## 🔄 Authentication Flow

```text
User Login
   ↓
Next.js API Route
   ↓
Credential Validation
   ↓
JWT Generation (jose)
   ↓
Cookie Storage
   ↓
Middleware Verification
   ↓
Protected Dashboard Access
```

### Why `jose`?

`jose` is Edge-runtime compatible, making it suitable for authentication inside Next.js Middleware.

---

## 🧠 State Management

Redux Toolkit handles:

- Authentication state
- Employee data
- Analytics data
- Pagination
- Filters
- Async loading states

Async operations are managed using:

```ts
createAsyncThunk()
```

---

## 📊 Data Visualization

Analytics are built using **Recharts**:

- Area Charts
- Bar Charts
- Line Charts
- Pie Charts
- Progress indicators

All charts are responsive and optimized for different screen sizes.

---

# ⚖️ Tradeoffs & Technical Decisions

| Decision | Reason | Tradeoff |
|---|---|---|
| json-server | Faster mock backend setup | No real persistence |
| Redux Toolkit | Better scalability | More boilerplate |
| JWT Cookie Auth | Simulates production auth | Middleware complexity |
| App Router | Modern Next.js architecture | Learning curve |
| Tailwind + Custom CSS | Faster UI development | Mixed styling system |

---

# 🚧 Challenges Faced

## 1. Middleware Authentication

Handling authentication with Next.js App Router required Edge-compatible JWT verification using:

```bash
jose
```

Traditional JWT libraries were not fully compatible with middleware runtime.

---

## 2. Managing Complex State

Handling:
- employee CRUD
- filters
- analytics
- pagination
- loading states

became difficult using local state alone, so Redux Toolkit was introduced.

---

## 3. Responsive Charts

Making charts responsive across mobile and tablet layouts required:
- ResponsiveContainer
- adaptive layouts
- custom tooltip handling

---

## 4. Debounced Search

To reduce unnecessary API calls while typing, a custom debounce hook was implemented.

---

# 🔐 Security Features

- Protected dashboard routes
- JWT verification middleware
- Form validation using Zod
- Secure token handling
- Axios request interceptors

---

# 🎨 Design System

The UI is built using reusable design utilities:

```css
:root {
  --bg-0: #080c18;
  --brand: #5b73ff;
  --accent: #00d4b4;
  --danger: #ff4d6d;
}
```

Features:
- glassmorphism cards
- consistent spacing system
- reusable buttons
- responsive grid layouts
- dark dashboard theme

---

# 📦 Setup Instructions

## 1️⃣ Clone Repository

```bash
git clone https://github.com/your-username/teampulse-dashboard.git
cd teampulse-dashboard
```

---

## 2️⃣ Install Dependencies

```bash
npm install
```

---

## 3️⃣ Run Development Servers

Run both Next.js and json-server together:

```bash
npm run dev:full
```

OR run separately:

### Terminal 1
```bash
npm run server
```

### Terminal 2
```bash
npm run dev
```

---

## 4️⃣ Open Application

```bash
http://localhost:3000
```

---

# 🔑 Demo Credentials

```bash
Email: admin@techcorp.in
Password: Admin@123
```

---

# 📈 Key Functionalities

| Feature | Implementation |
|---|---|
| Protected Routes | Next.js Middleware |
| Authentication | JWT + jose |
| Global State | Redux Toolkit |
| Async API Calls | createAsyncThunk |
| Form Validation | React Hook Form + Zod |
| API Communication | Axios |
| Debounced Search | Custom Hook |
| Charts | Recharts |
| Pagination | json-server |

---

# ⏱ Time Taken

| Module | Approx Time |
|---|---|
| Project Setup & Architecture | 3 hrs |
| Authentication System | 4 hrs |
| Employee CRUD | 5 hrs |
| Analytics Dashboard | 4 hrs |
| UI Design & Responsiveness | 5 hrs |
| Testing & Debugging | 2 hrs |

### Total Time:
# ~23 Hours

---

# 🚀 Future Improvements

- Role-based access control
- Real backend integration
- Unit & integration testing
- Exportable reports
- Real-time notifications
- Drag-and-drop widgets
- Theme switcher

---

# 📄 Submission Details


```

---

# 👨‍💻 Author

Built by **Ayush Thapliyal** using modern frontend engineering practices and scalable architecture principles.
