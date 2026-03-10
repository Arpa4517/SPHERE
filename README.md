# SPHERE — Secure Patient Health Encrypted Record Environment

A cryptographically secure patient health record system built for Cryptography and Cryptanalysis course.
SPHERE is a full-stack web application that provides end-to-end encrypted storage and management of sensitive patient health records. All cryptographic algorithms — RSA, ECC, SHA-256, and HMAC — are implemented **from scratch** without relying on any built-in cryptographic libraries.

The system addresses a critical gap in modern healthcare IT: patient records stored in plaintext or with weak encryption are highly vulnerable to breaches. SPHERE enforces encryption at rest, multi-factor authentication, role-based access control, and tamper-proof data integrity verification.


## Features

### 🔐 Authentication & Security
- Custom JWT session management with configurable expiration
- Password hashing with SHA-256 + random 32-byte salt
- Constant-time password comparison (timing-attack resistant)
- Two-Factor Authentication (2FA) via Email OTP (5-minute expiry)
- Forgot password flow with email verification

### 🔒 Data Encryption
- **RSA-1024** encryption for personal data: username, email, name, contact number
- **ECC (secp256k1)** encryption for role-specific data: doctor specialization, patient age and sex
- **Multi-level encryption** combining RSA + ECC for confidential diagnosis notes
- All encrypted data stored as Base64-encoded text
- SHA-256 hash indexes maintained on encrypted fields for searchability without exposing plaintext

### 🛡️ Data Integrity
- HMAC-SHA256 Message Authentication Codes on all critical data operations
- MAC verification before every data modification
- Integrity checks performed during decryption

### 🏥 Medical Features
- Encrypted diagnosis records (symptoms, diagnosis text, prescriptions)
- Appointment booking and scheduling with status tracking (pending / confirmed / completed / cancelled)
- Role-specific dashboards for Admin, Doctor, and Patient

### 🧑‍💼 Role-Based Access Control
- **Admin**: full user management — view, deactivate, or delete any account
- **Doctor**: manage diagnoses, view and update appointment statuses
- **Patient**: view own records, book appointments, manage profile


## Tech Stack

### Backend
| Layer | Technology |
|-------|-----------|
| Language | Python |
| Framework | FastAPI |
| ORM | SQLAlchemy |
| Database | SQLite |
| Server | Uvicorn (ASGI) |
| Auth | Custom JWT |
| Email | SMTP (2FA & password reset) |
| Config | python-dotenv |

### Frontend
| Layer | Technology |
|-------|-----------|
| Language | TypeScript |
| Framework | React |
| Build Tool | Vite (dev server on port 5173) |
| Styling | Tailwind CSS |
| HTTP Client | Axios |
| State | React Hooks + Context API |

---

## User Roles

### 👤 Patient
- Register with personal details (RSA-encrypted at rest)
- Log in with email + password + 2FA OTP
- View and edit own profile
- Browse available doctors by specialization
- Book, view, and track appointments
- View own diagnosis history and prescriptions

### 🩺 Doctor
- Register with specialization (ECC-encrypted at rest)
- View booked appointments; confirm, complete, or cancel them
- Create encrypted diagnosis records for patients (symptoms, diagnosis, prescription, notes)
- View all diagnoses created by them

### 🔧 Admin
- Automatically assigned to the first registered user
- View all users with role and status filters
- Deactivate or delete any user account
- Full read access to platform-wide data

---

## Contribution
Role-based access control, 2FA, Data encryption/decryption, Profile view & edit, Frontend design



---

