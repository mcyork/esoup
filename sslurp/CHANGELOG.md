# SSLurp Changelog

Notable features and improvements to [SSLurp](https://sslurp.esoup.net), the SSL certificate monitoring tool.

---

## January 19, 2026

### Centralized Unsubscribe
- All email unsubscribe links now route through esoup.net central subscription management

## January 15, 2026

### Mailing List
- Subscribe to SSLurp updates from the registration page
- Welcome email on subscribe with tag-specific unsubscribe
- Suppression checking — skips sending if you've previously unsubscribed
- Elevated rate limits (10x) available via API key capability flag

## January 14, 2026

### Cryptographic Chain Validation
- Verifies certificate signatures up the chain against Mozilla's trusted root store (144 CAs)
- Shows which root CA anchors the chain and whether each signature is valid
- Custom CA paths supported via `CUSTOM_CA_PATHS` environment variable
- CA bundle updater script for keeping roots current

### Email Results
- POST /check with an API key sends a styled email report of the certificate details
- Email includes owner, issuer, validity, SANs, chain verification, and trusted root info
- Plain text fallback for all emails

### Privacy Policy
- Published privacy policy covering API key data, email encryption, and retention

### UI Unification
- Shared header component across all pages with logo and navigation
- Full-width gradient header matching the brand style
- Consistent page layouts for checker, API docs, help, about, privacy, and registration

## January 13, 2026

### API Key System
- Self-service registration with email verification
- Stateless HMAC-SHA256 signed keys — no database required
- Slot-based revocation tracking with generation rotation
- Tiered keys (T/S/M/L) with varying TTL
- 16-bit capability flags for granular permissions
- Admin CLI for key issuance, revocation, and generation stats

### Interactive API Documentation
- Collapsible endpoint sections with live examples
- Try-it-yourself forms for each endpoint

## January 12, 2026

### Initial Launch
- Check SSL certificates by IP address with optional SNI and port
- Full certificate chain retrieval with OpenSSL fallback
- Hostname validation (CN and SAN matching)
- Certificate details: owner, issuer, validity dates, key algorithm, serial number
- Subject Alternative Names display
- Batch checking — up to 25 certificates in one request
- Rate limiting: 10 checks/min per IP, 500/day per /24 subnet
- SSRF protection — blocks private IPs and cloud metadata endpoints
- Security headers: CSP, HSTS, X-Frame-Options, Permissions-Policy
- Route allowlist — unrecognized paths return 404
- Help page and about page with links to related tools
