# x402 for Substrate Chains: Grant Proposal

## Name of Your Project

**x402 Substrate SDK & Facilitator Network**

### Tagline
HTTP 402 native payment protocol for Polkadot and Substrate-based chains, unlocking chain-agnostic micropayments for the Web3 ecosystem.

---

## Project Overview

### Brief Description

This project brings the x402 protocol, an HTTP 402-native payment standard currently dominant on Solana and EVM chains to the Polkadot ecosystem through two JavaScript/TypeScript libraries: an **x402 SDK** for client-side payment integration and an **x402 Facilitator** service for server-side payment verification and settlement.

x402 enables any HTTP API to require blockchain-backed micropayments before serving resources. Unlike traditional payment processors charging 2.9% + $0.30 per transaction, x402 charges zero protocol fees and allows settlement in milliseconds. On Solana, x402 processed over 500,000 weekly transactions as of October 2025, with 10,000% growth in a month, demonstrating massive demand for internet-native payments that autonomous AI agents can execute without human intervention.

The Substrate implementation addresses a critical gap: while x402 has achieved product-market fit on Solana and limited EVM support via Base, **no native Substrate implementation exists**. This proposal delivers chain-agnostic x402 support specifically optimized for Polkadot's architecture, enabling parachains, dApps, and wallets to integrate HTTP 402 payments with Substrate-native tokens and XCM interoperability.

### Integration with Polkadot/Kusama

The libraries will integrate seamlessly into the Polkadot SDK (formerly Substrate) ecosystem:

- **Client SDK**: Works with Polkadot.js, integrates with wallets supporting Substrate chains, and leverages XCM for cross-parachain settlements
- **Facilitator**: Runs as an off-chain worker or independent service, can settle payments directly on any Substrate chain's runtime, and respects Polkadot's governance model for fee structures
- **Protocol Flexibility**: Supports native DOT/KSM as settlement assets, custom tokens via pallet-assets, and cross-chain settlement via XCM bridges

### Why This Team

Edgetributors is a decentralized collective of open-source builders, curators, and educators:

- Deep expertise in both Substrate runtime development and JavaScript/TypeScript SDK architecture.
- Maintainers of Substrate-related infrastructure projects (e.g., Universal Hybrid Faucet).
- Ongoing development of AgentDot, A TypeScript/Next.js application integrating OpenAI with Polkadot's polkadot-api to provide a natural language interface for executing blockchain transactions, staking operations, and cross-chain transfers across the Polkadot ecosystem.
- Active governance participation in Polkadot's community and on-chain decision-making.
- Organizers of multiple Polkadot India Workshops at top Universities across India.
- Organizers of the AssetHub Hackathon and representer of Polkadot at ETHIndia 2024.

We see x402 Substrate adoption as critical infrastructure for the next wave of Web3 developer tools and are committed to making it a substrate-native well-maintained standard.

---

## Project Details

### Technology Stack

**Client SDK (`x402-substrate-client`):**
- Language: TypeScript
- Core Dependencies:
  - `@polkadot/api` (chain interaction)
  - `@polkadot/keyring` (account signing)
  - `@polkadot/util` and `@polkadot/util-crypto` (encoding/crypto)
  - `node-fetch` (HTTP client)
  - `axios` (optional alternative HTTP client)
- No blockchain RPC calls by default; respects facilitator architecture
- Handles payment signing, transaction serialization, and HTTP header management

**Facilitator Service (`x402-substrate-facilitator`):**
- Language: TypeScript/Node.js
- Framework: Express.js
- Core Dependencies:
  - `@polkadot/api` (chain integration)
  - `@polkadot/keyring` (transaction signing)
  - Lightweight JSON RPC client for facilitator endpoint
- Features:
  - In-memory or SQLite transaction ledger for verification
  - Support for custom chain configs (testnet/mainnet)
  - Optional KYT/OFAC screening hooks (pluggable)
  - Prometheus metrics endpoints for monitoring

**Development & Testing:**
- Vitest for unit testing
- Docker for local Substrate node simulation
- GitHub Actions for CI/CD

### Core Components, Protocols & Architecture

#### 1. Client Library Architecture

```
┌─────────────────┐
│  User App       │
│  (Next.js, etc) │
└────────┬────────┘
         │
    ┌────▼────────────────────┐
    │ x402-substrate-client    │
    ├────────────────────────┤
    │ • PaymentHandler        │
    │ • TransactionBuilder    │
    │ • HeaderManager         │
    │ • AccountSigner         │
    └────┬───────────┬────────┘
         │           │
    HTTP 402    Substrate
    Response    Signing
         │           │
    ┌────▼───────────▼────┐
    │  Server / Blockchain │
    │  (via Facilitator)   │
    └─────────────────────┘
```

