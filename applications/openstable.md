# OpenStable: Adaptive Open-Source Stablecoin Platform on Polkadot

## Project Overview

This project is an open-source, Ethereum-compatible stablecoin platform built on Polkadot Hub’s new PVM. It enables fiat-backed stablecoin issuance through smart contracts that support minting, compliance workflows, KYC, and auditing.

Rather than enforcing rigid regulatory frameworks, the platform provides an abstracted compliance layer designed to adapt to diverse regulatory environments. This flexibility allows institutions and developers to align with local requirements without sacrificing interoperability or composability.

Initially focused on South Korea’s evolving KRW stablecoin market, the project aims to showcase the capabilities of PVM and reduce adoption friction for Solidity developers. The architecture is designed to be extensible across currencies and jurisdictions, positioning Polkadot Hub as a global leader in adaptable, institution-ready stablecoin infrastructure.

### Project Details

We aim to deliver a full-stack, open-source stablecoin issuance platform that can serve both as infrastructure for institutional-grade deployments and as a flexible toolkit for developers building on Polkadot Hub’s Ethereum-compatible PVM.

#### Technology Stack

- Smart Contracts: Solidity, deployed on PVM (Ethereum-compatible Polkadot Virtual Machine)
- Backend Framework: Rust with actix-web for orchestration, PostgreSQL for data persistence
- Frontend UI: Svelte (for admin/operator dashboards and demo interfaces)

#### Core Components

- Minting & Burning Module (Smart Contract)
- Abstracted Compliance & KYC/AML Integration Layer
- Audit Logging & Monitoring Module
- Admin Dashboard & Issuance Workflow Management
- RESTful APIs for Wallet Simulation and Demo Interactions

#### PoC / MVP

We are currently in the architecture and design phase of a KRW-backed stablecoin issuance platform built on Polkadot Hub’s PVM. Our goal is not just to deliver a proof-of-concept but to implement core features—such as minting, burning, freezing, blacklist management, and whitelist management via an abstracted KYC compliance layer—at a production-ready level. Additionally, we aim to develop a minimal UI demo that enables users to interact with these functionalities.

This system will consist of smart contracts and an API server responsible for intermediate processing, with the ultimate goal of delivering a fully functional demo UI. By leveraging PVM’s Ethereum compatibility, the platform will showcase a reliable and practical stablecoin issuance infrastructure tailored for regulated markets.

#### Data Models / API Specs

We plan to define JSON-based data models for core stablecoin operations such as minting, burning, freezing, blacklisting, whitelist management for KYC-verified accounts, and compliance workflows. These will be exposed via RESTful endpoints as part of the demo implementation. Initial API development will focus on administrative and issuer-facing operations, designed around a modular and extensible compliance abstraction layer to accommodate different regulatory requirements and KYC providers.

#### What This Project Will Not Provide

- This project will not offer a consumer-facing wallet or payment application.
- We do not aim to implement algorithmic stablecoins or decentralized collateral mechanisms.
- The focus is not on building a DeFi product, but rather on infrastructure for regulated issuance.

### Ecosystem Fit

Our project proposes a regulated fiat-backed stablecoin issuance platform built on Polkadot Hub’s new Ethereum-compatible environment powered by the RISC-V-based Polkadot Virtual Machine (PVM). This strategic upgrade introduces smart contract support while preserving the modularity and security of the Polkadot stack.

We believe a KRW-based stablecoin platform tailored to South Korea’s emerging regulatory framework can serve as a flagship showcase for PVM on Polkadot Hub. South Korea is experiencing rapid regulatory clarity around fiat-backed stablecoins, with strong interest from enterprises looking to issue KRW-pegged tokens. However, there is currently no production-ready infrastructure within the Polkadot ecosystem to meet this demand. Additionally, while Ethereum development is widespread in Korea, familiarity with the Polkadot SDK remains low—making an EVM-compatible solution the most viable path forward for adoption.

To address this, our platform will be implemented using PVM-compatible smart contracts delivering core features such as issuance, compliance workflows, KYC, and whitelist management. Importantly, it is designed around an abstracted compliance layer that provides flexible adaptation to diverse regulatory requirements and KYC providers. This abstraction enables seamless extension and customization across different jurisdictions and institutional needs.

The technical stack includes Solidity-based contracts, a lightweight Rust backend (with actix-web and PostgreSQL), and a Svelte-based frontend to serve as a working demo for institutional stakeholders.

While our initial focus is on the Korean market, the architecture is designed to be extensible across currencies and jurisdictions. As an open-source framework, it aims to empower other nations and institutions to launch regulated fiat-backed stablecoins on Polkadot. In doing so, this project positions Polkadot Hub not just as an Ethereum-compatible network, but as a global hub for institutional-grade, compliance-ready stablecoin infrastructure.

## Team

