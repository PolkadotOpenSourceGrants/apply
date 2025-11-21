# Clad Sovereign – Native mobile sovereign RWA infrastructure

## 🌟 Project Overview

**Tagline**  
Open-source mobile-native signer and compliance pallet for sovereign real-world asset issuance on Polkadot.

**One-sentence description**  
Clad Studio & Clad Signer deliver a Substrate FRAME pallet for compliant RWA tokenization and a native iOS/Android biometric signer — built specifically for finance ministries and debt offices to issue sovereign bonds or equity without any browser or extension dependency.

**How it fits Polkadot**  
Pallet runs on any parachain or relay chain; mobile signer uses standard Substrate RPC, inherits Polkadot shared security, and supports XCM for cross-chain liquidity.

**Why we’re doing this**  
To provide emerging-market issuers with secure, sovereign-controlled mobile infrastructure for real-world asset tokenization.

*[Watch 60-second demo – November 2025](https://www.loom.com/share/dd334230db154f9891f46664ae02aec4)*  
![Clad Signer Demo – Native iOS & Android](https://cdn.loom.com/sessions/thumbnails/dd334230db154f9891f46664ae02aec4-9e6c0699711bd8ff-full-play.gif#t=0.1)\
*(Current demo shows native iOS/Android biometric connection + live block stream. Full signing and issuance coming in funded milestones.)*


### 🔍 Project Details

**Tech stack**  
- Pallet & runtime: pure Substrate/FRAME (Rust, polkadot-stable2412)  
- Mobile signer: Kotlin Multiplatform + native UI (Jetpack Compose Android, SwiftUI iOS) using direct Substrate RPC (official Polkadot SDK primitives)

**Core components**  
- Pallet: role-based access, freeze/whitelist, ERC-3643-style hooks  
- Mobile: biometric key storage, offline QR signing, live RPC connection  
- Architecture: shared KMP business logic + fully native screens

**Current MVP (already shipped)**  
Multi-validator testnet + native iOS/Android signer with biometric auth and live block stream (see demo).

**Functionality**  
Pallet extrinsics: mint, transfer, freeze/unfreeze, whitelist add/remove  
Mobile: metadata fetch, balance queries, extrinsic building/signing/submit

**What it is NOT**  
Not a general-purpose wallet; no support for native DOT/KSM, staking, governance voting, or third-party tokens. Balance display is limited to the ministry-issued sovereign token (pallet-clad-token) and minimal system balance for transaction fees.


### 🧩 Ecosystem Fit

**Where it fits**  
Real-World Assets (RWA) + institutional tooling category on Polkadot.

**Target audience**  
Finance ministries, debt-management offices, and state-owned enterprises in emerging markets.

**Problem solved**  
Officials in these jurisdictions use mobile phones as their primary work device and cannot/will not install browser extensions. Clad Signer gives them a biometric-secured, ministry-grade native app to issue and manage tokenized sovereign bonds or equity.

**Similar projects & differentiation**  
- Centrifuge, Maple, Goldfinch → browser-based, focused on US/EU private credit  
- Polymesh → permissioned chain for enterprises

Clad Signer is the **first native mobile signer** explicitly built for sovereign/emerging-market issuers.

## 👥 Team

**Team**  
WIDEAS Technologies, OPC  
https://wideas.tech

**Contact**  
Ed Bienes – helloclad@wideas.tech

**Member**  
Ed Bienes (solo founder)  
www.linkedin.com/in/edbienes

**GitHub**  
- Org: https://github.com/clad-sovereign  
- Personal: https://github.com/edbienes

**Repos**  
- https://github.com/clad-sovereign/clad-studio  
- https://github.com/clad-sovereign/clad-mobile

Former corporate developer and technical consultant with over 12 years delivering enterprise and fintech systems — including Oracle/NetSuite implementations, a stock-options trading dashboard, and as part of the team that built a Singapore-funded asset-management web app. Left the corporate world in late 2022 to run WIDEAS Technologies, OPC full-time. Clad Sovereign is the sole focus since November 2025.

## 📊 Development Status

Project started November 2025.

Current state: working multi-validator node + native iOS/Android signer with biometric authentication, metadata fetch, and live block stream (see demo).

No prior blockchain contributions.

## 📅 Development Roadmap

### Overview

- **Estimated Duration:** 4 months
- **Full-Time Equivalent (FTE):** 1
- **Total Costs:** $30,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | Apache 2.0 |
| 0b. | Documentation | We will provide both **inline documentation** of the code and a basic **tutorial** that explains how a user can run the node and connect with the mobile signer. |
| 0c. | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness. In the guide, we will describe how to run these tests. |
| 0d. | Article | We will publish an **article** that explains what was done/achieved as part of the grant. |
| 1. | Account & Balance | Secure account import (QR/seed) + biometric-protected key storage + balance display (system + pallet-clad-token). Verify: run app, import account, see balances update live. |
| 2. | Signing & QR | Full extrinsic signing for pallet-clad-token (mint/transfer/freeze/whitelist/remove) + offline QR flow + push notifications. Verify: build/sign/submit extrinsic via app. |
| 3. | Pilot preparation | White-label ministry theme + localized strings (English + one additional language) + non-monetary pilot package for debt offices. Verify: build and run branded APK/IPA. |

### 💰 Budget Breakdown

| Milestone | Deliverables         | Cost (USD) | Estimated Completion |
| --------- | -------------------- | ---------- | -------------------- |
| 1         | Deliverables 0a–0d + 1 | $10,000    | 1.5 months           |
| 2         | Deliverable 2        | $10,000    | 1.5 months           |
| 3         | Deliverable 3        | $10,000    | 1 month              |
| **Total** |                      | **$30,000**| **4 months**         |

Budget covers 4 months of full-time solo development at $80/hour (375 hours total).

## 🔮 Future Plans

- Run non-monetary pilots with 2–3 debt-management offices or state issuers (Q3–Q4 2026)
- Apply for a larger Web3 Foundation General Grant to fund white-label deployments, oracle integrations, and operational support
- Pursue Polkadot Treasury referendum for scaling once pilots are live

**Long-term vision**  
Become the default native mobile issuance and signing layer for sovereign real-world assets on Polkadot — the trusted, ministry-grade tool that enables finance ministries and state issuers in the Global South to deploy and manage tokenized debt and equity under their full control.
