# Speed Run Polkadot

## Project Overview

**Tagline:** Interactive, gamified learning platform for onboarding developers to the Polkadot ecosystem through hands-on challenges.

**Description:**  
Speed Run Polkadot is an open-source educational platform that enables developers to learn Polkadot development through progressive, hands-on challenges. Inspired by Speed Run Ethereum's model of interactive learning, this platform features two distinct learning tracks: (1) building user-centric dApps using Polkadot APIs and parachain infrastructure, and (2) building custom blockchains using the Polkadot SDK. Each challenge includes scaffolding code, automated grading systems, and deployment to testnets.

**Integration with Polkadot:**  
- Built using Polkadot.js API, Substrate, and Polkadot SDK
- All challenges deploy to Polkadot testnets (Paseo/Westend)
- Integrates with parachain ecosystems (Moonbeam, Astar, Acala, etc.)
- Teaches both ink! smart contracts and Substrate pallet development
- Demonstrates XCM cross-chain messaging
- Uses Polkadot wallet infrastructure (Polkadot.js, Talisman, SubWallet)

**Why I'm Building This:**  
As a Polkadot Fast Grants alumni who built PowerGrid Network, I experienced the steep learning curve for Polkadot development firsthand. When I wanted to learn Substrate, I found mostly text-based documentation but few interactive, hands-on resources. Speed Run Ethereum exists for the Ethereum ecosystem, but Polkadot lacks an equivalent platform. Having won multiple hackathons, I've seen how new developers struggle with Polkadot's unique architecture. This platform aims to provide the interactive learning experience that I wish existed when I was starting out.

### Project Details

**Technology Stack:**
- **Frontend:** React 18 / Next.js 14 with TypeScript
- **Styling:** Tailwind CSS
- **Backend:** Node.js / Express.js
- **Blockchain Integration:** 
  - Polkadot.js API
  - Substrate Node Template
  - ink! 4.x
  - Zombienet for testing
- **Testing:** Mocha/Chai for unit tests
- **Infrastructure:** Docker, GitHub Actions, Vercel
- **Database:** PostgreSQL

**Core Components:**

**1. Challenge Scaffolding System**
- GitHub template repositories for each challenge
- Docker containers with Polkadot tools pre-installed
- Automated setup scripts

**2. Auto-Grading Engine**
- Verifies blockchain state on testnets
- Validates transaction execution
- Checks smart contract deployment
- Confirms pallet integration

**3. Learning Track 1: User-Centric dApps (6 Challenges)**

| Challenge | Difficulty | Key Concepts |
|-----------|-----------|--------------|
| 1. Balance Transfer | Beginner | Polkadot.js API, accounts, extrinsics |
| 2. Multi-sig Wallet | Beginner | Multi-signature accounts |
| 3. NFT Minting | Intermediate | Parachain integration |
| 4. DeFi Swap Interface | Intermediate | DEX interaction |
| 5. XCM Basics | Advanced | Cross-chain transfers |
| 6. Full-stack dApp | Advanced | Complete application |

**4. Learning Track 2: Build a Blockchain (6 Challenges)**

| Challenge | Difficulty | Key Concepts |
|-----------|-----------|--------------|
| 1. Substrate Node Setup | Beginner | Node architecture, runtime |
| 2. Custom Pallet | Beginner | Storage, dispatchables, events |
| 3. Runtime Configuration | Intermediate | Weights, genesis config |
| 4. Off-chain Workers | Intermediate | OCW, HTTP requests |
| 5. Cross-Pallet Integration | Advanced | Pallet coupling |
| 6. Parachain Deployment | Advanced | Collator setup, testnet |

**Prior Work:**

**PowerGrid Network (Polkadot Fast Grants):**
- Built on Polkadot/Substrate
- Custom pallets for energy management
- IoT integration
- Repository: https://github.com/kunal-drall/PowerGrid_Network

**Halo Protocol:**
- Multi-chain DeFi platform
- Live on Solana Devnet
- Soonami venturethon EIR Track win
- Demonstrates ability to ship production applications
- Multi-chain expansion planned including Polkadot

**What This Project Will NOT Provide:**
- Not a comprehensive Polkadot course (focused on hands-on learning)
- Not a certification program
- Not covering governance or parachain auctions
- Not multilingual initially (English only for MVP)
- Not mobile apps (web-based only)

