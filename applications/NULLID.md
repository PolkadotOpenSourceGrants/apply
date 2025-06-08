# NULLID



- **Team Name:** NULLID TEAM

- **Payment Details:**
  - **DOT**: Polkadot address 14uiR7YeCsg9bq6AvLp13sBApwYBsuBSv59E7GwpnFCzHLfk

  - **Payment**:  **USDC** 14uiR7YeCsg9bq6AvLp13sBApwYBsuBSv59E7GwpnFCzHLfk

    
- **[Level](https://grants.web3.foundation/docs/Introduction/levels):** 1


## Project Overview :page_facing_up:

### Overview


NullID is a privacy-preserving, cross-platform identity verification system designed to help communities and organizations combat impersonation and scams. It uses zero-knowledge proofs to verify identities without revealing private data and anchors this verification onchain for transparency and trust.

Within the Polkadot ecosystem, NullID can serve as a trust layer for DAOs, projects, and parachains. By allowing users and contributors to link verified profiles (Telegram, GitHub, X, Discord, etc.) with onchain Polkadot addresses, NullID makes it easy to prove someone is who they say they are — whether they're joining a DAO, accessing contributor-only resources, or reaching out to someone.
NullID integrates with the Polkadot ecosystem through 3rd party/ custom protocol, smart contract APIs, and storage on decentralized networks like Arweave. It complements Substrate-based chains by providing secure identity links across the ecosystem.

### Project Details

1. UI Mockups/Designs
Clean, modern UI for web onboarding and  inline interactions.
Key screens include: Work email verification via OTP, zero-knowledge proof generation,  verified badge display.
Design prioritizes privacy, usability, and clear trust signals. 

2. Core Data Models & API Specifications
User: Identified by work email,  ID, and zero-knowledge proof attestations.
Proof: Contains verified attestation data (email, timestamp), secured with zero-knowledge proofs and anchored on-chain.
API: RESTful endpoints for OTP verification, proof generation/submission, and  bot interactions.
Smart Contract: Validates submitted proofs on a public blockchain integrated with Polkadot.

3. Technology Stack
Frontend: React (TypeScript), TailwindCSS, Next.js for landing pages, Vite for mini-apps.
Blockchain:  smart contracts with Polkadot ecosystem integration.
Zero-Knowledge Proofs: Utilizes Reclaim Protocol SDK (client-side proof generation).
Other Tools:  Bot API, ethers.js.

4. Architecture & Core Components
User Flow: User verifies work email via OTP → generates zero-knowledge proof → submits proof on-chain →  bot issues verified badge.
Components: Web onboarding, client-side ZK proof engine,  inline bot, Solidity smart contract for proof validation.
Protocols: Zero-knowledge proofs, REST API, blockchain transactions.

5. Proof of Concept / MVP
Live MVP deployed on testnet: users can verify emails, post proofs on-chain, and receive  badges.
bot and smart contract already operational.

6. Out of Scope / Limitations
No KYC/AML or government ID verification — verification limited to work emails.
No centralized data storage — privacy is a priority.
Does not include advanced anti-abuse or reputation management features at this stage.



### Ecosystem Fit

NullID brings privacy-first, on-chain identity verification to the Polkadot/Substrate/Kusama ecosystem. It leverages zero-knowledge proofs and blockchain smart contracts to allow users to prove their work email (and hence professional identity) without revealing private data. NullID can be integrated by, dapps, wallets, or any project needing privacy-preserving trust signals for users, especially in community/chat contexts.

Our primary users are Web3 communities, DAOs, and projects seeking secure and privacy-preserving identity verification solutions. Secondary users include parachain developers, dapp creators, wallet providers, and community managers who need to onboard users with verified credentials while minimizing scam risks and impersonation.

NullID addresses the critical problem of identity verification in decentralized communities, specifically:
Combatting scams and impersonations in messaging and coordination platforms used by Web3 projects.
Enabling privacy-preserving verification without exposing sensitive data publicly.
Providing a reusable, cross-platform identity layer that projects and users can trust.
Enhancing user onboarding with verifiable claims anchored on Polkadot’s secure infrastructure.

Identifying needs:
Empirical data from frequent scam and impersonation reports in Telegram and Discord communities within Polkadot and broader Web3 ecosystems.
Community feedback and developer forums (e.g., Polkadot and Kusama discourse channels) highlight growing demand for privacy-preserving identity solutions.
Analysis of existing identity tools lacking zero-knowledge privacy or cross-platform usability.
Studies on the impact of fake accounts and scams on DAO treasury security and community trust.

While there are identity-related projects such as KILT Protocol and DID implementations on Polkadot, NullID differs by:
Focusing specifically on zero-knowledge proof-based privacy-first verification rather than general DID frameworks.
Prioritizing practical, user-friendly integrations with messaging platforms (starting with Telegram) used heavily by Web3 projects.
Providing modular, composable verifications that can anchor verified claims on any substrate-based chain or compatible public blockchain.
Emphasizing decentralized identity pages hosted on permaweb (Arweave) as a public yet privacy-preserving proof layer

Projects like BrightID and Proof of Humanity aim at Sybil resistance and social identity verification but lack native zero-knowledge proof privacy or deep integration with messaging platforms. NullID’s modular ZK approach and focus on professional/work email attestations combined with onchain verification and  bot integration create a unique niche for secure, privacy-preserving identity in Web3 coordination layers.


## Team :busts_in_silhouette:


### Team members

- Name of team leader   -     Chandan Kumar 
- Names of team members -      Chandan Kumar (solo)

### Contact

- **Contact Name:** Chandan Kumar 
- **Contact Email:** chankumar015@gmail.com
  


### Team's experience
Chandan Kumar 
I'm Chandan Kumar, a blockchain developer experienced in Rust, Solidity, TypeScript, JavaScript, Python, and Go. My work focuses on building privacy-preserving and user-friendly infrastructure for Web3.  Most recently, I’ve developed a lightweight private transaction layer to enable confidential blockchain interactions without compromising performance.
https://github.com/cadalt0
https://github.com/cadalt0/NULLID
https://nullid.vercel.app/
https://www.linkedin.com/in/cadalt/
https://x.com/CadaltX





## Development Roadmap :nut_and_bolt:

### Overview

- **Total Estimated Duration:**  2 months
- **Full-Time Equivalent (FTE):**  1 FTE
- **Total Costs:** $2600 USD 
- **DOT %:**  50% 


### Milestone 1: Identity Verification Core & Telegram Integration
**Estimated Duration** : 1 month
**FTE**: 1
**Costs**: $1,300

![image](https://github.com/user-attachments/assets/529809ab-ad00-4dad-84f5-ee655bf14cc1)

### Milestone 2: Identity Profiles, Multi-Platform Support & Indexer
**Estimated Duration**: 1 month
**FTE**: 1
**Costs**: $1,300

![image](https://github.com/user-attachments/assets/de7f8ee4-8bbd-4cec-b95c-727ad764fb9b)





## Future Plans

Telegram is where much of Web3 coordination happens. We began with Telegram to solve urgent real-world problems like impersonation and fake admins, validate our architecture under high user volume, and battle-test our zero-knowledge proof (ZK) stack and verification backend within a highly active user base.
But Telegram is only our entry point.
What is NullID really building?
### NullID aims to become the first ZK-powered, cross-platform, verifiable identity layer for Web3 users and communities. 
Our goal is to let users:

Link accounts from Organizations, Telegram, X (Twitter), GitHub, Discord, LinkedIn, Farcaster, Lens, and more
Generate zero-knowledge proofs proving control over these accounts
Store only verified metadata (not raw personal data) onchain
Host a public, decentralized identity profile on permaweb  —  **like Linktree, but backed by cryptographic proofs and free from fake profiles**
this programmable identity layer will be usable by DAOs, dApps, wallets, and reputation systems.

Short-Term Plans
In the coming months, we will enhance NullID with support for more social platforms, make our Telegram bot public and battle-tested, and launch the first set of public identity pages. We plan to actively collaborate with DAO tooling providers, onchain contributor platforms, and community folks  to adopt NullID for lightweight contributor verification.

Long-Term Vision
Our long-term plan is to become the default privacy-preserving identity protocol for Web3. NullID will be integrated with multiple dApps, DAOs, and wallets as a plug-and-play solution for verifiable, multi-platform reputation.
To extend usability into the physical world, we also plan to release NFT-based identity cards — scannable physical cards linked to the owner’s NullID identity. These will be usable at conferences, DAO events, or even for decentralized proof-of-participation systems.

Sustainability & Maintenance
We aim to finance continued development through a mix of methods:
Grants (such as this one) to cover foundational infrastructure and OSS tooling
Premium features or integrations for projects requiring advanced access controls or branding
Collaborations with wallets, identity tools, or onchain reputation platforms

We are committed to keeping the core NullID stack open source, privacy-first, and censorship-resistant — while exploring sustainable paths to support maintenance and iteration.




## Additional Information :heavy_plus_sign:

**How did you hear about the Grants Program?** Twitter 

