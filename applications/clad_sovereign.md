# Clad Sovereign – Native mobile sovereign RWA infrastructure

## 🌟 Project Overview

**Tagline**  
Open-source mobile-native signer and compliance pallet for sovereign real-world asset issuance on Polkadot.

**One-sentence description**  
Clad Studio & Clad Signer deliver a Substrate FRAME pallet for compliant RWA tokenization and a native iOS/Android biometric signer — built specifically for finance ministries and debt offices to issue sovereign bonds or equity without any browser or extension dependency.

**How it fits Polkadot**  
Pallet runs on any parachain or relay chain; mobile signer uses standard Substrate RPC, inherits Polkadot shared security, and supports XCM for cross-chain liquidity.

**Why we're doing this**  
Sovereign bond tokenization grew 260% in 2024 (€3B issued), with governments from Slovenia to Paraguay actively deploying blockchain infrastructure. However, all existing RWA platforms require browser extensions—which don't work on iOS/Android mobile browsers. This creates a technical barrier for institutions that increasingly rely on mobile workflows. We're building the first mobile-native signing infrastructure for Substrate RWA tokenization.

*[Watch 60-second demo – November 2025](https://www.loom.com/share/dd334230db154f9891f46664ae02aec4)*
![Clad Signer Demo – Native iOS & Android](https://cdn.loom.com/sessions/thumbnails/dd334230db154f9891f46664ae02aec4-9e6c0699711bd8ff-full-play.gif#t=0.1)

**What's working today (pre-funding):**
- ✅ Multi-validator local testnet (2 nodes: Alice + Bob validators, GRANDPA finality)
- ✅ Native iOS/Android app skeleton with navigation
- ✅ Biometric authentication UI flow (FaceID/TouchID/fingerprint prompts)
- ✅ Live block stream connection via Substrate RPC
- ✅ Pallet with ERC-3643 compliance patterns (mint/transfer/freeze/whitelist)

**What requires grant funding:**
- 🚧 **Pallet production hardening:** Benchmarking, real weight calculations, storage migrations, comprehensive testing
- 🚧 **Infrastructure:** Docker containerization, CI/CD setup, deployment documentation
- 🚧 **Mobile - Account management:** Secure key generation and biometric-protected storage (iOS Keychain + Android Keystore), account import from seed phrase or QR code
- 🚧 **Mobile - Data display:** Balance queries from pallet storage + system balances
- 🚧 **Mobile - Signing:** Full extrinsic signing and submission pipeline, offline QR signing for air-gapped scenarios


### 🔍 Project Details

**Tech stack**  
- Pallet & runtime: pure Substrate/FRAME (Rust, polkadot-stable2412)  
- Mobile signer: Kotlin Multiplatform + native UI (Jetpack Compose Android, SwiftUI iOS) using direct Substrate RPC (official Polkadot SDK primitives)

**Core components**  
- Pallet: role-based access, freeze/whitelist, ERC-3643-style hooks  
- Mobile: biometric key storage, offline QR signing, live RPC connection  
- Architecture: shared KMP business logic + fully native screens

**Current implementation**  
See "What's working today" section above for detailed breakdown.

**Planned functionality:**
- Pallet extrinsics: mint, transfer, freeze/unfreeze, whitelist add/remove
- Mobile: secure account import, biometric key storage, balance queries, extrinsic signing/submission, offline QR flow

**Scope boundaries:**  
This grant focuses on a specialized ministry issuance tool, not a general-purpose wallet:
- ❌ No support for native DOT/KSM transfers
- ❌ No staking, governance voting, or NFT support
- ❌ No third-party token integration
- ✅ Only displays: ministry-issued sovereign tokens (pallet-clad-token) + minimal system balance for fees

This narrow scope is intentional for the MVP—finance officials need focused tools, not feature-bloated wallets. Future extensions (multi-account management, additional pallet support, hardware wallet integration) are planned for post-grant phases as outlined in Future Plans section.


### 🧩 Ecosystem Fit

**Where it fits**  
Real-World Assets (RWA) + institutional tooling category on Polkadot.

**Target audience**  
Finance ministries, debt-management offices, and state-owned enterprises in emerging markets.

**Problem solved**  
Browser extensions don't work on mobile: iOS blocks extension support entirely, and Chrome for Android still doesn't support them. MetaMask mobile requires using an in-app browser rather than Safari/Chrome, creating poor UX for professional workflows. Meanwhile, debt management offices modernized to remote/mobile operations post-COVID, requiring accessible signing infrastructure.

Clad Signer provides a native iOS/Android app with biometric-secured key storage, enabling institutional users to sign RWA extrinsics directly from their mobile devices—no browser dependency, no extension workarounds, fully open-source and self-hostable.

**Similar projects & differentiation**
- **Centrifuge** → $646M financed assets, browser-based platform, no mobile-native signer
- **Polymesh** → Permissioned chain with 200+ tokens, compliance-focused but not sovereign-controlled
- **Polkadot Vault** → Air-gapped general signer, no RWA-specific workflows or institutional UX

**Our differentiation:**
1. **Mobile-native Substrate signer** (Kotlin Multiplatform with native iOS/Android UI—addresses documented browser extension limitations)
2. **Compliance-first pallet** (ERC-3643 patterns adapted for Substrate: $28B tokenized with this standard validates the approach)
3. **Open-source infrastructure** (reusable by any Substrate chain, not tied to single parachain or vendor)
4. **Institutional UX focus** (biometric signing, offline QR flows, ministry-appropriate permissioning—not consumer wallet features)

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
- https://github.com/clad-sovereign/clad-studio (Substrate pallet + runtime)
- https://github.com/clad-sovereign/clad-mobile (Kotlin Multiplatform signer)

**Background**

Software developer with 11 years across enterprise platforms and fintech systems (2011-2022) before founding WIDEAS Technologies, OPC in late 2022. Prior experience includes Oracle-NetSuite implementations and eCommerce customizations (2015-2020), building a stock options trading analytics platform integrating Finance APIs (2011-2012), and delivering web/mobile applications across various lines of business.

Technical background spans NetSuite/Salesforce enterprise platforms, mobile development (progressing from early frameworks to current Kotlin Multiplatform focus), and desktop applications programming (C# .NET). Currently running solo consultancy focused on mobile projects for clients; Clad Studio represents first blockchain-native work, applying lessons from prior financial tooling experience to sovereign tokenization infrastructure.

No prior blockchain contributions, but committed to building open-source infrastructure (Apache 2.0) for the Polkadot ecosystem rather than proprietary solutions.

## 📊 Development Status

**Timeline:**
- Project inception: November 2025
- MVP development: 3 weeks (Nov 1-22, 2025)
- Current status: Functional testnet + demo-ready mobile app (see video above)

**Market context:**
Sovereign bond tokenization is accelerating (sources: government press releases, industry reports):
- Slovenia (€30M, July 2024), Hong Kong ($100M, 2023-2024), Germany (€8.5B KfW, 2024), Paraguay ($6M on Polkadot via Moonbeam, Q3 2025 launch)
- RWA market: $24B in 2025, up 380% in 3 years (McKinsey projects $2T by 2030)
- Government bond DLT issuance: €3B in 2024, up 260% YoY (BIS reports)

Despite this growth, mobile tooling lags behind. This grant would enable production-ready infrastructure as institutional adoption scales.

## 📅 Development Roadmap

### Overview

- **Estimated Duration:** 3 months
- **Full-Time Equivalent (FTE):** 1
- **Total Costs:** $30,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | Apache 2.0 (both clad-studio and clad-mobile repositories) |
| 0b. | Documentation | Inline code documentation + comprehensive tutorial covering: (1) local testnet setup, (2) building mobile apps for iOS/Android, (3) account import/key management, (4) signing extrinsics end-to-end. Target audience: Debt Management Office (DMO) IT teams and institutional deployers. |
| 0c. | Testing and Testing Guide | **Pallet:** Full unit test coverage for all extrinsics (mint/transfer/freeze/whitelist) with edge cases. **Mobile:** Integration tests for key storage, signing pipeline, and RPC connection. Guide includes CI/CD setup for reproducible builds. |
| 0d. | Docker | We will provide a Dockerfile that can be used to run the local testnet and test all pallet functionality delivered with this milestone. |
| 0e. | Article | Technical article (Medium/Polkadot blog) explaining: (1) why mobile-native signing matters for sovereign issuers, (2) architecture decisions (KMP + biometric storage), (3) security model, (4) how to extend for custom use cases. |
| 1. | Substrate Pallet Hardening | **Production-ready pallet-clad-token:** Benchmark all extrinsics with real weight calculations, add storage migration framework, implement additional error handling for edge cases, complete inline documentation for all public functions. **Verification:** Run benchmarks, generate weight files, execute test suite (>90% coverage). |
| 2. | Mobile Core: Complete Signing Infrastructure | **Secure account management:** QR/seed import with BIP39 validation, biometric-protected key storage (iOS Keychain + Android Keystore), balance display (system + pallet-clad-token storage queries). **Extrinsic signing:** Full signing pipeline for all pallet-clad-token extrinsics (mint/transfer/freeze/whitelist/remove), offline QR flow for air-gapped scenarios (generate unsigned tx → scan → sign → broadcast). **Verification:** Import test account, lock/unlock with biometric, view balances updating in real-time, successfully mint/transfer pallet-clad-token assets via mobile app (not DOT/KSM), complete offline signing round-trip. |

### 💰 Budget Breakdown

**By Milestone:**

| Milestone | Deliverables | Cost (USD) | Estimated Completion |
| --------- | ------------ | ---------- | -------------------- |
| 1 | 0a–0e + Deliverable 1 (Pallet hardening + Docker) | $12,000 | 1.5 months |
| 2 | Deliverable 2 (Complete mobile signing infrastructure) | $18,000 | 1.5 months |
| **Total** | | **$30,000** | **3 months** |

**By Category:**

| Category | Item | Cost per Unit | Amount | Total | Description |
| --- | --- | --- | --- | --- | --- |
| Personnel | Solo Developer (Milestone 1) | $80/hour | 150 hours | $12,000 | Pallet benchmarking, weight calculation, storage migrations, Docker setup, comprehensive testing framework, documentation, article |
| Personnel | Solo Developer (Milestone 2) | $80/hour | 225 hours | $18,000 | Mobile account management, biometric key storage, balance queries, extrinsic signing pipeline, offline QR flow, integration testing |
| --- | --- | --- | **Total** | **$30,000** | |

**Budget rationale:**
Total: 375 hours @ $80/hour. This rate reflects solo founder economics (no overhead, no profit margin) focused entirely on technical execution. Milestone 1 allocates realistic time for production-grade pallet hardening (benchmarking, weight generation, storage migrations) plus Docker containerization and comprehensive documentation. Milestone 2 focuses on complete mobile signing infrastructure covering both iOS/Android platforms with biometric security and offline capabilities.

## 🔮 Future Plans

**Immediate post-grant (Q2-Q3 2026):**
- Publish comprehensive deployment guides for Substrate chains wanting mobile RWA signing
- Contribute mobile signer integration documentation to Polkadot SDK resources
- Engage with existing Polkadot RWA projects (Centrifuge, Phyken, others) for integration testing
- Gather feedback from open-source community on production deployment patterns

**Phase 2 funding (Q3-Q4 2026):**
- Apply for Web3 Foundation General Grant to fund:
  - Additional pallet features (multi-signature governance, dividend distribution, oracle integration)
  - Security audit by Trail of Bits or equivalent
  - Extended mobile features (multi-account management, hardware wallet integration)
  - White-label deployment tooling for parachain teams

**Phase 3 scaling (2027+):**
- Pursue Polkadot Treasury referendum for ecosystem-wide adoption
- Build reference implementations for common RWA use cases (bonds, equity, real estate)
- Expand mobile signer to support additional Substrate pallets beyond clad-token
- Establish as go-to mobile signing infrastructure for institutional Polkadot deployments

**Long-term vision:**  
Become the standard mobile signing layer for Substrate-based RWA tokenization—open-source infrastructure that any parachain, sovereign chain, or institutional deployment can adopt. Enable the Polkadot ecosystem to compete with Ethereum's institutional tooling (Polymesh, ERC-3643 platforms) by providing production-grade mobile UX that existing platforms lack.

## Additional Information

**Other funding:**
No other grants have been submitted or received for this project. This is the first and only funding application for Clad Sovereign.