**Core Classes:**
- `X402Client`: Main entry point, configuration management
- `PaymentHandler`: Processes 402 responses, parses payment requirements
- `TransactionBuilder`: Constructs unsigned extrinsics for payment
- `AccountSigner`: Signs transactions using Substrate keyring
- `HeaderManager`: Encodes/decodes X-PAYMENT and X-PAYMENT-RESPONSE headers

**Payment Flow:**
1. User calls API endpoint without payment
2. Server responds with `402 Payment Required` + `X-PAYMENT-REQUIRED` header containing:
   ```json
   {
     "recipient": "5FHneA46xotXSfzQmKKJ2MEYAqQVzkpbRm2V8xXwXvHm",
     "amount": "1000000", // 1 DOT in Planck
     "chain": "PolkadotAssetHub",
     "timeout": 60
   }
   ```
3. Client builds unsigned extrinsic: `system.remark` + metadata
4. Client signs extrinsic with user's private key
5. Client retries API with `X-PAYMENT` header (base64-encoded signed extrinsic)
6. Server validates via Facilitator and responds with `200 OK`

#### 2. Facilitator Architecture

```
┌──────────────────────┐
│  Multiple Servers    │
│  (Payment consumers) │
└──────────┬───────────┘
           │
    ┌──────▼────────────────────┐
    │  x402 Facilitator Service  │
    ├───────────────────────────┤
    │ REST API (:3000)           │
    │ • /verify (payment check)  │
    │ • /settle (on-chain tx)    │
    │ • /supported (networks)    │
    │ • /health (status)         │
    │                            │
    │ Internal:                  │
    │ • TxLedger (verification)  │
    │ • ChainAdapter (multi-chain)
    │ • KeyManager (signing key) │
    └──────────┬─────────────────┘
               │
         ┌─────▼──────┐
         │ Substrate  │
         │ RPC Nodes  │
         │ (via API)  │
         └────────────┘
```

**Facilitator Responsibilities:**

**Verification (`/verify` endpoint):**
- Decode and validate X-PAYMENT header
- Extract extrinsic and check signature validity
- Verify nonce matches current chain state
- Return `{valid: true/false, txHash?: string}`

**Settlement (`/settle` endpoint):**
- Accept verified extrinsic
- Submit to chosen Substrate chain (Polkadot, Kusama, parachain)
- Monitor finality (wait for block confirmation)
- Record in ledger and respond with `{txHash, confirmed: true/false}`

**Facilitator Storage & Idempotency:**
- Maintain SQLite ledger: `{extrinsicHash, serverAddress, clientAddress, amount, chain, status, confirmedAt}`
- Prevent double-settlement through idempotent `/settle` calls
- Optional webhook support for async settlement notifications

#### 3. On-Chain Integration (Substrate Runtime)

**No custom pallet required.** Settlements use standard Substrate calls:

- **Direct token transfer**: `pallet_balances::transfer`
- **Custom token transfer**: `pallet_assets::transfer`
- **Optional memo storage**: `system::remark` extrinsic (for audit trail)

**Facilitator Runtime Config:**
- Runs as standalone service external to chain
- Uses Substrate RPC (`system_submitExtrinsic`, `system_getAccountInfo`) for verification
- Does NOT require new pallet code or governance approval
- Chainagnostic: same facilitator can settle across the common-good & commercial parachains of Paseo/Polkadot/Kusama.

### PoC / Prior Work

**Edgetributors x402 Research:**
- Studied x402 v2 spec and identified gaps for non-EVM chains
- Designed initial proof-of-concept facilitator to be developed in Rust (x402.rs)
- Evaluated Solana x402 and Aptos x402 implementations as reference

**Reference Implementations Analyzed:**
- Coinbase x402 SDK (EVM-focused)
- Aptos x402 and Solana x402 implementations (corbits, Faremeter)
- PayAI facilitator (multi-chain but EVM-dominant)

### Mockups / UI Designs

**Client SDK Usage Example:**
```typescript
import { X402Client } from '@x402/substrate-client';

const client = new X402Client({
  chain: 'PolkadotAssetHub',
  facilitatorUrl: 'https://facilitator.example.com',
  account: keypair // from @polkadot/keyring
});

// Automatic 402 handling
const data = await client.fetch('https://api.example.com/premium', {
  method: 'GET'
});
// If 402 received: client signs, retries automatically
// If 200 OK: data returned
```

