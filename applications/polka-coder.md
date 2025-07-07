# Polka Coder

## Project Overview

**Tagline:** An AI code generation tool that converts natural language prompts into FRAME-based parachain runtimes, A FRAME/Substrate custom pallets or ink! smart contracts, work naturally with Cursor IDE.

**Brief description:** Polka Coder is an open-source AI development tool that allows users to generate customized parachain, make custom pallets, and develop ink! smart contract code, or migrate an ink! contract to a parachain runtime from natural language prompts. Built using Retrieval-Augmented Generation (RAG), it is able to search from ink! documentation, community examples and Polkadot documentation to provide accurate code.

**An indication of how your project relates to / integrates into Polkadot (SDK) / Kusama**: PolkaCoder will improve developer experience, accelerate adoption of FRAME, SUBSTRATE, INK, and reduce the entry barrier for both new and experienced builders in the Polkadot ecosystem.

**Why our team is interested:** We are full-stack Web3 developers with experience in development across multiple ecosystems. Over time, we’ve repeatedly encountered the steep learning curve and tooling friction that slows down ink! adoption, especially for new contributors and smaller teams. After experimenting with AI-assisted development flows in other ecosystems (such as Starknet/Cairo), we realized that a retrieval-augmented coding assistant tailored for ink! and Substrate could dramatically improve the developer experience on Polkadot. We believe PolkaCoder will not only save time for existing developers but also unlock access for a broader contributor base, from hackathon participants to entrepreneurs building their first parachain runtime or smart contract. We’re passionate about building open-source tools that accelerate ecosystem growth, and PolkaCoder is our way of contributing to that mission.

### Project Details