### Ecosystem Fit

**Where it fits:**  
Developer education infrastructure for Polkadot, bridging the gap between documentation and production development.

**Target Audience:**
- Developers new to Polkadot
- Ethereum developers exploring Polkadot
- Hackathon participants
- Self-taught developers

**Need Addressed:**

Based on my experience at hackathons and building on Polkadot, I've observed that:
- New developers struggle with Substrate's complexity
- Most resources are documentation-heavy
- There's no clear, interactive learning path
- Polkadot's unique value (building blockchains) isn't easy to learn

**Similar Projects in Polkadot:**

**Polkadot Wiki & Documentation:**
- Comprehensive but not interactive
- Complementary to this project

**Substrate Tutorials:**
- Text-based guides
- Not gamified or interactive

**Polkadot Blockchain Academy:**
- In-person/hybrid program
- Requires application and selection
- Limited capacity

**Speed Run Polkadot Difference:**
- Interactive and hands-on
- Gamified with leaderboards
- Free and open-source
- Self-paced
- Covers both dApps and blockchain building

**Similar Projects in Other Ecosystems:**

**Speed Run Ethereum:**
- Interactive challenges for Ethereum
- Proven model that works
- Speed Run Polkadot adapts this for Polkadot

**CryptoZombies:**
- Gamified Solidity learning
- Shows demand for interactive education

## Team

**Team Name:** 29projects Labs  
**Contact Name:** Kunal 
**Contact Email:** kunaldrall29@gmail.com 
**Website:** https://github.com/kunal-drall

### Team Members

Kunal Drall

### LinkedIn Profile

- https://linkedin.com/in/kunaldrall

### Team Code Repos

- https://github.com/kunal-drall/PowerGrid_Network
- https://github.com/kunal-drall/halo
- https://github.com/kunal-drall/educate-fi
- https://github.com/kunal-drall

### Team's Experience

**Kunal Drall** - Full-stack blockchain developer:

**Polkadot Experience:**
- **Polkadot Fast Grants Alumni:** PowerGrid Network
- Built Substrate-based blockchain with custom pallets
- Experience with Polkadot.js API and testnet deployments

**Production Track Record:**
- **Halo Protocol (Founder):** Live DeFi platform on Solana
- 50 active users, 94% retention rate, zero defaults
- Multi-chain expansion planned

