# Changelog

All notable changes to VerifyIn will be documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [1.0.0] — 2024-03-15

### Initial open source release

#### Added
- Visitor pre-registration form with ID photo upload
- Host approval workflow via SMS (Africa's Talking) and email (SendGrid)
- QR code generation — embedded in approval SMS and email
- Security guard mobile console with QR/ID search and check-in/out
- Admin dashboard with live stats, venue breakdown, and CSV/JSON export
- JWT-based authentication with role system (visitor, host, security, admin)
- Cloudinary integration for secure ID photo storage
- Docker Compose deployment with PostgreSQL, Redis, Nginx, and Let's Encrypt SSL
- PWA manifest + service worker — installable as a mobile app
- One-click `setup.sh` deployment script
- Full audit log (every approval, check-in, check-out recorded)
- Multi-venue support (offices, apartments, gated communities)
- GitHub Actions CI pipeline
- MIT License

---

## Upcoming

See [Roadmap in README.md](README.md#roadmap) for planned features.
