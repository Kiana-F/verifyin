<div align="center">

<img src="https://img.shields.io/badge/VerifyIn-Visitor%20Management-1e3a5f?style=for-the-badge&logo=shield&logoColor=white" alt="VerifyIn"/>

# VerifyIn — Open Source Visitor Management System

**VerifyIn is a free, self-hostable visitor verification system for offices, apartments, and gated communities.**  
Built for Africa. Works everywhere.

[![MIT License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-20+-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://reactjs.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?style=flat-square&logo=postgresql&logoColor=white)](https://postgresql.org)
[![Docker](https://img.shields.io/badge/Docker-ready-2496ED?style=flat-square&logo=docker&logoColor=white)](https://docker.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)

[Live Demo](#demo) · [Quick Start](#quick-start) · [Features](#features) · [Contributing](CONTRIBUTING.md) · [Support the project](#support-the-project)

---

<img src="docs/screenshot.png" alt="VerifyIn screenshot" width="700"/>

</div>

---

## What is VerifyIn?

VerifyIn is a **free and open source** visitor management system that replaces paper sign-in books and manual gate logs. It lets anyone pre-register a visit, get approved by their host, receive a QR code, and check in with security — all without any manual paperwork.

Built for office buildings, residential apartments, and gated communities across Africa and beyond.

---

## Features

- **Visitor pre-registration** — visitors fill in their details online before arriving
- **Host approval workflow** — hosts get instant SMS + email notifications and approve or deny with one tap
- **QR code check-in** — approved visitors receive a QR code; security scans it at the gate
- **ID photo upload** — visitors upload their ID; security guards verify on arrival
- **Security guard console** — mobile-optimised dashboard for checking visitors in and out
- **Admin dashboard** — live stats, venue breakdown, full visit history
- **CSV / JSON export** — export visitor reports for any date range or venue
- **Multi-venue support** — one system for offices, apartments, and gated communities
- **SMS via Africa's Talking** — works on any phone, no app required
- **PWA** — security guards can install it as a native-feeling mobile app
- **Self-hostable** — run it on your own server with one command

---

## Tech stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite + React Router |
| Backend | Node.js + Express |
| Database | PostgreSQL 16 |
| Cache | Redis |
| File storage | Cloudinary |
| SMS | Africa's Talking |
| Email | SendGrid |
| Deployment | Docker + Nginx + Let's Encrypt |

---

## Quick start

### Prerequisites
- Docker + Docker Compose
- A PayPal, Stripe, or M-Pesa account (for the demo — not required for local dev)

### 1. Clone the repo

```bash
git clone https://github.com/Kiana-F/verifyin.git
cd verifyin
```

### 2. Set up environment variables

```bash
cp .env.example .env
# Edit .env — add your Africa's Talking, SendGrid, and Cloudinary keys
```

### 3. Start everything

```bash
bash setup.sh
```

The setup script will:
- Build all Docker images
- Start PostgreSQL, Redis, the API, and the frontend
- Run database migrations automatically
- Create a default admin account

### 4. Open the app

| URL | What it is |
|-----|-----------|
| `http://localhost` | Visitor registration form |
| `http://localhost/login` | Staff login |
| `http://localhost/admin` | Admin dashboard |

Default admin: `admin@verifyin.local` / `admin123` — **change this immediately.**

### Local development (without Docker)

```bash
# Backend
cd verifyin-backend
npm install
npm run migrate
npm run dev        # runs on :3000

# Frontend (separate terminal)
cd verifyin-frontend
npm install
npm run dev        # runs on :5173
```

---

## Project structure

```
verifyin/
├── verifyin-backend/          # Node.js + Express API
│   ├── src/
│   │   ├── routes/            # visitors, auth, admin, upload
│   │   ├── services/          # notifications (SMS + email), QR code
│   │   ├── middleware/        # JWT auth, role checks
│   │   └── models/            # PostgreSQL migrations
│   └── package.json
│
├── verifyin-frontend/         # React app
│   ├── src/
│   │   ├── pages/             # VisitorForm, HostDash, SecurityDash, AdminDash
│   │   ├── components/        # Navbar, ProtectedRoute
│   │   ├── context/           # AuthContext (JWT)
│   │   └── services/          # Axios API client
│   └── package.json
│
├── docker-compose.yml         # Full stack deployment
├── nginx/nginx.conf           # Reverse proxy + SSL
├── setup.sh                   # One-click setup script
└── .env.example               # Environment variable template
```

---

## API reference

All endpoints are documented in [`docs/API.md`](docs/API.md).

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/visitors` | Register a visit | Public |
| GET | `/api/visitors/:visitId` | Look up a visit | Public |
| PATCH | `/api/visitors/:id/approve` | Approve visit | Host / Admin |
| PATCH | `/api/visitors/:id/deny` | Deny visit | Host / Admin |
| PATCH | `/api/visitors/:id/checkin` | Check in visitor | Security / Admin |
| PATCH | `/api/visitors/:id/checkout` | Check out visitor | Security / Admin |
| GET | `/api/admin/stats` | Dashboard stats | Admin |
| GET | `/api/admin/export` | Export CSV / JSON | Admin |

---

## Deployment

See [`DEPLOY.md`](DEPLOY.md) for full instructions including:
- Docker Compose (recommended)
- SSL with Let's Encrypt (free)
- Installing as a PWA on mobile
- Database backup strategy
- Recommended hosting providers (Hetzner, DigitalOcean, AWS Lightsail Nairobi)

---

## Contributing

Contributions are very welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a PR.

Some good first issues to start with:
- [ ] Dark/light mode toggle
- [ ] Multi-language support (Swahili, French)
- [ ] M-Pesa payment verification integration
- [ ] Bulk visitor import from CSV
- [ ] Recurring visitor whitelist
- [ ] Webhook support for custom integrations

---

## Support the project

VerifyIn is free and open source. If it saves you time or helps your business, consider buying me a coffee ☕

<div align="center">

[![Support via PayPal](https://img.shields.io/badge/Support%20via-PayPal-003087?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/YOUR_PAYPAL_USERNAME)

**[paypal.me/YOUR_PAYPAL_USERNAME](https://paypal.me/YOUR_PAYPAL_USERNAME)**

Every contribution — big or small — helps keep this project alive and maintained. Thank you!

</div>

---

## Roadmap

- [x] Visitor pre-registration
- [x] Host approval via SMS + email
- [x] QR code check-in
- [x] ID photo upload + verification
- [x] Security guard mobile console
- [x] Admin dashboard + CSV export
- [x] Docker deployment
- [x] PWA support
- [ ] M-Pesa integration
- [ ] Swahili language support
- [ ] Mobile app (React Native)
- [ ] Webhook integrations
- [ ] Multi-tenant SaaS mode
- [ ] Analytics & reports

---

## License

MIT © [Kiana-F](https://github.com/Kiana-F)

Free to use, modify, and distribute. See [LICENSE](LICENSE) for details.
