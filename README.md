# Melusina TrustMaster

🧬 **Blockchain-powered trust verification for Melusina OS deployments**

[![Deploy to GitHub Pages](https://github.com/melusina-os/trustmaster/actions/workflows/deploy-pages.yml/badge.svg)](https://github.com/melusina-os/trustmaster/actions/workflows/deploy-pages.yml)

## Live Verification Tool

**[➡️ Launch Verifier](https://melusina-os.github.io/trustmaster/verify/)**

## Deployment

This repository uses a two-branch model:
- **`main`** - Source code and development
- **`gh-pages`** - Auto-deployed static site (via GitHub Actions)

Any push to `main` automatically deploys to `gh-pages` and updates the live site.

## What It Does

TrustMaster verifies the complete trust chain for any Melusina OS deployment:

1. **DNS Records** - Verifies `_melusina` TXT records via DNS-over-HTTPS
2. **License NFT** - Validates Solana blockchain license authenticity
3. **Reseller Chain** - Traces provenance: License → Reseller → Foundation
4. **Foundation Verification** - Confirms link to Master NFT
5. **Release Authenticity** - Verifies release hash against on-chain signatures
6. **DANE/TLS** - Checks certificate pinning via TLSA records

## Usage

1. Visit [melusina-os.github.io/trustmaster/verify/](https://melusina-os.github.io/trustmaster/verify/)
2. Enter a domain (e.g., `test.melusina-os.org`)
3. Click **Verify**
4. View complete trust chain with green checkmarks ✅

## API Integration

The verifier can be invoked with URL parameters:

```
https://melusina-os.github.io/trustmaster/verify/?domain=example.melusina-os.org
```

## Networks Supported

- **Devnet** - For testing and development
- **Mainnet-beta** - Production deployments

## Trust Chain Architecture

```
┌─────────────────────────────────────────┐
│         Melusina Foundation             │
│         (Master NFT Holder)             │
└─────────────────┬───────────────────────┘
                  │ Print Edition
                  ▼
┌─────────────────────────────────────────┐
│            Reseller NFT                 │
│     (Territory + Quota Limited)         │
└─────────────────┬───────────────────────┘
                  │ Print Edition
                  ▼
┌─────────────────────────────────────────┐
│            License NFT                  │
│    (Domain-Bound + M-of-N Threshold)    │
└─────────────────┬───────────────────────┘
                  │ DNS TXT Records
                  ▼
┌─────────────────────────────────────────┐
│         Deployed Instance               │
│   (Verifiable by anyone, anywhere)      │
└─────────────────────────────────────────┘
```

## License

Server Side Public License (SSPL) v1 with Time-Delayed Conversion - This is a standalone public tool for verifying Melusina OS deployments and is not part of Melusina OS itself.

**Permitted Uses:**
- ✅ Internal use (testing, evaluation, security auditing, compliance)
- ✅ Production use within your organization
- ✅ Modifications and derivative works
- ✅ Redistribution under the same license

**Restricted Uses:**
- ❌ Offering as a Service (SaaS) without open-sourcing your entire service stack

**Change License:** After 3 years, each version automatically converts to GNU Affero General Public License v3.0 (AGPL-3.0).

> **Note:** SSPL is source-available but not OSI-approved open source. After conversion to AGPL, the software becomes true open source.

## Links

- [Melusina OS](https://melusina-os.org)
- [Documentation](https://docs.melusina-os.org)
- [Solana Explorer](https://explorer.solana.com)
