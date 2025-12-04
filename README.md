🩺 OlaDoc – Healthcare Appointment & Telemedicine Platform

OlaDoc is a modern healthcare platform that connects patients with doctors for appointments, secure document sharing, chat, video consultations, and online payments.
Built with Next.js, Prisma, MongoDB, and trusted external providers, OlaDoc enables a seamless and scalable telemedicine experience.

🚀 Features
👤 For Patients

Search doctors by specialty, location, or availability

Book, cancel, and manage appointments

Upload and store medical documents securely

Real-time chat with doctors

Video consultations via provider SDK

Online payments for consultations

🩺 For Doctors

Personal dashboard with full appointment calendar

Manage patient interactions

View and download patient documents

Accept video or chat consultations

🛠️ For Admins

Manage users, doctors, clinics

Verify medical professionals

View system analytics

Admin-level configuration access

🧩 System Elements
Frontends

Patient Web App (Next.js)

Doctor Dashboard (Next.js)

Admin Panel (Next.js)

Backends

Core API (Next.js API Routes / Server Actions)

Background workers (notifications, reminders)

Data & Storage

MongoDB + Prisma ORM

External cloud storage for document files

Optional Redis (caching, rate limiting)

External Providers

Authentication provider (OAuth/OIDC)

Video call provider (WebRTC SDK)

Payment provider (Stripe/PayPal/etc.)

Email/SMS notifications provider

🏗️ Architectural Patterns Applied

Modular Monolith inside Next.js for simplicity and maintainability

Event-driven async patterns for reminders, notifications, and payment webhooks

Real-time communication (via provider SDK) for chat & presence

Externalized services for auth, video calls, and payments

Edge-layer middleware (Vercel) for rate limiting and token validation

🔌 Communication Between Components
From	To	Method
Frontend → Core API	HTTPS (REST)	
API → Database	Prisma (TCP)	
Frontend → Auth Provider	OAuth / OIDC	
Frontend ↔ Video Provider	WebRTC + provider SDK	
Frontend → Payment Provider	Checkout redirect / payment widget	
Payment Provider → API	Webhooks (payment succeeded/failed)	
API → Email/SMS Provider	HTTPS	
API → Workers	Internal async queue	
🔐 Authentication & Authorization
Authentication (AuthN)

Handled entirely by an external authentication provider:

User login & identity

Token issuance

Session management

The API trusts validated tokens from the provider.

Authorization (AuthZ)

Role-based permissions enforced inside the API.

Roles:

PATIENT

DOCTOR

ADMIN

Used to control access to:

Appointments

Medical documents

Dashboards

Prescriptions

Payments

Admin management features

🗄️ Tech Stack

Frontend: Next.js 14, React, TailwindCSS
Backend: Next.js API Routes / Server Actions
Database: MongoDB + Prisma ORM
Integrations: Auth Provider, Video Provider, Payment Provider, Email/SMS Provider
Deployment: Vercel + GitHub CI/CD