PolkaCoder is built using a modular and production-grade stack optimized for Retrieval-Augmented Generation (RAG), AI-assisted code generation, and seamless IDE integration via Model Context Protocol (MCP). Our architecture is inspired by proven systems like [Cairo Coder](https://github.com/KasarLabs/cairo-coder/tree/main/packages), but customized for FRAME, Substrate and ink! development.

**Backend (MCP Server)**

- Node.js and TypeScript: Provides the MCP-compliant HTTP interface that connects to IDEs like Cursor.
- Nestjs: Lightweight and extensible web framework for routing and request handling.
- OpenAPI Schema: Ensures standardized MCP compatibility and future IDE extensibility.

**Retrieval-Augmented Generation (RAG) Engine**

- Embeddings: Utilizes open-source equivalents to vectorize related docs and examples.
- LLM Providers: Supports GPT-4, Claude, and Gemini via pluggable backends.
- Vector Database
  - PostgreSQL with pgvector extension: Stores vectorized FRAME Documentation, FRAME/Substrate pallets, ink! documentation, and curated examples for fast semantic search.
  - Embeddings management: Supports dynamic updates, allowing quick adaptation to new versions of ink! or Substrate.

**DevOps & Tooling**

- Docker and docker-compose: For reproducible local development and deployment.
  pnpm + turbo: Used for managing monorepo structure across ingestion scripts, MCP server, and backend.
- LangSmith (optional): For LLM monitoring and performance debugging during development.

This stack allows us to deliver a fast, reliable, and modular natural language to Frame/Substrate/ink! code generation service that developers can self-host, integrate into IDEs, or use via API. It also ensures that PolkaCoder is future-proof and easily maintainable by the broader community.

#### PoC/MVP or other relevant prior work or research on the topic:

Although the PolkaCoder repository is not yet public, the project builds directly on a proven architecture and prior experimentation with Retrieval-Augmented Generation (RAG) systems tailored for smart contract development.

**Foundational Infrastructure (Validated by Cairo Coder)**

Our development approach is informed by Cairo Coder, a successful open-source RAG-powered code generator for StarkNet’s Cairo language. Cairo Coder, which we are using as an architectural blueprint, attracted over 200 users in its first week. PolkaCoder adapts this infrastructure to target the ink! and Substrate domain.

- We analyzed forum posts and developer feedback to identify major pain points in ink!/Substrate onboarding (e.g. steep learning curve).
- We’ve also reviewed and differentiated our project from similar efforts like Ink!jet and dAppForge, ensuring that PolkaCoder complements rather than duplicates existing tools.

We are now ready to proceed with a fully open-source implementation.

#### What your project is not or will not provide or implement

PolkaCoder is designed as a backend service (Model Context Protocol server) with no standalone web interface or desktop GUI. It is intended to be integrated into IDEs (e.g., Cursor, Zed). PolkaCoder wont focus on XCM at this point, but users can input prompts anyway.

### Ecosystem Fit

#### 1. Where and how does your project fit into the ecosystem?

Polka Coder enhances the Polkadot ecosystem by providing the first AI-powered code generation tool tailored specifically for parachain runtimes, frame custom pallets, and ink! smart contracts. It improves developer experience and lowers onboarding friction. By utilizing RAG technology, it can query official FRAME, SUBSTRATE, Ink! and Polkadot latest documentation, ensuring accuracy, making it a valuable addition to the Polkadot developer toolkit.

#### 2. Who is your target audience (parachain/dapp/wallet/UI developers, designers, your own user base, some dapp's userbase, yourself)?

PolkaCoder is designed primarily for FRAME runtime developers, Substrate devs and ink! smart contracts devs in the Polkadot ecosystem. This includes FRAME/SUBSTRATE runtime engineers implementing custom pallets and blockchain logic, as well ink! developers building on parachains such as Astar, Aleph Zero, Shiden, Pendulum, Amplitude and Phala, as well as. It also targets early-stage builders, hackathon participants, and newcomers who want to rapidly prototype without deep familiarity with Rust or ink!. Additionally, the tool benefits developer experience teams, dApp tool creators, and wallet infrastructure teams who may need to generate or modify contracts dynamically. By integrating seamlessly into IDEs like Cursor via the Model Context Protocol (MCP), PolkaCoder also appeals to AI-native developers looking for intelligent code completion, refactoring, and explanation capabilities. Overall, the target audience spans a wide range of technical users who want to accelerate and simplify FRAME/Substrate or ink! development using natural language interfaces.

#### 3. What need(s) does your project meet?

PolkaCoder addresses several critical needs within the Polkadot development ecosystem. First and foremost, it lowers the steep learning curve associated with FRAME/Substrate and ink! development by allowing developers to generate functional runtime code and smart contracts using plain English. This is especially valuable for new developers, hackathon teams, and non-Rust-native contributors who often struggle with Rust-specific syntax, ink! macros, or FRAME conventions. Secondly, it boosts productivity for experienced developers by automating repetitive boilerplate code, providing context-aware suggestions, and accelerating prototyping workflows. Third, it fills a tooling gap, while LLMs like ChatGPT are useful, they lack up-to-date ink!/Substrate context and often hallucinate APIs or syntax. PolkaCoder solves this by using a retrieval-augmented generation (RAG) pipeline grounded in real ink! documentation and community examples.

#### 4. How did you identify these needs? Please provide evidence in the form of (scientific) articles, forum discussions, case studies, or raw data.

Polkadot stakeholders have emphasized that [developer experience is the #1 priority](https://forum.polkadot.network/t/developer-experience-must-be-our-1-priority/3957), because richer tooling attracts more builders . By automating boilerplate and explaining complex patterns, PolkaCoder [lowers the barrier of entry for smart contract developers](https://forum.polkadot.network/t/ink-jet-a-vs-code-extension-for-generative-ai-assisted-smart-contract-development-with-retrieval-augmented-generation/6572). As one community member noted, an AI tool could help [“ease the onboarding process for new developers”](https://forum.polkadot.network/t/dappforge-ai-powered-plugin-for-polkadot-developers-that-reduces-development-time/6166?page=2) in a space where getting started is challenging. Another observed that Polkadot is a powerful ecosystem that “can be challenging for newcomers to learn”, and that [AI-augmented learning would be “very useful for the development of the ecosystem](https://forum.polkadot.network/t/dappforge-ai-powered-plugin-for-polkadot-developers-that-reduces-development-time/6166/21?page=2). In short, PolkaCoder’s assistance aligns with calls for better DX: it will help developers write, test, and iterate ink! contracts much faster, and pave the way for eventual automated translation of ink! logic into runtime modules. PolkaCoder could also use its gathered knowledge to help port ink! contracts into FRAME pallets via natural-language, further bridging contract and chain development.

#### 5. Are there any other projects similar to yours in the Polkadot/Kusama ecosystem? Make sure to at least check the Polkadot Forum, the wiki's Tech Stack doc and OpenGov.

| Feature / Dimension                      | PolkaCoder                                                                                                                                                     | Ink!jet                                                                 | dAppForge                                                                                            |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Open Source**                          | Fully open source (Apache/MIT)                                                                                                                                 | Not explicitly open source                                              | Not open source or publicly released                                                                 |
| **Interface Type**                       | Model Context Protocol (MCP)                                                                                                                                   | GUI-based VS Code extension                                             | GUI plugin for VS Code (planned)                                                                     |
| **IDE Compatibility**                    | IDE-agnostic, works with Cursor, Zed, CLI, etc.                                                                                                                | Only available in VS Code                                               | Only targets VS Code                                                                                 |
| **Primary Functionality**                | Natural-language to parachain runtimes, customize parachains, ink! smart contract code, make custom pallets or migrate an ink! contract to a parachain runtime | ink! smart contract assistance, refactoring, vulnerability scanning     | General developer assistance for ink!/Substrate (including runtime customization)                    |
| **Retrieval-Augmented Generation (RAG)** | Yes, similar RAG pipeline                                                                                                                                      | Yes, similar RAG pipeline                                               | Training own fine-tuned model, less emphasis on live doc-based retrieval                             |
| **Substrate Runtime Support**            | Yes                                                                                                                                                            | No                                                                      | Yes                                                                                                  |
| **LLM Architecture**                     | Pluggable: OpenAI GPT, Gemini, Claude via LangChain                                                                                                            | OpenAI GPT-4 with high token context + RAG                              | WizardCoder-based custom model (fine-tuned on Substrate/ink!)                                        |
| **Differentiator Summary**               | Modular, IDE-agnostic, open-source backend with runtime generation support                                                                                     | GUI plugin with focus on smart contract authoring and UX within VS Code | Ambitious UX-focused AI tool with fine-tuned model, but lacks public code, MCP, or cross-IDE support |

## Team

### Team members

Name of team leader: Ng Ju Peng
Names of team members:Martin Hofmann, Gian Alarcon

### Contact

Contact Name: Ng Ju Peng
Contact Email: jupeng@quantum3labs.com
Website: https://quantum3labs.com/

### Legal Structure

Registered Address: 68 Circular Road #02-01, Singapore 049422
Registered Legal Entity: Quantum3 Labs Pte. Ltd.

### Team's experience

**Ng Ju Peng (Project Lead):** Blockchain developer with 3+ years of experience and a bachelor's degree in Software Engineering from Xiamen University. Winner of the Starknet Bengaluru Hacker House and founder of Q3x v1. Has contributed to fully on-chain mobile games on Starknet and served as core contributor to Scaffold-Stark. Featured as speaker at Starknet Basecamp and workshops, and built an NFT game on Caldera plus an Ethereum delegation staking platform that secured 100k+ TVL.

**Gian Alarcon:** Software Engineer with a degree in Systems Engineering from UNMSM, Peru, and Intelligence Science Technology from USTB, China. Graduate of Polkadot Blockchain Academy (PBA 5 Singapore). Serves as main contributor to the Scaffold-Stark project with expertise in Rust backend development. Has made significant contributions to the Starknet Dojo framework and founded the onchain game The Marquis.

**Martin Hofmann:** Developer Relations Engineer with expertise in blockchain infrastructure, developer support, and technical documentation. Currently part of the team at PaperMoon.io, helping developers build on Wormhole. Graduate of Polkadot Blockchain Academy (Singapore, 2024). Previously worked at SenseiNode, focusing on blockchain infrastructure, monitoring tools, and building internal tools and dashboards to support operations.

### Team Code Repos

- https://github.com/Scaffold-Stark
- https://github.com/The-Marquis-Gaming
- https://github.com/dojoengine/dojo
- https://github.com/Quantum3-Labs
- https://github.com/q3x-finance/
- https://github.com/Top-Summer-Hackers

#### Please also provide the GitHub accounts of all team members.

- https://github.com/gianalarcon
- https://github.com/ngjupeng
- https://github.com/martin0995

## Development Status

Evidence of demand for PolkaCoder’s functionality comes from both Polkadot forums and analogous projects. As mentioned above, forum discussions [highlight struggles](https://forum.polkadot.network/t/dappforge-ai-powered-plugin-for-polkadot-developers-that-reduces-development-time/6166/21?page=2) with learning ink!/Substrate and the value of AI helps. In addition, community prototypes have drawn enthusiastic responses. For example, a recent forum thread about an AI-powered Polkadot plugin (dAppForge) attracted dozens of positive comments: developers repeatedly said “this is exactly the type of innovation we need” and that such a tool would “make it much easier for devs to write code for innovative chains and dApps”. Finally, as noted above, the StarkNet “Cairo Coder” MCP saw [200+ users in its first week](https://x.com/kasarLabs/status/1937806892849385596), indicating that blockchain developers are eager for AI code generators. We take these as strong signals that the Polkadot community will adopt PolkaCoder once available.

## Development Roadmap

### Overview

- **Total estimated duration:** 2 months
- **Full-time equivalent (FTE):** ~2.5 FTE
- **Total costs:** 30,000 USD

#### Milestone 1

- **Estimated duration:** 1 month
- **FTE:** 2.5
- **Costs:** 15,000 USD

| Number | Deliverable               | Specification                                                                                                                 |
| -----: | ------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
|    0a. | License                   | Apache 2.0 / MIT                                                                                                              |
|    0b. | Documentation             | Inline code documentation + tutorial on using natural language prompts to generate ink! smart contracts in Cursor IDE         |
|    0c. | Testing and Testing Guide | Comprehensive unit tests covering prompt-to-contract generation pipeline                                                      |
|    0d. | Docker                    | Dockerfile to spin up the backend server for ink! generation via Cursor MCP                                                   |
|    0e. | Article                   | Technical blog post: “From Prompt to Contract: ink! Generation with PolkaCoder”, targeting parachain and hackathon developers |
|     1. | ink! Code Generator       | RAG-based backend module that generates valid ink! contract code from English prompts                                         |
|     2. | MCP Integration           | Model Context Protocol (MCP) server compatible with Cursor IDE, exposing PolkaCoder's ink! generation API                     |

### Budget Breakdown For Milestone 1

| Category            | Item                 | Cost      | Amount  | Total          | Description       |
| ------------------- | -------------------- | --------- | ------- | -------------- | ----------------- |
| Personnel (Ju Peng) | Full-Stack Developer | 6,000 USD | 1 FTE   | 6,000 USD      | leading developer |
| Personnel (Gian)    | Full-Stack Developer | 6,000 USD | 1 FTE   | 6,000 USD      | developer         |
| Personnel (Martin)  | Full-Stack Developer | 3,000 USD | 0.5 FTE | 1,500 USD      | developer         |
| **Total**           |                      |           | 2.5 FTE | **15,000 USD** |                   |

#### Milestone 2

- **Estimated duration:** 1 month
- **FTE:** 2.5
- **Costs:** 15,000 USD

| Number | Deliverable               | Specification                                                                                               |
| -----: | ------------------------- | ----------------------------------------------------------------------------------------------------------- |
|    0a. | License                   | Apache 2.0 / MIT                                                                                            |
|    0b. | Documentation             | Inline code documentation + tutorial for generating Substrate runtime and FRAME pallet modules from prompts |
|    0c. | Testing and Testing Guide | CUnit tests for runtime scaffolding, CI instructions for pallet code; testing guide included                |
|    0d. | Docker                    | Dockerfile to test runtime generation features locally                                                      |
|    0e. | Article                   | Deep-dive blog post: “Natural Language for Runtime Generation for Substrate Devs”                           |
|     1. | Custom Pallet Generator   | Convert natural language prompts into FRAME pallets (config, calls, events, storage, etc.)                  |
|     2. | Runtime Generator         | Generate full runtime file using core + custom pallets                                                      |

### Budget Breakdown For Milestone 2

| Category            | Item                 | Cost      | Amount  | Total          | Description       |
| ------------------- | -------------------- | --------- | ------- | -------------- | ----------------- |
| Personnel (Ju Peng) | Full-Stack Developer | 6,000 USD | 1 FTE   | 6,000 USD      | leading developer |
| Personnel (Gian)    | Full-Stack Developer | 6,000 USD | 1 FTE   | 6,000 USD      | developer         |
| Personnel (Martin)  | Full-Stack Developer | 3,000 USD | 0.5 FTE | 1,500 USD      | developer         |
| **Total**           |                      |           | 2.5 FTE | **15,000 USD** |                   |

## Future Plans

In the short term, we intend to enhance and promote PolkaCoder by releasing a fully open-source MVP under a permissive license and actively engaging developer communities through workshops, hackathons, and integration guides for IDEs like Cursor. We plan to collaborate with Polkadot parachains and ecosystem teams to tailor the tool for real-world developer workflows. For long-term maintenance and development, our strategy includes applying for follow-up grants, forming partnerships with parachain teams, and exploring ecosystem support. Ultimately, our long-term vision is to make PolkaCoder the toolchain for building not just FRAME runtimes, substrate parachains and ink smart contracts but also, integrate XCM, Cumulus, and more tools to enable a faster and more accessible developer experience across the Polkadot ecosystem.
