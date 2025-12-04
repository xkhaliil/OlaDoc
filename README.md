# OlaDoc
A comprehensive web application that connects patients with doctors for easy appointment booking, secure document exchange, and real-time video consultations.

1. Elements of the Project
Frontends

Patient Web App (Next.js)

Doctor Dashboard (Next.js)

Admin Panel (Next.js)

Backends

Core API (Next.js API Routes / Server Actions)

Background workers (notifications, reminders)

Data & Storage

MongoDB via Prisma (users, appointments, payments, documents, messages)

Cloud storage provider (patient files)

Optional Redis (cache + rate limiting)

External Providers

Authentication provider

Video call provider

Payment provider (Stripe / PayPal / similar)

Email/SMS provider
2. Architectural Patterns Applied

Modular Monolith inside Next.js for simplicity and maintainability

Event-driven async patterns for reminders, notifications, and payment webhooks

Real-time communication (via provider SDK) for chat & presence

Externalized services for auth, video calls, and payments

Edge-layer middleware (Vercel) for rate limiting and token validation

3. Communication Between Components
From	To	Method
Frontend → Core API	HTTPS (REST)	
API → Database	Prisma (TCP)	
Frontend → Auth Provider	OAuth / OIDC	
Frontend ↔ Video Provider	WebRTC + provider SDK	
Frontend → Payment Provider	Checkout redirect / payment widget	
Payment Provider → API	Webhooks (payment succeeded/failed)	
API → Email/SMS Provider	HTTPS	
API → Workers	Internal async queue	
4. Authentication & Authorization Needed
Authentication (AuthN)

Handled entirely by the external authentication provider:

User login & identity

Token issuance

Session management

API trusts validated tokens from the provider.

Authorization (AuthZ)

Role-based permissions inside the Core API:

Roles:

PATIENT

DOCTOR

ADMIN

Used to control access to:

appointments

medical documents

dashboards

prescriptions

payments

admin management features
