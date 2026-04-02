<div align="center">

# Shadowchain

**Decentralized Reputation Layer for the Open Internet**

[![Polkadot SDK](https://img.shields.io/badge/Polkadot%20SDK-E6007A?style=flat-square&logo=polkadot&logoColor=white)](https://github.com/paritytech/polkadot-sdk)
[![Substrate](https://img.shields.io/badge/Substrate-232323?style=flat-square)](https://substrate.io)
[![IPFS](https://img.shields.io/badge/IPFS-65C2CB?style=flat-square&logo=ipfs&logoColor=white)](https://ipfs.io)

Transform your Web2 footprint into verifiable Web3 identity

[Live Demo](https://shadowchain.locsafe.org) | [Docs](docs/arch.md) | [Discord](#)

</div>

---

## What is Shadowchain?

Shadowchain mirrors your digital activity from centralized platforms into a blockchain-verified, user-controlled archive. Your GitHub commits, tweets, and professional history become portable, verifiable credentials you actually own.

**The problem:** Platforms control your data. Accounts get suspended. APIs change. Your digital reputation is locked in silos you don't control.

**The solution:** Cryptographic proofs of your contributions, stored on IPFS, anchored on Polkadot. Portable across Web3. Owned by you.

---

## Architecture

```mermaid
%%{init: {'theme':'dark', 'themeVariables': { 'primaryColor':'#3b82f6','primaryTextColor':'#f8fafc','primaryBorderColor':'#60a5fa','lineColor':'#94a3b8','secondaryColor':'#06b6d4','tertiaryColor':'#8b5cf6','fontSize':'14px'}}}%%
flowchart LR
    subgraph sources["Data Sources"]
        GH[GitHub]
        TW[Twitter/X]
    end
    
    subgraph shadow["Shadowchain"]
        direction TB
        ENC[Encrypt Locally]
        IPFS[(IPFS Storage)]
        CHAIN[Parachain]
    end
    
    subgraph output["Verifiable Output"]
        CREDS[Credentials]
        XCM[Cross-chain Queries]
    end
    
    GH --> ENC
    TW --> ENC
    ENC --> IPFS
    ENC --> CHAIN
    CHAIN --> CREDS
    CHAIN --> XCM
    
    classDef source fill:#334155,stroke:#64748b,color:#f8fafc
    classDef core fill:#3b82f6,stroke:#60a5fa,color:#f8fafc
    classDef out fill:#06b6d4,stroke:#22d3ee,color:#f8fafc
    
    class GH,TW source
    class ENC,IPFS,CHAIN core
    class CREDS,XCM out
```

**How it works:**
1. Authorize platform access via OAuth
2. Data encrypted client-side (keys never leave your device)
3. Encrypted blobs stored on IPFS
4. Content hashes anchored on Shadowchain parachain
5. Credentials queryable cross-chain via XCM

---

## Quick Start

```bash
git clone https://github.com/tufstraka/shadowchain.git
cd shadowchain
make install-deps
cp .env.example .env  # Add OAuth credentials
make dev              # Starts everything
```

Open `http://localhost:3000`, connect wallet, authorize platforms, mirror your data.

**Prerequisites:** Node.js 18+, Docker, Polkadot.js extension

---

## Use Cases

| Scenario | Problem | Shadowchain Solution |
|----------|---------|---------------------|
| **Developer hiring** | GitHub accounts can be faked | Blockchain-verified commit history |
| **DAO membership** | No proof of contribution | Reputation-weighted voting |
| **DeFi lending** | Requires overcollateralization | Reputation-based loan terms |
| **Deplatforming** | Lose years of content | Censorship-resistant archive |

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| **Blockchain** | Substrate/FRAME, custom pallets |
| **Storage** | IPFS with XSalsa20-Poly1305 encryption |
| **Identity** | KILT DIDs, W3C Verifiable Credentials |
| **Interop** | XCM v3 cross-chain queries |

---

## Roadmap

```mermaid
%%{init: {'theme':'dark', 'themeVariables': { 'done0':'#22c55e','active0':'#06b6d4','crit0':'#ef4444','grid':'#334155','textColor':'#f8fafc','fontSize':'12px'}}}%%
gantt
    dateFormat YYYY-MM
    section Complete
    GitHub Integration          :done, 2025-07, 2025-10
    Twitter/X Integration       :done, 2025-08, 2025-11
    IPFS Storage                :done, 2025-09, 2025-12
    Client-side Encryption      :done, 2025-10, 2026-01
    Web Dashboard               :done, 2025-11, 2026-02
    section In Progress
    Performance Optimization    :active, 2026-02, 2026-04
    section Upcoming
    KILT DIDs + XCM             :2026-04, 2026-07
    LinkedIn, Reddit, Discord   :2026-06, 2026-09
    Security Audit              :crit, 2026-08, 2026-10
    Mainnet Launch              :crit, 2026-11, 2026-12
    section 2027
    Mobile App                  :2027-01, 2027-03
    AI Reputation Scoring       :2027-02, 2027-06
```

---

## Security

- **Zero-knowledge:** Backend never sees plaintext data
- **Client-side encryption:** Keys derived from wallet signature
- **Selective disclosure:** Share only what you choose
- **Revocable:** Invalidate OAuth tokens anytime

---

## Contributing

We welcome contributions in Rust/Substrate, TypeScript, DevOps, and documentation.

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## Links

[Website](https://shadowchain.locsafe.org) | [GitHub](https://github.com/tufstraka/shadowchain) | [Twitter](https://twitter.com/shadowchain) | [Discord](https://discord.gg/shadowchain)

---

<div align="center">

**Built on Polkadot. Secured by cryptography. Owned by you.**

MIT License

</div>