**Facilitator API Docs / OpenAPI Spec:**
- HTTP 200: `{valid: true, txHash: "0x..."}`
- HTTP 400: `{valid: false, reason: "invalid_signature"}`
- HTTP 500: `{error: "failed_to_settle"}`

No custom UI required—operates entirely via HTTP headers and REST endpoints.

### Data Models / API Specifications

#### X-PAYMENT-REQUIRED Header (Server → Client)

```json
{
  "recipient": "5FHneA46xotXSfzQmKKJ2MEYAqQVzkpbRm2V8xXwXvHm",
  "amount": "1000000",
  "chain": "PolkadotAssetHub",
  "timeout": 60,
  "version": 1,
  "scheme": "exact",
  "token": "DOT" // optional, defaults to native
}
```

#### X-PAYMENT Header (Client → Server)

Base64-encoded signed extrinsic:
```
X-PAYMENT: base64(signedExtrinsic)
```

#### Facilitator API Schema

**POST /verify**
```json
Request:
{
  "extrinsic": "0x...",
  "chain": "PolkadotAssetHub",
  "recipient": "5F...",
  "amount": "1000000",
  "nonce": 42
}

Response:
{
  "valid": true,
  "signature_valid": true,
  "nonce_valid": true,
  "account_exists": true,
  "balance_sufficient": true
}
```

**POST /settle**
```json
Request:
{
  "extrinsic": "0x...",
  "chain": "PolkadotAssetHub",
  "serverAddress": "5F..."
}

Response:
{
  "txHash": "0x...",
  "status": "pending|confirmed",
  "blockNumber": 12345,
  "error": null
}
```

### What This Project Is NOT

- **Not a pallet or runtime upgrade**: No governance approval needed; operates via off-chain facilitator
- **Not a wallet**: Does not manage user keys; integrates with existing Substrate wallets (SubWallet, Talisman, Polkadot.js)
- **Not a gateway**: Not a centralized payment processor; facilitator is deployable and open-source
- **Not tied to DOT**: Supports any Substrate-based chain's native or custom tokens
- **Not replacing XCM**: Complements cross-chain messaging; does not alter Polkadot's consensus or security
- **No frame/pallet dependency**: Designed as pure off-chain infrastructure
- **No compliance/AML built-in**: Optional hooks for KYT/OFAC, but primary focus is protocol; compliance is server's responsibility
- **No subscription management**: Transactional only; recurring payments require server-side logic

---

## Ecosystem Fit

### Where & How This Project Fits

**Gap Being Filled:**

x402 is rapidly becoming the native payment protocol for the internet:
- Solana: 500,000+ weekly transactions (October 2025)
- EVM chains: Growing adoption via Base facilitator
- **Substrate/Polkadot: Zero native support**

This proposal closes that gap by bringing HTTP 402 payments to Substrate chains, unlocking:

1. **For Parachains**: Native monetization of APIs without relying on EVM bridges or centralized payment processors
2. **For dApp Developers**: Add payment gates to Dapps (data feeds, compute, premium features) with one SDK
3. **For Wallets & Tools**: Extend UX to support x402 payment flows natively
4. **For AI Agents**: Enable autonomous transactions on Polkadot at scale (as seen on Solana)
5. **For Builders in India & Asia**: Make Relay (protocol), chains like AssetHub, Hydration, Bifrost, and other Polkadot parachains viable for micropayment use cases

### Target Audience

- **Parachain Developers**: Build APIs monetized via x402
- **dApp Developers**: Integrate payments into Dapps (games, data platforms, premium services)
- **Wallet & Infrastructure Providers**: Add x402 support to Substrate wallets
- **AI Agent Builders**: Access Polkadot ecosystem data/compute through autonomous payments
- **Relay / Community Relay Users**: Enable peer-to-peer micropayments on Polkadot

### Needs Being Met

1. **Micropayment Infrastructure**: Current solutions (Stripe, PayPal) charge 2.9% + $0.30/tx, making sub-$1 transactions uneconomical. x402 enables true micropayments (¢1–$100 range).

2. **Chain-Native Payments**: Existing x402 implementations assume EVM (EIP-3009 transfers). Substrate has different account models, cryptography (SR25519 vs ECDSA), and extrinsic formats. This SDK enables Substrate-native payments without EVM compatibility layer.

