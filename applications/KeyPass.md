# KeyPass: Self-Sovereign Login Toolkit for Polkadot

## Project Overview

**Tagline (one-sentence summary):**  
KeyPass provides a Polkadot-native login SDK with decentralized identity and credentials, replacing “Sign in with Google” with a wallet-first, privacy-preserving system.  

**Brief description of the project:**  
KeyPass makes it easy for developers to add **self-sovereign login** to their Polkadot dApps. Users authenticate with their wallets instead of centralized providers, and can manage identity-bound credentials such as “student” or “DAO member.” These credentials are built using **DIDs (via KILT Protocol)**, **Soulbound Tokens (SBTs)**, and **Ink! smart contracts** for revocation and lifecycle management.  

**How this project integrates into Polkadot:**  
- **Wallet-first login**: Talisman, Polkadot.js, Nova, SubWallet, Ledger.  
- **Identity**: DID issuance and resolution via KILT Protocol.  
- **Credentials**: Ink! smart contracts for SBT issuance, revocation, expiration.  
- **Adoption**: Integration toolkit with UI widgets, sample repos, and onboarding wizard.  

**Why I’m building this:**  
Identity and login are bottlenecks for onboarding to Web3. I want Polkadot to be the ecosystem that solves this — with a simple, reusable SDK that any project can adopt, without forcing users to give up control of their data.  

---

## Project Details

### Technology Stack

- **Authentication**: Current MVP implements Ethereum-style wallet authentication using `personal_sign` with an **EIP-4361-inspired message format**. As part of this grant, I will extend the SDK to support **multi-wallet login** for Polkadot.js, SubWallet, Nova, and Ledger, and align message formats with best practices.  

- **Frontend**: The MVP is built with **React (Vite + Tailwind)**. This stack will be maintained, with additional example apps and UI components added for easier integration.  

- **Identity**: The MVP includes a **custom lightweight DID layer**. This grant will add **KILT Protocol integration** for DID issuance and resolution, while maintaining compatibility with existing flows.  

- **Contracts**: The MVP does not yet include any contracts. As part of this grant, I will implement **new Ink! smart contracts** for credential issuance, expiration, and revocation.  

- **Privacy**: Future-ready design that can support zk-proof templates (e.g., age verification, DAO membership) as optional extensions, though this is not in current scope.  

### Core Components & Architecture
1. **SDK v2**  
   - Multi-wallet login support (Polkadot.js, Nova, SubWallet, Ledger).  
   - React/Vue components for developers to drop into apps.  

2. **Credential Lifecycle Manager**  
   - Issue, revoke, and update identity-bound credentials (SBTs).  
   - Simple web dashboard to manage credentials.  
   - Integrates with KILT Protocol for DID issuance/resolution.  

3. **Ink! Smart Contracts**  
   - On-chain rules for SBT issuance, expiration, and revocation.  
   - Tested and deployed to a Substrate-based chain.  

4. **Integration Simplification Toolkit**  
   - Drop-in UI widgets for “Login with Polkadot” and “Credential Badge.”  
   - Example repos for common use cases (DAO membership gating, student verification, age restriction).  
   - CLI integration wizard that guides developers through setup.  
   - Quickstart docs and troubleshooting based on community feedback.  

### What the Project is *Not*
- Not a Web2 login (no email/password support).  
- Not a credential marketplace or social network.  
- Not reliant on external partners for adoption — all milestones are self-contained.  

---

## Ecosystem Fit

**Where and how does your project fit into the ecosystem?**  
KeyPass is identity middleware for Polkadot. It enables dApps, DAOs, and learning platforms to use wallet-first login and on-chain credentials without reinventing identity infrastructure.  

**Target Audience**  
- Polkadot dApp developers  
- DAO and community platforms  
- Hackathon and education platforms  

**Needs Met**  
- Removes reliance on Big Tech logins (Google, Facebook, GitHub, etc).  
- Provides easy SDK for Polkadot-native login.  
- Simplifies integration to boost adoption.  

**How I identified these needs**  
- Ethereum’s SIWE has proven strong adoption, but Polkadot lacks an equivalent.  
- Developer conversations show friction in onboarding users without Web2 accounts.  
- Feedback from early testers showed that integration complexity was a barrier, motivating the Integration Toolkit.  

