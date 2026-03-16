# Contributing to VerifyIn

First off — thank you for considering contributing! VerifyIn is built for everyone, and every contribution matters, whether it's fixing a typo, reporting a bug, or building a new feature.

---

## Ways to contribute

- **Report a bug** — open a GitHub issue using the Bug Report template
- **Suggest a feature** — open a GitHub issue using the Feature Request template
- **Fix a bug** — pick an open issue, comment that you're working on it, submit a PR
- **Add a feature** — discuss it in an issue first so we can align on approach
- **Improve documentation** — always needed!
- **Translate** — help translate VerifyIn into Swahili, French, or other languages
- **Share** — star the repo and tell others about it

---

## Getting started

### 1. Fork and clone

```bash
git clone https://github.com/YOUR_USERNAME/verifyin.git
cd verifyin
```

### 2. Create a branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

### 3. Set up local dev

```bash
# Backend
cd verifyin-backend
cp .env.example .env      # fill in your test credentials
npm install
npm run migrate
npm run dev

# Frontend (new terminal)
cd verifyin-frontend
npm install
npm run dev
```

### 4. Make your changes

Keep changes focused — one feature or fix per PR. This makes review much faster.

### 5. Test your changes

Before submitting:
- [ ] The backend starts without errors (`npm run dev`)
- [ ] The frontend builds without errors (`npm run build`)
- [ ] New API routes are tested with Postman or curl
- [ ] No existing functionality is broken

### 6. Commit with a clear message

```bash
git commit -m "feat: add recurring visitor whitelist"
git commit -m "fix: QR code not rendering on Safari"
git commit -m "docs: add M-Pesa setup instructions"
```

We use [Conventional Commits](https://www.conventionalcommits.org/):
- `feat:` — new feature
- `fix:` — bug fix
- `docs:` — documentation only
- `style:` — formatting, no logic change
- `refactor:` — code restructure, no feature change
- `chore:` — dependency updates, config

### 7. Open a pull request

- Fill in the PR template
- Reference the issue it closes (e.g. `Closes #42`)
- Add screenshots for UI changes

---

## Code style

**Backend (Node.js)**
- Use `async/await`, not callbacks
- Validate all input with `express-validator`
- Always handle errors in routes — no unhandled promises
- Keep route files focused — business logic goes in `services/`

**Frontend (React)**
- Functional components only
- Keep components small and focused
- Use the existing CSS variables — don't hardcode colours
- Toast notifications for all user actions (success/error)

---

## Areas that need help

These are open and actively wanted:

| Area | Description | Difficulty |
|------|-------------|------------|
| Swahili translation | i18n support, starting with Swahili | Medium |
| M-Pesa integration | Verify payments via Daraja API | Medium |
| Bulk CSV import | Import visitor lists from Excel/CSV | Easy |
| Recurring visitors | Whitelist frequent visitors | Medium |
| Webhook support | POST to custom URLs on status change | Medium |
| React Native app | Mobile app for security guards | Hard |
| Unit tests | Jest tests for API routes | Easy–Medium |
| Dark/light toggle | Theme switcher in the UI | Easy |

---

## Questions?

Open a [GitHub Discussion](https://github.com/Kiana-F/verifyin/discussions) or GitHub Discussions at https://github.com/Kiana-F/verifyin/discussions.

---

## Code of conduct

Be kind. We're all here to build something useful.  
See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) for the full version.
