# 🩺 OlaDoc – Healthcare Appointment & Telemedicine Platform

OlaDoc is a modern healthcare platform that connects patients with doctors for appointments, secure document sharing, chat, video consultations, and online payments.
Built with Next.js, Prisma, MongoDB, and trusted external providers, OlaDoc offers a seamless telemedicine experience.

## 🚀 Features

### For Patients
- Search doctors by specialty, location, or availability
- Book, cancel, and manage appointments
- Securely upload medical documents
- Real-time chat with doctors
- Video consultations via provider SDK
- Online payments

### For Doctors
- Dashboard with full appointment calendar
- Manage patient interactions
- Access and download patient documents
- Chat and video consultations

### For Admins
- Manage users, doctors, and clinics
- Verify doctors
- System analytics and admin settings

---

## 🧩 System Elements

### Frontends
- Patient Web App (Next.js)
- Doctor Dashboard (Next.js)
- Admin Panel (Next.js)

### Backends
- Core API (Next.js API Routes / Server Actions)
- Background workers (notifications, reminders)

### Data & Storage
- MongoDB + Prisma ORM
- External cloud storage for files
- Optional Redis

### External Providers
- Authentication provider (OAuth/OIDC)
- Video call provider (WebRTC SDK)
- Payment provider
- Email/SMS provider

---

## 🏗 Architectural Patterns Applied

- Modular Monolith inside Next.js for simplicity and maintainability
- Event-driven async patterns for reminders, notifications, and payment webhooks
- Real-time communication (via provider SDK) for chat & presence
- Externalized services for auth, video calls, and payments
- Edge-layer middleware (Vercel) for rate limiting and token validation

---

## 🔌 Communication Between Components

| From                       | To                    | Method                               |
|----------------------------|------------------------|----------------------------------------|
| Frontend → Core API        | Core API               | HTTPS (REST)                           |
| Core API → Database        | MongoDB (Prisma ORM)   | TCP (via Prisma client)                |
| Frontend → Auth Provider   | Auth Provider          | OAuth / OIDC                           |
| Frontend ↔ Video Provider  | Video Provider         | WebRTC + Provider SDK                  |
| Frontend → Payment Provider| Payment Provider       | Checkout Redirect / Payment Widget     |
| Payment Provider → API     | Core API               | Webhooks (Payment success/failure)     |
| API → Email/SMS Provider   | Email/SMS Provider     | HTTPS                                   |
| API → Workers              | Background Workers     | Internal Async Queue / Event Trigger    |


---

## 🔐 Authentication & Authorization

### Authentication (AuthN)
Handled entirely by the external authentication provider:
- User login & identity
- Token issuance
- Session management
The API trusts validated tokens.

### Authorization (AuthZ)
Role-based permissions inside the API.

**Roles**
- PATIENT
- DOCTOR
- ADMIN

**Controls**
- appointments
- medical documents
- dashboards
- prescriptions
- payments
- admin features

---

## 🗄 Tech Stack

- Next.js 14
- React + TailwindCSS
- Prisma ORM
- MongoDB
- External Auth / Video / Payment / Email services
- Vercel Deployment + GitHub CI/CD
