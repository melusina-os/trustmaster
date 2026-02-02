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

**Melusina TrustMaster License** - Three-Phase Time-Delayed License with AI Protection

This is a standalone public tool for verifying Melusina OS deployments and is not part of Melusina OS itself.

### License Phases

| Phase | License | Duration | Status |
|-------|---------|----------|--------|
| **1** | Business Source License 1.1 | Years 0-3 | 🔒 Current |
| **2** | Server Side Public License v1 | Years 3-5 | ⏳ Pending |
| **3** | GNU AGPL v3.0 | After Year 5 | ⏳ Pending |

### Permitted Uses (All Phases)

- ✅ Internal use (testing, evaluation, security auditing, compliance)
- ✅ Production use within your organization
- ✅ Modifications and derivative works
- ✅ Redistribution under the same license

### Restricted Uses

| Restriction | Phase 1 (BSL) | Phase 2 (SSPL) | Phase 3 (AGPL) |
|-------------|---------------|----------------|----------------|
| Competitive SaaS/hosted offerings | ❌ | ❌* | ✅ |
| SaaS without open-sourcing service stack | N/A | ❌ | ✅ (code only) |
| AI reverse engineering of code | ❌ | ❌ | ✅ |

*Phase 2 (SSPL) requires open-sourcing entire service stack if offering as SaaS

### ⚠️ AI Protection Clause (Phases 1 & 2 Only)

**STRICT PROHIBITION** on using AI/ML to reverse engineer, analyze, or derive insights from this codebase.

**Violation Damages (Joint & Several Liability):**
- 💰 **$1,000,000 USD** one-time payment
- 📊 **25% of annual turnover** perpetually

Liable parties: The person performing analysis + AI system developer/operator

> This clause expires when software enters Phase 3 (AGPL).

### Timeline

```
Feb 2024                Feb 2027                Feb 2029
    │                       │                       │
    ▼                       ▼                       ▼
┌───────────────────┬───────────────────┬───────────────────────────▶
│   PHASE 1: BSL    │  PHASE 2: SSPL    │    PHASE 3: AGPL-3.0
│   + AI Protection │  + AI Protection  │    (Full Open Source)
└───────────────────┴───────────────────┴───────────────────────────▶
```

## Links

- [Melusina OS](https://melusina-os.org)
- [Documentation](https://docs.melusina-os.org)
- [Solana Explorer](https://explorer.solana.com)