3. **Facilitator Decentralization**: Coinbase's facilitator dominates x402 on EVM. Substrate implementation must allow anyone to run an independent facilitator, respecting Polkadot's decentralization values.

4. **Zero-Fee Protocol**: Eliminates payment processor rent-seeking; aligns with Polkadot's ethos of democratized infrastructure.

### Evidence of Need

**Solana Adoption Metrics** (as of October 2025):
- x402 transactions grew 10,000% in one month
- 500,000+ weekly transactions
- Ecosystem market cap: $810M+ (per CoinGecko x402 category)

**Polkadot Community Signal:**
- Forum discussions on payment infrastructure as gap in SDK
- Relay product demand (Polkadot-native community payments)

**Cross-Ecosystem Research:**
- Aptos x402 implementation (Move-based, similar VM challenges to Substrate)
- Solana x402 success (proof x402 works for high-throughput chains)
- x402 Foundation formation (September 2025) signals protocol maturity and multi-chain intention

### Similar Projects in Polkadot/Kusama Ecosystem

**None** currently exist. Polkadot ecosystem payment infrastructure is fragmented:

| Project | Purpose | Gap vs x402 Substrate |
|---------|---------|----------------------|
| Relay (MontaQ Labs) | Community fundraising, P2P payments | Limited to Polkadot, no HTTP 402 standard |
| Equilibrium | Synthetic assets & staking | Not micropayment-focused; no API monetization |
| PolkaEx / Zenlink | DEX aggregators | Swap execution only, not API payments |
| Stable.bonds | Stablecoins | Currency layer, not payment protocol |

**Why No Prior Attempt:**

1. **Timing**: x402 itself only reached maturity in 2024–2025; Polkadot SDK stabilization came later
2. **Complexity**: Substrate account model (SR25519, multi-sig support) differs from EVM; requires custom extrinsic builder
3. **Network Effects**: x402 was proving itself on Solana/EVM first; Substrate effort would have been premature
4. **Leadership Gap**: Needed Substrate protocol knowledge + x402 spec expertise (rare combination)

### Similar Projects in Related Ecosystems

| Ecosystem | Project | Status | Relevance |
|-----------|---------|--------|-----------|
| Solana | corbits, Faremeter | Production | Reference implementations for Solana VMs |
| Aptos | x402 early adopters | Early | Move VM + x402 integration |
| TON | ton-http-payment-channel | Experimental | Alternative HTTP payment model |
| Cosmos | IBC payment middleware | Proposed | IBC analogue to x402 XCM bridge |

Our approach builds on these precedents while respecting Substrate's unique architecture (XCM, multi-chain composability, forkless upgrades).

---

## Team

### Team Name
**Edgetributors** (Blockchain Infrastructure & Developer Tools)

### Contact
- **Contact Name**: Shankar Warang
- **Contact Email**: shankar@edgeware.community
- **Website**: https://edgetributors.xyz/
- **GitHub Org**: https://github.com/edgeware-network

### Team Members

**Core Contributors:**

1. **Shankar Warang: Solution Architect** (Lead)
   - 5+ years working exclusively with Substrate/PolkadotSDK, 8+ years of web3 experience
   - GitHub: https://github.com/ShankarWarang
   - LinkedIn: https://www.linkedin.com/in/shankar-warang/

2. **Raj Raorane: Fullstack Developer**
   - PBA Graduate, AgentDOT core developer, 4+ years experience working on Substrate/PolkadotSDK
   - GitHub: https://github.com/Raj-RR1
   - LinkedIn: https://www.linkedin.com/in/raj-raorane-45b2b4166/

4. **Rama Jha: Lead Designer and Frontend Developer**
   - 4+ year frontend developer experience. Advanced on React, Next.js, Typescript
   - GitHub: https://github.com/ramavats
   - LinkedIn: https://www.linkedin.com/in/rama-jha/

### Team Code Repos

- Main org: https://github.com/edgeware-network
- Relay (production payment product for cross-integration): https://github.com/montaq-labs/relay

### Team Experience

Edgetributors is a collective of long-time contributors (5+ years) in the Polkadot ecosystem with 3–4 years of experience building and maintaining public goods and developer infrastructure within the Substrate framework. The team recently developed AgentDOT, an automation layer to streamline coordination and contributor workflows, and previously built the Universal Hybrid Substrate Faucet, a treasury-funded project enabling seamless multi-network token distribution.
Edgetributors has also led multiple Polkadot India workshop series at premier institutions such as IIT Bombay, IIT Roorkee, MIT, and NITK, helping onboard students and developers into the Substrate and Polkadot ecosystem. Well known for hosting the successful AssetHub hackathon and representing Polkadot in ETHIndia 2024!

