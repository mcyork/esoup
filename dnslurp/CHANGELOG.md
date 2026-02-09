# DNSlurp Changelog

Notable features and improvements to [DNSlurp](https://dnslurp.esoup.net), the DNS lookup and diagnostic tool.

---

## January 27, 2026

### API Documentation
- All API doc sections now collapsible for easier scanning
- Each section shows a subtitle hint and expands on click

## January 25, 2026

### NS Delegation Validation
- Compares parent zone delegation (NS + glue records) against zone apex NS records
- Flags mismatches: extra NS records, glue IP conflicts, missing glue
- Available as `validateNS` parameter on authoritative lookups

### Enterprise Edition
- Cross-platform standalone binaries (Windows, Linux x64/arm64, macOS x64/arm64)
- Three-tier configuration: environment variables, config.json, built-in defaults
- Custom branding: page title, about page content
- Audit logging to stdout, syslog (Splunk/Graylog), or file
- Hostname binding for secure internal deployments

### Ed25519 License System
- Self-service license generation with cryptographic signing
- Licensed instances can customize rate limits, branding, and DNS server config
- Non-expiring licenses verified at startup

## January 21, 2026

### DNS Configuration
- Externalized DNS server lists to config.json for easy customization
- Added underscore support in domain validation for service records (`_dmarc`, `_dkim`, etc.)

## January 17, 2026

### Initial Launch
- Query 24 DNS record types including full DNSSEC support (DS, DNSKEY, RRSIG, NSEC)
- Compare results across multiple DNS servers simultaneously
- Authoritative lookups that trace the delegation chain from root to target
- Raw UDP queries with automatic TCP fallback for truncated responses
- DNS-over-HTTPS (DoH) support for Google, Cloudflare, and Quad9
- Exposes DNS flags: AA, AD, TC, RA and response codes
- Export results to Markdown and CSV
- RESTful API with shareable GET links
- Rate limiting: 20 lookups/min, 10 authoritative/min, 1000/day per subnet
- Security headers: CSP, HSTS, X-Frame-Options, Permissions-Policy
- Route allowlist — unrecognized paths return 404
