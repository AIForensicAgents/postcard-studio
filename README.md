<!--
<meta property="og:title" content="🎨 Postcard Studio" />
<meta property="og:description" content="A beautiful Apple‑inspired web app for creating custom AI‑generated postcards in standard postal sizes — family-safe, passkey‑ready, versioned cloud storage, and a stunning card carousel." />
<meta property="og:image" content="https://your-domain.example/assets/og-postcard-studio.png" />
<meta property="og:type" content="website" />
<meta property="og:url" content="https://github.com/your-org/postcard-studio" />
<meta name="twitter:card" content="summary_large_image" />
-->

# 🎨 Postcard Studio

<!-- Badges (HTML img tags as requested) -->
<div>
  <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT" />
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" alt="PRs welcome" />
  <img src="https://img.shields.io/badge/made%20with-AI-blue.svg" alt="Made with AI" />
</div>

A beautiful, Apple‑inspired single‑page web application for creating custom AI‑generated postcards in standard postal sizes. Postcard Studio is designed for simplicity and safety: user authentication, versioned cloud storage, optional passkey security (WebAuthn), family‑safety AI screening, and a stunning card carousel interface for browsing and printing.

---

## Table of Contents
- Features
- Screenshot
- Tech Stack
- Getting started
- Usage Guide
- Security Features
- Deployment
- Contributing
- License
- Credits

---

## Screenshot
<img src="docs/screenshot.png" alt="Postcard Studio — screenshot placeholder" style="max-width:100%;border:1px solid #eaeaea;border-radius:8px" />

> Screenshot placeholder: replace `docs/screenshot.png` with a high‑resolution screenshot of the app (recommended 1200×630 for social previews).

---

## Features ✨

- 🤖 AI postcard generation — generate images + copy from prompts, templates, or uploaded photos
- 🛡️ Family‑safe AI screening — automated content filtering & human review queue
- 📏 Standard postal sizes — 4×6, 5×7, 6×11 (see table below)
- 🔁 Versioned cloud storage — automatic version history and rollback for each postcard
- 🔐 Optional passkey security — WebAuthn / platform authenticators for passwordless login
- 🌙 Dark mode & clean Apple‑inspired UI
- 🃏 Card carousel — beautiful, touch‑friendly card browsing with swipe/keyboard support
- 📦 ZIP export — export selected postcards as a ZIP for print or archive
- 📱 Responsive design — optimized for desktop, tablet and mobile

Standard sizes (common print targets):

| Name | Inches (W×H) | Pixels @ 300 DPI |
|---|---:|---:|
| 4×6 | 4 × 6 in | 1200 × 1800 px |
| 5×7 | 5 × 7 in | 1500 × 2100 px |
| 6×11 | 6 × 11 in | 1800 × 3300 px |

---

## Tech Stack 🧰

| Layer | Technologies / Notes |
|---|---|
| UI | HTML5, CSS3 (Apple‑inspired design), optional Tailwind or custom variables |
| JavaScript | Vanilla ES Modules, small helpers (carousel, local caching, JWT helpers) |
| AI | API‑backed generative models (prompt → image/text). Integration via secure server or proxy. |
| Auth | WebAuthn (passkeys) for optional passwordless, fallback to OAuth / JWT |
| Storage | Versioned cloud storage (S3 / S3‑compatible backends recommended) |
| Export | JSZip for ZIP creation, client‑side downloads |
| Security | CSP, secure cookies / token storage, family‑safe AI screening pipeline |
| Hosting | Static (index.html) → GitHub Pages / Netlify / Vercel / S3 + CloudFront |

---

## Getting started 🚀

Postcard Studio is designed to be a single HTML app for fast setup.

1. Clone the repo:
   ```bash
   git clone https://github.com/your-org/postcard-studio.git
   cd postcard-studio
   ```
2. Open locally:
   - Simply open `index.html` in your browser (works best from a server due to API calls / CORS).
   - For a local dev server you can run:
     ```bash
     # Python 3
     python -m http.server 8000
     # then open http://localhost:8000/index.html
     ```
3. Deploy:
   - Upload the repo to any static host (GitHub Pages, Netlify, Vercel) or serve via S3 + CloudFront.

Notes:
- The app is a static single‑file shell that expects optional backend endpoints for:
  - AI API proxy (to keep API keys secret)
  - Auth and versioned storage APIs
  If you want to run entirely client-side with third‑party services, configure secure proxies to avoid exposing keys.

---

## Usage Guide 🧭

Quick user flow:

1. Create an account or enable passkey login (recommended for security).
2. Start a new postcard:
   - Choose a size (4×6 / 5×7 / 6×11).
   - Pick a canvas template or blank template.
3. Generate art & copy:
   - Enter a prompt or select a template.
   - Choose generation options (style, color palette, aspect, safety level).
4. Family safety screening:
   - Generated content is automatically scanned. If flagged, the card goes to a local review queue or is blocked until edited.
5. Save & version:
   - Each save creates a new version. Open the version history to restore a prior state.
6. Share / export:
   - Use the ZIP export to download high‑res PNGs/PDFs for printing.
   - Use the share link to grant view access (configurable expiration).

Tips:
- For printing, export at 300 DPI with bleed as required by your printer.
- Use the carousel to preview a set of postcards; drag / swipe to reorder before exporting a ZIP.

---

## Security Features 🔐

Postcard Studio is built with user safety and data protection in mind.

- Passkey / WebAuthn (optional)
  - Passwordless sign‑in using platform authenticators (Touch ID, Face ID, security keys).
  - Reduces phishing and password theft risk.
  - Fallback to email / OAuth flows if passkeys not available.

- Family‑safe AI screening
  - Multi‑stage screening pipeline:
    - Fast client‑side checks (profanity filters, quick heuristics).
    - Model‑based content classification via an AI safety endpoint (image + text).
    - Configurable thresholds: block, warn, or flag for human review.
  - Administrators can configure strictness and review queues.

- Storage & privacy
  - Versioned cloud storage with per‑user access control.
  - Optional encryption-at-rest (via provider) and encryption-in-transit (HTTPS).
  - No API keys are stored in client-side code; use a server proxy or environment variables during deployment.

- Best practices
  - Use a server‑side proxy for AI calls to keep secrets safe.
  - Enable strict Content Security Policy (CSP) for production.
  - Rotate API keys and monitor usage.

---

## Deployment & Hosting 🛰️

Recommended quick hosts:
- GitHub Pages (static)
- Netlify / Vercel (static with optional serverless functions)
- S3 + CloudFront for high throughput

For AI and storage integrations:
- Use serverless functions (Netlify Functions / Vercel Serverless / AWS Lambda) as a secure proxy for AI APIs.
- Store images & versions in an S3 bucket with a versioning policy enabled.

---

## Contributing 🤝

Contributions are welcome — PRs, issues, and design ideas!

- Please open issues to discuss big changes before implementing.
- Follow the repository's Code of Conduct and CONTRIBUTING guidelines (add a file if needed).
- PR checklist:
  - Clear description of change
  - Screenshots for UI updates
  - Tests or manual verification instructions

---

## License

This project is licensed under the MIT License — see the LICENSE file for details.

---

## Credits & Acknowledgements

Built with care and AI assistance. Special thanks to:
- Claude
- GPT‑5
- Gemini

These models helped with copywriting, UX suggestions, and iteration of ideas.

---

If you'd like, I can also:
- Produce a ready‑to‑use `index.html` starter that wires up the UI, a demo carousel, and placeholders for API endpoints.
- Generate graphic assets for the Open Graph image and screenshot placeholders.