---

## Development Status

### Prior Work & Research

1. **x402 Protocol Analysis** (Oct-Nov 2025):
   - Read Coinbase x402 spec, GitHub repo, v2 proposal
   - Analyzed Solana x402 implementations (corbits, Faremeter, native examples)
   - Identified Substrate-specific gaps (extrinsic format, account model, crypto)
   - Published technical writeup: "x402 for Non-EVM Chains" (internal)

2. **Proof-of-Concept Facilitator roadmap** (Nov 2025):
   - Designed the architecture of minimal facilitator to be developed in Rust (x402.rs fork)
   - Evaluated testing feasibility against Paseo testnet
   - Verified signature validation flow works with Substrate accounts
   - Confirmed zero new pallet code required


### Blog Posts & Articles to be posted

- "Why Polkadot Needs HTTP 402" - internal research doc, planned for Month 1
- "x402 Protocol Deep Dive: Solana Success & EVM Limitations" — planned for Month 2
- "Building x402 SDK for Substrate"  implementation diary, public GitHub wiki, planned for Month 3


### Research

- Reference implementations tracked: corbits, CDP SDK, PayAI facilitator

---

## Development Roadmap

### Overview

- **Estimated Duration**: 4 months
- **Full-Time Equivalent (FTE)**: 0.9 FTE (0.4 × full stack engineer, 0.4 × JavaScript engineer + 0.1 × operations & architecture)
- **Total Costs**: 29040 USD {(160 hours per month * 4 months * 0.9 FTE * 50 USD per hour) + (60 USD per month VPS * 4 months)}

### Milestone 1: Client SDK & Core Facilitator (8 weeks)

**Deliverables:**

| # | Deliverable | Specification |
|---|---|---|
| 0a | License | MIT License (permissive, aligns with Polkadot SDK licensing) |
| 0b | Documentation | (1) Inline code documentation (JSDoc format, 80% coverage). (2) Beginner's tutorial: "Build Your First x402 API" (markdown, 1000 words). (3) API reference auto-generated from TypeScript types. (4) Architecture guide explaining facilitator design. |
| 0c | Testing & Guide | Vitest unit tests: 90%+ coverage for core payment flow (signature validation, header encoding, transaction building). Integration tests: 3 scenarios (happy path, invalid signature, server rejection). Testing guide in README with `npm test` commands. |
| 0d | Docker | Dockerfile for x402-substrate-facilitator service; docker-compose.yml spinning up Substrate testnet + facilitator. Works with `docker-compose up` for local testing. |
| 0e | Article | "x402 SDK for Substrate: Bridging Micropayments to Polkadot" — 2000-word blog post explaining protocol, implementation choices, comparison to EVM x402. Published on Edgetributors blog and cross-posted to Polkadot forum. |
| 1 | x402-substrate-client Library | TypeScript library (`@x402/substrate-client`). Features: (1) PaymentHandler class; auto-detect 402 responses. (2) TransactionBuilder: construct unsigned extrinsics from payment requirements. (3) AccountSigner: sign extrinsic with Substrate keypair. (4) HeaderManager: encode/decode X-PAYMENT headers (base64). (5) Support for multiple chains (Polkadot, Kusama, parachains) via chainConfig. (6) Zero external blockchain calls (verifies via facilitator only). Exports: Named exports (PaymentHandler, TransactionBuilder) + default export (X402Client). Published to npm: `npm install @x402/substrate-client`. |
| 2 | x402-substrate-facilitator Service | Node.js/Express service. Features: (1) `/verify` endpoint: validate X-PAYMENT extrinsic (signature, nonce, balance). (2) `/settle` endpoint: submit extrinsic to Substrate chain + wait for finality. (3) `/supported` endpoint: list supported chains/tokens. (4) TxLedger: SQLite table tracking {extrinsicHash, status, confirmedAt}. (5) ChainAdapter: abstract over Polkadot, Kusama, parachains. (6) Error handling & logging. (7) Optional KYT hook stub (no OFAC checks, but interface ready for integration). Starts on http://localhost:3000 by default. Health check at `/health`. Docker-ready. GitHub repo: https://github.com/montaq-labs/x402-substrate-facilitator. |
| 3 | Full Integrations Tests | End-to-end scenario: Client requests protected API → Server returns 402 → Client signs extrinsic → Client calls /verify + /settle on facilitator → Extrinsic submitted to local testnet → Block confirmation → Server grants access. Runs in CI via GitHub Actions (Vitest + Docker). |
| 4 | GitHub Repositories & README | 2 repositories created: (1) `@x402/substrate-client` (npm package). (2) `x402-substrate-facilitator` (service). Both with comprehensive README (setup, usage, architecture, roadmap). MIT license headers on all files. CONTRIBUTING.md for community contributors. |

