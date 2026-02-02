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

TrustMaster verifies the **complete 4-layer trust chain** for any Melusina OS deployment:

### Layer 1: Foundation
- ✅ Master NFT exists and is active
- ✅ Foundation keyholders (3-of-5 threshold)
- ✅ Global app/author registries
- ✅ Signed release hashes

### Layer 2: Reseller
- ✅ Reseller NFT linked to Foundation
- ✅ Territory and quota within limits
- ✅ Reseller active (not revoked)

### Layer 3: Licensee
- ✅ License NFT exists with correct domain binding
- ✅ TLS fingerprint matches on-chain record (SHA256 of pubkey)
- ✅ License signers registered (M-of-N threshold)
- ✅ Admin designations verified
- ✅ Local app approvals

### Layer 4: Shares
- ✅ Grain Share Registry exists
- ✅ Share entries (wallet-bound or URL token)
- ✅ Cross-domain share verification

## Verification Checks

| Check | Description |
|-------|-------------|
| **DNS Records** | Queries \`_melusina\` TXT records via DNS-over-HTTPS |
| **License NFT** | Validates Solana blockchain license authenticity |
| **TLS Fingerprint** | Verifies SHA256 of server TLS pubkey matches on-chain |
| **Reseller Chain** | Traces: License → Reseller → Foundation |
| **Foundation** | Confirms link to Master NFT |
| **Admin NFT** | Verifies admin wallet has valid InstallAdmin designation |
| **Grain Registry** | Checks per-grain share registries |
| **Release Authenticity** | Verifies release hash against Foundation signatures |
| **DANE/TLS** | Checks certificate pinning via TLSA records |

## Usage

1. Visit [melusina-os.github.io/trustmaster/verify/](https://melusina-os.github.io/trustmaster/verify/)
2. Enter a domain (e.g., \`test.melusina-os.org\`)
3. Click **Verify**
4. View complete trust chain with green checkmarks ✅

### Verify Admin Access
\`\`\`
https://melusina-os.github.io/trustmaster/verify/?domain=example.com&admin=7XUx...Fms
\`\`\`

### Verify Share Access
\`\`\`
https://melusina-os.github.io/trustmaster/verify/?domain=example.com&grain=abc123&wallet=Bob...Xyz
\`\`\`

## Networks Supported

- **Devnet** - For testing and development
- **Mainnet-beta** - Production deployments

## Authentication

**No LDAP** - Admin authentication is on-chain:

1. License holder designates admin wallets via \`designate_install_admin\`
2. Admin connects Solana wallet to Sandstorm
3. System verifies \`InstallAdmin\` PDA on Solana
4. Access granted based on role (Operator/Manager/Security/Root)

Admin designations are **soulbound** (non-transferable) and can be recalled instantly.

## Token Transferability

| Token | Transferable? | Rationale |
|-------|---------------|-----------|
| Master NFT | ✅ Yes | Foundation ownership can change |
| Keyholder NFT | ❌ **Soulbound** | Authority not tradeable |
| Reseller NFT | ✅ Yes | Business can be sold |
| License NFT | ✅ Yes | Installation can be transferred |
| Share NFT* | **Configurable** | Issuer chooses per-share |

*Shares use on-chain registry, NFT is optional proof

## License

MIT License - Part of the Melusina OS project.

## Links

- [Melusina OS](https://melusina-os.org)
- [Documentation](https://docs.melusina-os.org)
- [Architecture](../docs/MELUSINA_ARCHITECTURE_v2.html)
- [Solana Explorer](https://explorer.solana.com)
