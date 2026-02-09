# MailTaste Changelog

Notable features and improvements to [MailTaste](https://mailtaste.esoup.net), the DMARC report monitoring dashboard.

---

## February 8, 2026

### Account & Domain Deletion
- Email-confirmed account deletion with two-step flow (request, then confirm via email link)
- Email-confirmed domain removal for verified domains; unverified domains delete immediately
- Danger Zone section in Settings for account owners
- DMARC cleanup reminders: monthly emails if your DNS still points to MailTaste after deletion
- Blocked report tracking for deleted accounts — reports are silently discarded
- Updated privacy policy to describe the new deletion flow

### Data Export
- Export DMARC reports in CSV, Markdown, or rich HTML format
- HTML exports include styled tables and summary statistics
- Filter exports by domain, status, and time window (up to 90 days)
- Single report detail export

## January 24, 2026

### Dashboard Timeframe Selector
- Choose between 7-day, 30-day, and 90-day views across the entire dashboard
- All widgets (timeline chart, health stats, sources, offenders) respect the selected timeframe

### Organization Settings
- Rename your organization from Settings (admin/owner)
- Organization name displays in the banner and invite emails

### Needs Attention Detail View
- Click the Needs Attention widget to see individual failing events with dates
- Drill down into which IPs are failing authentication and when

## January 22, 2026

### Team Invites & Magic Link Auth
- Invite team members via email with role-based access (viewer, member, admin)
- Magic link login for invited users who don't have GitHub accounts
- Auto-login on invite accept — no second email required
- Role-based UI: viewers see reports only, members can manage domains, admins manage team

## January 21, 2026

### Top Offenders Report
- See which IPs are sending the most unauthorized email using your domains
- Helps identify spoofing sources and misconfigurations

### DMARC Record Generator
- Interactive DMARC record generator when setting up a domain
- Handles existing records — shows what to add vs. what to change
- Generates the correct `rua` tag with your MailTaste reporting address

### API Keys
- Generate API keys from Settings with scoped capabilities
- Programmatic access to all report data via REST API
- Key management: revoke keys, set expiration dates

### Per-Organization Encryption
- DMARC report IP addresses encrypted at rest with per-org AES-256-GCM keys
- Supports crypto shredding — deleting the org key makes report data unrecoverable

### Audit Trail
- Encrypted, append-only log of account actions (account creation, domain claims, deletions)
- Survives account deletion for compliance — retained 7+ years

### Privacy Policy
- Full privacy policy published at launch covering data collection, storage, retention, and deletion

### Performance
- Time-windowed data loading — only fetches the reports you need
- Logarithmic scale toggle on charts for domains with high volume
- Async DNS lookups on the Domains page with retry logic

### Per-Org Domain Limits
- Organizations limited to 10 domains (free plan)
- Usage indicator shows claimed vs. available slots

### Security Hardening
- Rate limiting across all endpoints (webhook, authenticated, demo, DNS)
- Timing-safe signature verification for Mailgun webhooks
- Reduced cache TTLs to 60 seconds

## January 20, 2026

### Multi-User & Auth
- eSoup Central Auth integration (GitHub OAuth)
- Multi-tenant architecture with per-org data isolation
- Domain onboarding workflow with DNS verification

### Database Migration
- Migrated from flat JSON files to MySQL with per-org encryption
- Reports stored with foreign key relationships for efficient querying

## January 19, 2026

### Inbound Report Processing
- Accept DMARC reports from any SMTP sender (not just known providers)
- Zip bomb protection: 1MB compressed, 50MB decompressed limits
- Failed reports quarantined for investigation

## January 18, 2026

### Initial Launch
- DMARC aggregate report parsing and visualization
- Timeline charts, source analysis, domain overview
- Report detail view with per-record breakdown
- Dark/light theme
- Live demo mode for unauthenticated visitors