**Success Criteria:**
- Client SDK: Passes all unit tests, parses x402 headers correctly, signs extrinsics with valid Substrate keypair
- Facilitator: Validates signatures against local Polkadot testnet, submits extrinsics, confirms in block, ledger records all txs
- Documentation: Beginner can clone repo, run `npm install && npm test`, and integrate client SDK into Next.js app in <30 min
- Tests: 90%+ code coverage, all scenarios pass (happy path, invalid sig, network error, timeout)

**Timeline:** Weeks 1–8

---

### Milestone 2: Multi-Chain Support & Production Hardening (8 weeks)

**Deliverables:**

| # | Deliverable | Specification |
|---|---|---|
| 0a | License | MIT License (maintained from M1) |
| 0b | Documentation | (1) Multi-chain setup guide (Common-good & commercial parachains of Paseo/Polkadot/Kusama). (2) "Running Your Own Facilitator" guide (deployment to VPS, Docker, systemd). (3) Token support guide (native + pallet-assets). (4) Troubleshooting FAQ (10+ common issues). (5) Security considerations doc (key management, signature validation, nonce attacks). |
| 0c | Testing & Guide | Integration tests on live testnets (Polkadot testnet, Kusama testnet). Stress test facilitator: 100 concurrent /verify calls, 50 /settle calls. Load test: latency <500ms for /verify, <2s for /settle. Guide: `npm run test:integration` + testnet setup instructions. |
| 0d | Docker | Enhanced Dockerfile with multi-stage build (small image). docker-compose with Polkadot testnet + facilitator + mock server. Support for `CHAIN_RPC_ENDPOINT` env variable for custom chain. |
| 0e | Article | "Deploying x402 Facilitators on Polkadot: A Community Guide" — 1500-word guide for operators running their own facilitators. Covers security, compliance hooks, monitoring, economics. Published to Polkadot forum + MontaQ blog. |
| 5 | Multi-Chain Support | ChainAdapter extended to support: (1) Paseo common-good & commercial parachains. (2) Polkadot common-good & commercial parachains. (3) Kusama common-good & commercial parachains. (4) Custom chain configs via JSON. Client SDK: specify chain in config: `new X402Client({chain: 'PolkadotAssetHub'})`. Facilitator: environment variable `CHAIN_RPC_ENDPOINT=wss://polkadot-asset-hub-rpc.polkadot.io` selects chain. All chains tested with live e2e test suite. |
| 6 | Token Support | (1) Native tokens (DOT, KSM, MOVR, etc.) — default settlement method. (2) Custom tokens via pallet-assets — ForeignAsset settlement for cross-chain transfers. (3) Client SDK: specify token in payment requirements: `{token: "AUSD", amount: ...}`. Facilitator: validates token exists on-chain before settle. Tests: transfer native DOT, transfer pallet-assets token, reject unknown token. |
| 7 | Facilitator Monitoring & Ops | (1) Prometheus metrics: request counts, latency p50/p95/p99, settlement success rate, ledger size. (2) Health check endpoint: `/health` returns {status, uptime, ledgerSize, recentErrors}. (3) Structured logging (Winston): all transactions logged for audit trail. (4) Optional webhook support: facilitator calls server webhook on settlement confirmation (async notification). (5) Admin endpoint (gated by API key): `/admin/ledger` to query settlement history. |
| 8 | Security Hardening | (1) Extrinsic signature validation: full SR25519 verification. (2) Nonce replay attack prevention: track nonces per account per chain. (3) Balance validation: check account has funds before settle (prevent pending tx spam). (4) Rate limiting: facilitate max 1000 /verify reqs/min per client IP. (5) Optional KYT hook implementation stub (no-op by default, but pluggable for integrations). (6) Security audit checklist + findings documented. |
| 9 | Community Examples & Templates | (1) Next.js example: Protected API route using x402 client SDK. (2) Express example: API server using x402 facilitator middleware. (3) React Hook example: `useX402Payment()` for UI integration. (4) Polkadot.js example: wallet integration. All examples in separate `examples/` directory, runnable with `npm install && npm start`. |
| 10 | Roadmap & Handoff | (1) Public roadmap: "Phase 2" features (XCM integration, EVM bridges, subscription model). (2) Community maintenance guide: how to onboard new chain adapters, report bugs. (3) Handoff package: all repos transferred to community/governance structure (GitHub org or DAO if applicable). (4) Post-grant support commitment: 4-week bug fix window (critical issues only). |