**Hackathon Success:**
- ISA Solarthon (UN COP'24): 2nd runner-up
- Soonami Venturethon: Winner (EIR track)
- Solana SuperteamDE: Track winner
- Agoric Fast Hack: Bounty winner
- EduChain Build Station Delhi: Top project

**Technical Skills:**
- Rust (Substrate/FRAME), Solidity
- TypeScript, JavaScript, React, Node.js
- Polkadot.js, ink!, various blockchain SDKs
- Docker, GitHub Actions

**Education:**
- BTech in Computer Science (in progress), SGT University

## Development Status

**Current State:** Planning phase

**Completed:**
- Analyzed Speed Run Ethereum's approach
- Designed challenge curriculum for both tracks
- Planned platform architecture
- Created initial Docker setup for Substrate development

**No prior funding for this specific project.**

## Development Roadmap

### Overview

- **Estimated Duration:** 3 months
- **Full-Time Equivalent (FTE):** 1 FTE
- **Total Costs:** $30,000 USD

### Milestone 1: Platform Infrastructure & Track 1 (dApp Challenges)

**Estimated Duration:** 6 weeks  
**FTE:** 1  
**Cost:** $15,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | MIT License |
| **0b.** | Documentation | (1) Inline code documentation, (2) Setup guide for local development, (3) User tutorial for completing challenges, (4) Challenge creation guide, (5) API documentation |
| **0c.** | Testing Guide | Unit tests with >70% coverage for auto-grading engine and API. Instructions for running tests. Integration tests for challenge verification. |
| **0d.** | Docker | Dockerfile for backend, frontend, and Substrate node. Docker Compose for local development. |
| **0e.** | Article | Medium article explaining the project, architecture, and first 6 challenges |
| **1.** | Frontend Platform | React/Next.js application with: challenge browser, challenge page with code editor, progress tracking, leaderboard, wallet integration (Polkadot.js, Talisman, SubWallet), responsive design |
| **2.** | Auto-Grading Engine | Node.js backend with: REST API, blockchain state verification on testnets, transaction validation, smart contract testing, scoring system, PostgreSQL integration |
| **3.** | Challenge Scaffolding | GitHub template repositories with starter code, setup scripts, and local testing |
| **4.** | Track 1 Challenges (6) | **Challenge 1: Balance Transfer** - Polkadot.js API basics, account management, simple transfers<br/><br/>**Challenge 2: Multi-sig Wallet** - Multi-signature accounts, threshold signing, transaction approval<br/><br/>**Challenge 3: NFT Minting** - Parachain integration, NFT creation<br/><br/>**Challenge 4: DeFi Swap** - DEX integration, token swapping<br/><br/>**Challenge 5: XCM Transfer** - Cross-chain messaging basics, asset transfers<br/><br/>**Challenge 6: Lending dApp** - ink! smart contract, full frontend, deployment<br/><br/>Each includes: starter code, tests, solution, deployment instructions |

### Milestone 2: Track 2 (Blockchain Challenges) & Platform Polish

**Estimated Duration:** 6 weeks  
**FTE:** 1  
**Cost:** $15,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | MIT License |
| **0b.** | Documentation | Complete documentation including admin guide, troubleshooting, video tutorials for first 3 challenges, deployment guide |
| **0c.** | Testing Guide | Full test coverage for Track 2 challenges, end-to-end testing guide, CI/CD documentation |
| **0d.** | Docker | Production-ready Docker Compose setup with optimization |
| **0e.** | Article | Technical article on auto-grading system + launch announcement |
| **1.** | Track 2 Challenges (6) | **Challenge 1: Substrate Setup** - Node template compilation, local node launch, UI connection<br/><br/>**Challenge 2: Custom Pallet** - Pallet creation with storage, dispatchables, events, errors, unit tests<br/><br/>**Challenge 3: Runtime Config** - Weight configuration, genesis setup, chain spec<br/><br/>**Challenge 4: Off-chain Workers** - HTTP data fetching, signed transactions from OCW<br/><br/>**Challenge 5: Cross-Pallet Integration** - Multiple interacting pallets, trait bounds<br/><br/>**Challenge 6: Parachain Deployment** - Collator setup, testnet registration, block production<br/><br/>Each includes: starter code, comprehensive tests, solution, documentation |
| **2.** | Gamification Features | Badge system for achievements, personal statistics, challenge ratings, streak tracking |
| **3.** | Community Features | Project showcase, Discord integration for notifications, solution discussion after completion |
| **4.** | Production Polish | Performance optimization, monitoring setup, security hardening, SEO optimization, accessibility improvements |

### Budget Breakdown

| Category | Item | Monthly Rate | Duration | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Full-Stack Blockchain Developer | $10,000 USD | 3 months | $30,000 USD | Platform development, 12 challenges with solutions, auto-grading, testing, documentation |
| --- | --- | --- | **Total** | **$30,000 USD** |  |

## Future Plans

**Maintenance:**
- Apply for Web3 Foundation grants/Polkadot Treasury funding for ongoing maintenance
- Open-source model allows community contributions
- Explore parachain partnerships for sponsored challenges

**Short-term:**
- Launch at Polkadot events
- Share with developer communities
- Gather user feedback for improvements

**Long-term:**
- Expand challenge library based on demand
- Add more advanced topics if platform gains traction
- Potential specialization tracks for different use cases

## Additional Information

**Work Already Done:**
- Platform architecture planning
- Challenge curriculum design
- Docker setup for Substrate development
- Initial auto-grading proof-of-concept

**Previous Funding:**
- Polkadot Fast Grants: PowerGrid Network (~$10K in DOT)
- Hackathon prizes (non-dilutive, used for other projects)

**Other Applications:**
- No other grant applications submitted for this project

**Why Solo:**
- Successfully shipped PowerGrid Network and Halo Protocol independently
- Full-time commitment for 3 months
- Direct accountability

**Commitment:**
- All code will be open-source (MIT License)
- Platform will remain free
- Willing to collaborate with Polkadot DevRel for feedback
- Bi-weekly progress updates

---

Thank you for considering this application.
