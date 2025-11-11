# PAPI Copy‑n‑Paste

## Project Overview

* **Tagline:** *Stop scrolling through docs – start building.*
* **Description:** PAPI Copy‑n‑Paste is a development platform for the Polkadot‑API (PAPI) that combines interactive documentation, live blockchain interaction, and code generation. Developers can explore pallets and extrinsics, execute transactions from connected wallets, query live blockchain data, subscribe to real-time state changes, and interact with smart contracts (ink! and EVM) across multiple chains. The upcoming v2.0 will add contract interaction capabilities including address validation, metadata fetching, method execution, event monitoring, and storage inspection.
* **Integration with Polkadot/Kusama:** The app uses the PAPI (Polkadot API) library to connect to multiple Substrate chains (Polkadot, Kusama, Moonbeam, Astar, Acala and others). By generating code that calls PAPI methods, it reduces boilerplate and accelerates dApp development.
* **Motivation:** PAPI docs and examples are fragmented, forcing developers to jump between resources. This project offers a single interactive playground to learn by doing, reducing context‑switching and speeding up onboarding. Positive forum feedback shows the community values this tool and wants to see it improved and maintained.

### Project Details

* **Technology stack & architecture:** Next.js web app with TypeScript, Tailwind CSS, and shadcn/ui components. Monorepo structure with core package for chain metadata and PAPI helpers. Turbo and pnpm for build management.
* **Deliverables:**

  * **Interactive explorer:** Support for more chains and extrinsics with an intuitive UI and contextual help.
  * **Live code generator:** Real‑time transaction and storage query snippets with copy‑to‑clipboard and parameter validation.
  * **CLI integration:** A built‑in interface for `create‑papi‑app` so users can scaffold projects directly from the webapp.
  * **Contract interaction module:** Remix‑style interface for interacting with ink! and EVM contracts across multiple chains, including metadata fetching, method execution, event monitoring, and storage inspection.
  * **Documentation & tutorials:** A getting‑started guide and examples showing how to use the generated code in real projects.
  * **Tests and deployment:** Unit/integration tests and Dockerfiles for reproducible builds.
* **Limitations:** Client-side contract interaction and development tools only. Excludes full IDE features, debugging, and version control. Wallet integration via browser extensions.

### Ecosystem Fit

Help us locate your project in the Polkadot/Kusama landscape and what problems it tries to solve by answering each of these questions:

**Where and how does your project fit into the ecosystem?**
PAPI Copy‑n‑Paste fills a critical gap in the Polkadot developer tooling ecosystem by providing interactive documentation and code generation capabilities that are currently missing.

**Who is your target audience?**
- Parachain developers building on Substrate
- dApp developers creating Polkadot-based applications  
- Frontend developers learning PAPI integration
- Educational institutions teaching blockchain development
- Hackathon participants needing rapid prototyping tools

**What need(s) does your project meet?**
- Fragmented PAPI documentation requiring context-switching
- Lack of interactive learning tools for PAPI
- Missing code generation for common PAPI patterns
- Absence of multi-chain contract interaction tools

**How did you identify these needs?**
Evidence from Polkadot forum discussions, community feedback on existing tools, and direct developer pain points expressed during PBA Bali and hackathon participation.

**Are there any other projects similar to yours in the Polkadot/Kusama ecosystem?**
- dev.PAPI.how provides excellent documentation and examples
- Polkadot.js Apps focuses on governance, not development tools
- No existing interactive PAPI playground with live blockchain interaction

**How is your project different from dev.PAPI.how?**
While dev.PAPI.how provides comprehensive documentation and static examples, PAPI Copy-n-Paste offers significant improvements:
- **Better and Easier Access to Docs**: Streamlined navigation and searchable API reference
- **Understanding of the API**: Clear visualization of inputs and outputs for each method
- **Try Before You Code**: Test APIs directly in the browser before implementing
- **Ready-to-Use Code**: Copy-paste TypeScript snippets that work immediately
- **CLI Setup**: Complete CLI tool to scaffold repositories with starter code for dApps