**Success Criteria:**
- Multi-chain: SDK works seamlessly with common-good & commercial parachains of Paseo/Polkadot/Kusama (verified via e2e tests on live testnet)
- Token support: Native + pallet-assets transfers working; reject invalid tokens gracefully
- Monitoring: Prometheus metrics scraped; health endpoint returns correct status; logs are parseable
- Security: Nonce replay prevented; signature validation rejects forged txs; rate limiting enforced
- Examples: Developer can clone example, `npm install`, `npm start`, and have working x402 payment flow in <5 min
- Community: README explains how to add new chains; contribution guidelines clear; 1st external PR expected within 2 weeks of grant completion

**Timeline:** Weeks 9–16

---

## Budget Breakdown

| Category | Item | Cost (USD) | FTE/Amount | Total (USD) | Description |
|----------|------|-----------|-----------|-----------|-------------|
| **Personnel** | Fullstack Engineer (Lead) | $3200/mo | 0.4 FTE (4 months) | $12800 | Full stack Substrate + x402 development; architecture, SDK design, facilitator implementation, security audit |
| **Personnel** | JavaScript/Node.js Engineer | $3200/mo | 0.4 FTE (4 months) | $12800 | Client SDK polish, Express service, testing, examples, npm publishing |
| **Personnel** | DevRel / Community Support | $800/mo | 0.1 FTE (4 months) | $3200 | Documentation, blog posts, forum engagement, community feedback loops, GitHub issues triage |
| **Equipment** | Dedicated VPS for testnet facilitator | $60/mo | 4 months | $240 | Stable environment for e2e testing and public examples |
| **Subcontracts** | (None budgeted) | — | — | — | Team has internal expertise; no external audits or contractors needed for this phase |
| | | | | **TOTAL** | **$29040** |

**Cost Justification:**

- **Fullstack Engineer (0.4 FTE)**: Substrate protocol expertise, extrinsic building, cryptography, chain integration. Market rate for senior blockchain engineer in India: $6,000–$10,000/mo; using $3200 reflects ecosystem-first approach and open-source contribution commitment.
- **JavaScript Engineer (0.4 FTE)**: Polkadot.js library integration, SDK polish, testing framework setup. Market rate: $5,000–$7,000/mo; using $3200 reflects ecosystem-first approach and open-source contribution commitment.
- **DevRel (0.1 FTE)**: Documentation, blog content, community management, GitHub maintenance. Market rate: $3,000–$5,000/mo; using $800 reflects community focus and internal rotation.
- **VPS**: AWS EC2 or Hetzner equivalent; $60/mo for stable testnet facilitator hosting during development + post-grant.

**Total Project Cost: $29040 USD**

---

## Future Plans

### Long-Term Maintenance & Funding

1. **Community Governance**: Transfer repos to Polkadot Foundation or community DAO after M2 completion (6+ months); establish community council for feature decisions.

2. **Facilitator Network Economics**:
   - Each facilitator operator retains 100% of settlement fees (protocol fee: 0%)
   - Incentivize decentralization: facilitate public registry of facilitators + uptime SLAs
   - Long-term: optional fee-sharing model if ecosystem wants to fund maintenance

3. **Funding Sources**:
   - Polkadot Open Source Grants (this proposal)
   - Potential follow-up grant for Phase 2 features (XCM settlements, advanced integrations)
   - Community crowdfunding via Relay (Polkadot community fundraising platform)
   - Revenue from commercial facilitator deployment (optional, not mandatory)

### Short-Term Enhancement & Promotion (0–6 months)

1. **Marketing & Adoption**:
   - Launch blog series: "x402 SDK for Substrate" (3 articles covering SDK, facilitator ops, use cases)
   - Host 2 virtual workshops (1 SDK intro, 1 facilitator setup) on Polkadot community spaces
   - Create 3-minute demo video: "Monetize Your API with x402"
   - Publish on Polkadot Forum as sticky post in #dev-general

