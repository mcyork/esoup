# Sipcode Changelog

Notable features and improvements to [Sipcode](https://box.esoup.net), the dynamic QR code platform.

---

## January 20, 2026

### Management Hardening
- Auth changed from email+PIN to secretGuid+PIN for stronger security
- "My QR Codes" page converted to compact table view with sorting (newest, oldest, most scans, name)
- "Description" field renamed to "Title" for clarity

## January 18, 2026

### API Key System
- Self-service API key registration with email verification
- Full REST API: create, list, update, delete, and stats for QR codes
- Interactive API documentation page with theme support

## January 17, 2026

### Rewrite & Rebrand
- Complete rewrite from Python/Flask to TypeScript/Bun
- Migrated to MySQL with full backwards compatibility
- Rebranded from "Logo QR" to Sipcode with QR-themed wax seal logo

### Graffiti Generator
- Client-side Canvas rendering with 12 graffiti fonts
- 86 wall backgrounds with customizable text, color, size, rotation
- Create QR codes directly from graffiti tags
- Shareable via URL parameters

### Label Sheets
- Generate printable PDF label sheets with QR codes
- Avery label sizes: 5163 (shipping), 5160 (address), 5167 (return address), 22806 (square)
- Custom grid option for cutting your own
- US Letter and A4 paper sizes

### Pre-Printed Label Claim Flow
- Print blank QR code labels, stick them on things
- Scan to claim and activate — assign a destination URL on first use

### QR Code Customization
- Color picker with ROYGBIV presets
- Bulk image ZIP download for batch exports

### Theme System
- Four themes: Dark, Dim, Dusk, Light
- Persists across sessions

### Google Safe Browsing
- Validates destination URLs against Google's threat database
- Blocks malicious and phishing URLs with database-cached results

### Authentication & Email
- Session-based auth with 6-digit PIN protection
- Exponential backoff on failed attempts (1s to 1h)
- Mailgun email integration for QR creation confirmations
- PIN entry page before showing edit form

### Security
- Rate limiting and SSRF protection
- Security headers: CSP, HSTS, X-Frame-Options
- Modular architecture — if one module fails, others keep running