- **Team Name:** KDC (Korea Digital Currency)
- **Contact Name:** Jungyong Um
- **Contact Email:** <contact@kdccy.com>
- **Website:** <https://kdccy.com>

### Team members

- Jungyong Um
- Jeeyong Um

#### LinkedIn Profiles

- <https://www.linkedin.com/in/jungyong-um>
- <https://www.linkedin.com/in/jeeyong-um>

### Team Code Repos

- <https://github.com/noirhq>
- <https://github.com/kdccy>

#### GitHub Profiles

- <https://github.com/code0xff>
- <https://github.com/conr2d>

### Team's experience

- Extensive open-source contributions (Polkadot SDK, Frontier, Cosmos SDK, EOS, etc.)
- Alumni of Polkadot Blockchain Academy (PBA)
  - First prize winner at PBA Demo Day
- Participation in the Bank of Korea’s CBDC consulting project and development of a proof-of-concept (PoC).
- Participated in the development of the blockchain infrastructure and backend for COOV, South Korea’s official COVID-19 digital vaccine certificate app, which utilizes blockchain-based digital identity verification.

## Development Status

We are currently designing and developing a KRW-backed stablecoin issuance system on Polkadot Hub’s Ethereum-compatible environment (PVM).

The smart contracts are being developed based on an in-depth analysis of existing implementations, particularly Circle’s USDC. Key functionalities under review include minting, burning, freezing, blacklist management, and regulatory compliance. Based on this analysis, we are designing contract-level restrictions to allow on-chain transfers only between addresses that have completed KYC verification.

The backend is being implemented using Rust’s actix-web framework with PostgreSQL. It serves as a modular and abstracted compliance layer that handles KYC processing, user onboarding, identity verification, and registration of verified wallet addresses to an on-chain whitelist. This abstraction enables seamless integration with various in-house or third-party KYC providers, ensuring flexibility to adapt to different regulatory environments. Addresses not on the whitelist will be programmatically blocked from participating in token transfers.

- <https://github.com/kdccy/stablecoin-evm>
- <https://github.com/kdccy/openstable-server>

## Development Roadmap

### Overview

- **Estimated Duration:** 3 months
- **Full-Time Equivalent (FTE):**  2 FTE
- **Total Costs:** 30,000 USD

| Number | Deliverable       | Specification                                                                                         |
|-------:|-------------------|----------------------------------------------------------------------------------------------------|
| 0a.    | License           | Apache 2.0                                                                                         |
| 0b.    | Documentation     | Inline code documentation and a basic tutorial explaining how to deploy and interact with the stablecoin smart contracts and backend services. |
| 0c.    | Testing and Guide  | Unit tests covering all core functions, along with a guide explaining how to run tests locally.    |
| 0d.    | Article           | A medium-level technical article introducing the OpenStable demo and how it demonstrates regulated stablecoin issuance on Polkadot Hub using PVM. |
| 1.     | Smart Contracts   | A set of Solidity contracts deployed to PVM implementing minting, burning, freezing, blacklisting, and KYC-based access control. |
| 2. | Backend Services | A lightweight, modular Rust backend (using actix-web and PostgreSQL) providing an abstracted compliance layer with REST APIs for smart contract interaction, flexible KYC integration, data management, and audit logging. |
| 3.     | Frontend UI       | A Svelte-based dashboard simulating issuer/operator workflows including issuance, compliance, and user management. |
| 4.     | API & Data Models | JSON-based data models and REST API specifications for mint/burn/freeze/blacklist/KYC operations, published in the documentation. |

### Budget Breakdown

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Blockchain Architect | 10,000 USD | 1.0 FTE | 10,000 USD | Architecture design and development |
| Personnel | Blockchain Developer | 10,000 USD | 2.0 FTE | 20,000 USD | Development, testing and documentation |
| --- | --- | --- | **Total** | **30,000 USD** |  |

## Future Plans

We envision OpenStable not just as a product, but as a foundational, open-source infrastructure for regulated stablecoin issuance on Polkadot. While we will build a sustainable business on top of it, our core platform—including essential smart contracts and tools—will remain open and free to use, allowing other teams, developers, and institutions to build upon it without reinventing the wheel.

In the short term, we will release a production-ready demo targeting South Korea’s emerging KRW-backed stablecoin market. This will help validate our approach, demonstrate real-world utility, and attract partners for further development and deployment.

To fund continued development, we will commercialize value-added services—such as white-labeled UIs, compliance automation, and managed stablecoin operations—but profits will be reinvested to improve the open-source platform. This ensures that as the platform grows, so does its ability to support new jurisdictions, currencies, and use cases.

We are committed to growing the ecosystem around OpenStable by engaging with public and private stakeholders, supporting contributors, and improving the platform based on real-world feedback. Our goal is to make OpenStable a trusted, community-driven foundation for compliant stablecoin issuance in regulated markets worldwide.