2. **SDK Enhancements**:
   - Add Polkadot.js wallet extension integration (auto-detect MetaMask-like extension)
   - React hook: `useX402Payment()` for common UI patterns
   - CLI tool: `x402-cli` for testing facilitators without code

3. **Ecosystem Partnerships**:
   - Approach wallets (SubWallet, Talisman) for native x402 support
   - Contact 3+ parachain projects for beta integration
   - Offer free facilitator hosting to early partners (first 3 months)

### Long-Term Vision (6–24 months, not part of the current scope)

1. **Phase 2: XCM Settlement**:
   - Extend facilitator to settle payments directly via XCM (cross-chain)
   - Example: Hydration dApp charges in USDT, settled to treasury on Polkadot AssetHub in DOT
   - New pallet (optional): `pallet-x402` for on-chain fee distribution

2. **Phase 3: EVM Bridges**:
   - Add EVM-to-Substrate bridge layer (pay in USDC on Moonbeam → settle in DOT on Polkadot AssetHub)
   - Connect to existing x402 EVM ecosystem (Coinbase CDP, Base)

3. **Phase 4: Subscription & Advanced Models**:
   - Extend x402 beyond "exact" scheme: support "upto," "subscription," "time-locked" payment models
   - Enable complex pricing (tiered, usage-based, dynamic)

4. **Maintenance & Standards**:
   - Join x402 Foundation governance (if Substrate-specific seat available)
   - Contribute improvements back to x402 spec (document Substrate-specific extensions)
   - Annual security audit (community-funded)

---

### Community Validation (Ongoing/planned):
   - Interest intent collection from the parachains teams
   - Wallet teams integration readiness feedback collection
   - Polkadot India Telegram: Collection of interest from the community members requesting Polkadot x402

### Other Funding & Contributors

- **No prior funding** for this specific project (x402 Substrate SDK is new)
- **No competing submissions**: First Polkadot grant application for x402 SDK

### Prior Grants & Declarations

- **Edgetributors**: No prior Polkadot Open Source grants (first-time applicant but did many contributions to different bounties and OpenGov.)
- **Team members**: No conflicting grants for related projects.
- **Full transparency**: Will disclose all grant details to community; no exclusivity clauses requested.

### Commitment to Open Source

- All code: MIT License (permissive)
- All repositories: Public GitHub under montaq-labs org (or transferred to Polkadot Foundation post-grant)
- All documentation: Published CC-BY-4.0 (reusable by others)
- 4-week post-grant bug fix commitment (after delivery)
- Long-term: Aim for community governance model by end of 2026

---

## Appendix: Technical Rationale for Design Decisions

### Why No Custom Pallet?

**Substrate Runtime Impact:**
- Custom pallet requires governance approval (referendum)
- Increases network complexity; x402 is optional infrastructure
- Most x402 logic is facilitator-side verification, not consensus-critical

**Our Approach:**
- Settlement uses standard `pallet_balances::transfer` or `pallet_assets::transfer`
- Verification happens off-chain via facilitator
- Works immediately on Polkadot mainnet (no waiting for pallet governance)

### Why JavaScript/TypeScript (Not Rust)?

**SDK Target Audience:**
- Web developers, dApp builders, API developers
- Most familiar with JavaScript; lower barrier to entry than Rust
- Ecosystem: polkadot.js already TypeScript; Ethers.js reference for EVM

**Facilitator Justification:**
- Can be written in Node.js (TypeScript); Rust optional in Phase 2
- Easier onboarding for community contributors
- HTTP-based design: performance bottleneck is RPC latency, not language

### Why Not Use Existing x402 Implementations?

**Coinbase x402 SDK** (EVM-specific):
- Built for EVM (Keccak256 hashing, secp256k1 signatures, EIP-3009 transferWithAuthorization)
- Substrate uses Blake2b, SR25519, different extrinsic format
- Cannot reuse without complete rewrite; custom build is cleaner

**corbits / Faremeter** (Solana):
- Solana-specific; uses Solana key derivation, instruction format
- Similar situation: too Solana-specific to fork; our build is better

**Takeaway:** Custom Substrate SDK is necessary, without a need for new pallet and thus making thid development permissionless to implement; we're not reinventing wheels, we're adapting a industry-wide accepted/adimired protocol for our Polkadot ecosystem.

---

**End of Proposal**

*For questions, contact: shankar@edgeware.community*