**Similar Projects in Polkadot/Kusama**  
- **KILT Protocol** → focused on credential issuance. KeyPass complements it by providing a **login-first SDK + credential lifecycle manager**.  
- **Dock** → also credential-focused, less Polkadot-native.  

**Similar Projects in Other Ecosystems**  
- **SIWE (Ethereum)** → login standard, but no built-in credential lifecycle or integration toolkit.  
- **Gitcoin Passport** → focuses on reputation/anti-Sybil, not general-purpose login.  

---

## Team

- **Team Name:** KeyPass Labs  
- **Contact Name:** Uliana Zavalova  
- **Contact Email:** zawulyana@gmail.com  
- **Website/GitHub:** [https://github.com/uliana1one/keypass](https://github.com/uliana1one/keypass)  

**Team Members**  
- Uliana Zavalova – Lead Developer, Product Architect  

**LinkedIn:** [Uliana Zavalova](https://www.linkedin.com/in/uliana-one/)

**Experience**  
- Delivered KeyPass MVP with a Polkadot Fast Grant.  
- NearAI useful agents hackathon prize winner.  
- Research experience (writing software) at Harvard Lab for Computational Cognitive Development.  

---

## Development Status

- Completed MVP: Polkadot login SDK prototype, DID explorer, zk-proof demo.  
- Public repo with code, demo site, and docs: [GitHub](https://github.com/uliana1one/keypass).
- Live demo: https://keypass-react-demo.vercel.app

---

## Development Roadmap

### Overview
- **Estimated Duration:** 3 months  
- **FTE:** 1.0 = 1 developer working full-time for 3 months 
- **Total Costs:** $30,000 USD  

### Milestone 1
| Number | Deliverable | Specification |
| ------ | ----------- | ------------- |
| 0a | License | MIT |
| 0b | Documentation | Inline docs + tutorial for login integration |
| 0c | Testing & Guide | Unit + integration tests, guide for running them |
| 0d | Docker | Dockerfile to spin up SDK demo locally |
| 0e | Article | Publish article on Polkadot Forum + Medium explaining SDK v2 |
| 1 | SDK v2 with Multi-Wallet Support | Support Polkadot.js, SubWallet, Nova, Ledger + React/Vue UI components |

**Expected Outcome for Milestone 1**  
Developers can log in to a demo app using multiple Polkadot wallets, and see a working integration flow with documentation.  

---

### Milestone 2
| Number | Deliverable | Specification |
| ------ | ----------- | ------------- |
| 2 | Credential Lifecycle Manager | Issue, revoke, update credentials via DID + SBTs; UI dashboard for users |
| 3 | Ink! Smart Contracts | Substrate-native contracts for SBT issuance and revocation |
| 4 | Integration Simplification Toolkit | Drop-in UI widgets, sample repos, CLI wizard, enhanced docs for easy adoption |

**Expected Outcome for Milestone 2**  
Users can create, revoke, and update credentials through the Credential Manager, backed by Ink! contracts. Developers can integrate KeyPass in minutes using drop-in widgets, sample repos, and the CLI wizard.  

---

## Budget Breakdown

| Category        | Item                          | Total Cost | Description |
|-----------------|-------------------------------|-----------:|-------------|
| Personnel       | SDK & Architecture Development| $15,000    | SDK v2, wallet integrations, React/Vue components |
| Personnel       | Smart Contract Development    | $11,000    | Ink! contracts for SBTs, revocation, expiration |
| Personnel       | Testing & Documentation       | $3,500     | Test suite, Docker, tutorials |
| Subscriptions & Services | Hosting & Dev Tools   | $500     | Demo hosting, CI/CD, Figma Pro, API monitoring |
| **Total**       |                               | **$30,000**|             |

---

## Future Plans

- Maintain SDK and contracts through CI/CD pipelines and open-source contributions.  
- Publish “KeyPass for Education” toolkit to onboard DAOs and student platforms.  
- Transition toward a **KeyPass DAO** for long-term governance of credential standards.  
- Seek follow-on grants from parachains (KILT, Moonbeam) or Web3 Foundation.  

---

## Additional Information

- MVP was already funded with $10,000 from Polkadot Fast Grants.  
- No other funding applications are active.  
- Live demo: [https://keypass-react-demo.vercel.app](https://keypass-react-demo.vercel.app)  
- Source code: [https://github.com/uliana1one/keypass](https://github.com/uliana1one/keypass)  