**Are there any projects similar to yours in related ecosystems?**
The current v1 provides interactive PAPI development capabilities, with v2 planned to add contract interaction features that will transform it into the "Etherscan for Polkadot" - enabling developers to enter any contract address and interact with it across all contract types (ink!, EVM) and major chains.

## Team

> **Note:** As a solo applicant you will still need to complete KYC/KYB, but there is only one beneficiary listed below.

* **Team Name:** illegalcall
* **Contact Name:** *Dhruv Sharma*
* **Contact Email:** *dhruvcoding67@gmail.com*
* **Website / GitHub:** [https://github.com/illegalcall](https://github.com/illegalcall)

### Team members

* *Dhruv Sharma* – sole developer responsible for development, design, testing and documentation.

#### LinkedIn Profiles

* https://www.linkedin.com/in/d3v-dhruv/

### Team Code Repos

* **PAPI Copy‑n‑Paste:** [https://github.com/illegalcall/papi-copy-n-paste](https://github.com/illegalcall/papi-copy-n-paste)
* **create‑papi‑app:** [https://github.com/illegalcall/create-papi-app](https://github.com/illegalcall/create-papi-app)

### GitHub Accounts

* https://github.com/illegalcall

### Team's experience

I built the initial PAPI Copy‑n‑Paste prototype and `create‑papi‑app` CLI using Next.js 15, TypeScript and PAPI. In 2024 I attended **PBA Bali (Polkadot Blockchain Academy)**, receiving advanced training in Substrate development, Rust programming, and Polkadot ecosystem architecture from experts including Dr. Gavin Wood. I collaborated with PAPI authors, gaining insights into best practices and ecosystem needs. My open‑source contributions and hackathon participation demonstrate Polkadot ecosystem familiarity and community feedback integration.

## Development Status

The project is already open‑source under the MIT licence with a fully functional web application ([papi-copy-n-paste-web.vercel.app](https://papi-copy-n-paste-web.vercel.app/)) and published CLI ([create‑papi‑app](https://www.npmjs.com/package/create-papi-app)). The current implementation provides comprehensive PAPI development capabilities with live blockchain interaction.

**Current Platform Capabilities:**
- **Live Blockchain Interaction**: Connect to multiple RPC endpoints and query real-time data
- **Real-Time Subscriptions**: Watch blockchain state changes using PAPI observables
- **Transaction Execution**: Send transactions from connected wallets (Polkadot.js, Talisman, SubWallet)
- **Multi-Chain Support**: Switch between Polkadot, Kusama, and parachains
- **Interactive Documentation**: Navigate PAPI docs with live examples
- **Code Generation**: Generate TypeScript snippets with real parameter values
- **Project Scaffolding**: CLI tool for bootstrapping PAPI projects

**Technical Implementation:**
- Monorepo architecture with Next.js, TypeScript, and modern tooling
- Multi-RPC connection management with failover support
- Wallet integration for major Polkadot ecosystem wallets
- Real-time metadata fetching and parameter validation
- Community validation through active usage and forum feedback [post](https://forum.polkadot.network/t/stop-scrolling-docs-start-building-meet-copy-n-paste-papi/14850)

The platform delivers significant value as a comprehensive PAPI development environment.

## Development Roadmap

**Duration:** 3 months | **Budget:** $15,000 USD | **Payment:** $5,000 (for v1 already developed), $10,000 upon contract interaction completion

This MVP focuses on core contract interaction capabilities, establishing the foundation for future backend infrastructure.

### Overview

* **Estimated Duration:** 3 months
* **Full‑Time Equivalent (FTE):** 1 FTE (solo developer)
* **Total Costs:** 15 000 USD


### Milestone 1 – Finalise Existing Tool (Month 1)
**Payment:** $5,000 USD

|  Number | Deliverable                     | Specification                                                                                                                                                                                                     |
| ------: | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **0a.** | **License**                     | Release all new code under the MIT licence and ensure third‑party dependencies remain compatible.                                                                                                                 |
| **0b.** | **Documentation**               | Provide comprehensive inline documentation, a getting‑started guide and tutorials covering transactions and storage queries. Publish docs in the repository and webapp.                                           |
| **0c.** | **Testing & Testing Guide**     | Implement unit tests (utilities, hooks), integration tests (UI interactions) and end‑to‑end tests (common user flows). Include instructions to run tests using pnpm.                                              |
| **0d.** | **Docker**                      | Supply Dockerfiles for development and production to ensure reproducible builds and deployment.                                                                                                                   |
| **0e.** | **Article**                     | Publish a technical article on the Polkadot forum explaining the project's goals, architecture and how to use the tool. Invite feedback and contributions.                                                        |

### Milestone 2 – Contract Interaction (Months 2–3)
**Payment:** $10,000 USD upon completion

|      Number | Deliverable                                    | Specification                                                                                                                                                                                                                                                                                                                                                                                |
| ----------: | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **0a.–0e.** | **Re‑licensing, docs, tests, Docker, article** | Update all mandatory items to reflect the new features and publish a second article describing the contract‑interaction module.                                                                                                                                                                                                                                                              |
|      **4.** | **Contract Interaction (v2)**                  | Build core contract interaction capabilities: implement contract address validation and detection for ink! and EVM contracts, multi-source metadata fetching (block explorers, registries, IPFS, manual upload), dynamic method interface generation with parameter forms, real-time event monitoring and storage inspection for ink! contracts, and seamless multi-chain support across Moonbeam, Astar, Aleph Zero, and other major parachains. |
|      **5.** | **Discovery & Release**                 | Implement contract discovery features: popular contracts database, search functionality, recently deployed contracts tracking, and user contract history. Finalise UX with educational content and performance optimizations. Publish v2.0 ready for backend infrastructure expansion.                                                                                                                                                                                                                                                     |

### Budget Breakdown

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Sole Developer | 15,000 USD | 1 FTE | 15,000 USD | Leading project development, implementing contract interaction features, UI/UX improvements, documentation, testing and maintenance |
| --- | --- | --- | **Total** | **15,000 USD** | **Payment Schedule:** $5,000 (for v1 already developed), $10,000 upon contract interaction completion |

## Success Metrics

**Core Contract Interaction Features:**
- Contract address validation working for ink! and EVM contracts across 3+ chains
- Metadata fetching from multiple sources (block explorers, registries, IPFS, manual upload) with 80%+ success rate
- Dynamic method interface generation with working parameter forms
- Real-time event monitoring and storage inspection for ink! contracts
- Multi-chain support for Moonbeam (EVM), Astar (dual VM), and Aleph Zero (ink!)

**User Experience & Performance:**
- Contract load time under 5 seconds end-to-end
- 90%+ transaction success rate for contract method execution
- Interactive contract method forms with parameter validation and type checking
- Real-time transaction status updates and result display
- Comprehensive error handling and user feedback
- Educational tutorials and documentation for contract interaction

**Technical Foundation:**
- Modular architecture ready for backend infrastructure expansion
- Contract discovery system with popular contracts database
- Search functionality for contract discovery
- User contract history and favorites system
- Performance optimizations for large contract interactions

**Ecosystem Validation:**
- 30+ developers actively using contract interaction features within 3 months
- Positive feedback from PAPI team and ecosystem developers
- Integration with at least 2 major parachain developer programs
- Community contributions to contract templates and examples
- Successful contract interactions across different contract types (ink!, EVM)

## Future Plans

After delivering v2.0 MVP, I will maintain the tool and incorporate new PAPI features. The next phase focuses on backend infrastructure for advanced features like comprehensive contract discovery, analytics, and user management. I plan to seek further funding, promote at hackathons, and collaborate with parachain teams. User feedback will guide priorities like mobile support and enterprise features.

## Additional Information

The prototype and CLI are publicly available under MIT licence with community feedback via the forum. My PBA Bali participation and direct mentorship from PAPI creators provide unique insights into the library's usage patterns and developer experience goals, ensuring PAPI Copy‑n‑Paste aligns with best practices. This is my first grant request; no prior funding received. Contributions welcome via GitHub.