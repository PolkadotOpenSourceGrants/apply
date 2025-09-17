# Python ink! Typegen and SDK

## Project Overview

**Tagline:** Typed Python clients for ink! contracts generated from contract metadata, plus a small runtime adapter for reliable calls and estimation on any **pallet-contracts** (Contracts pallet) chain.

**Brief description:** This project provides a code generator that converts an ink! contract metadata file into typed Python classes, and a lightweight runtime adapter that offers `read` and `exec` calls, dry-run with weight and gas estimation, retries, batching, and SS58 and AccountId helpers. It reduces reliance on hand-written scripts and supports a clear path toward production use in tests, backends, bots, and data pipelines.

**Relation to Polkadot (SDK) / Kusama:** The tool targets chains that expose the Contracts pallet in the Polkadot SDK and Kusama ecosystems, including parachains that enable contracts and the **`substrate-contracts-node`** development node maintained by the ink! team. It consumes current ink! metadata produced by **`cargo-contract`** and communicates through established Substrate RPC interfaces.

**Why our team is interested:** Dapps over Apps focuses on practical developer experience. Several developer reports indicate progress can stall beyond trivial examples, especially around address handling, metadata mapping, event decoding, and consistent estimation. A typed generator with a focused adapter closes this gap for Python users.

> 

---

### Project Details

**Technology stack:**  
- Python `3.9` to `3.12`  
- Code generator in Python that parses current ink! metadata and emits typed Python packages  
- Runtime adapter on established Python Substrate libraries for transport, metadata, SCALE encoding/decoding, and RPC calls  
- Continuous integration on Linux and macOS  
- Packaged to PyPI as wheels  

**Core components, protocols, architecture:**  
- Metadata parser reads constructors, messages, events, and errors from ink! metadata  
- Code generator emits a Python package with classes for the contract, typed arguments and return values, and event or error enums  
- Runtime adapter provides `read` and `exec`, dry-run with weight and gas estimation, pragmatic retry logic with backoff aligned to targeted node versions and RPC behavior, batching, and SS58 and AccountId utilities  
- Pytest fixtures for local nodes, compiled contracts, and deployed contracts  
- Examples for a simple flipper and a PSP22-style token  

**PoC / prior work:**  
- Review of existing Python Substrate libraries and their contract interfaces  
- To our knowledge there is no widely adopted typed client generator for ink! in Python  
- Internal experiments parsing the contract metadata file and producing minimal call stubs  

**Mockups / designs (CLI flow):**  
1. Developer runs `inkpy codegen` on an ink! contract metadata file and chooses an output package path  
2. The tool generates a Python package with `read` and `exec` methods and type definitions  
3. The developer imports the generated package and uses the runtime adapter to connect to `substrate-contracts-node` or a live contracts parachain  

**Data models / API specifications:**  
- Generated classes map directly to ink! constructors and messages  
- Method signatures expose typed arguments and return values as described in metadata  
- Events and errors are modeled as Python enums or data classes based on metadata, with initial coverage targeting commonly used patterns  
- Runtime adapter methods:  
  - `read` for dry-run and return decoding  
  - `exec` for on-chain calls with weight and gas estimation and retries  
  - `estimate` for explicit estimation  
  - `events` for iterating decoded events  
  - SS58 and AccountId helpers for safe account handling  

**What the project is not / will not provide (v1):**  
- Not a replacement for `cargo-contract`  
- Not an XCM helper or cross-contract code generator  
- Not an EVM tool  

---

## Ecosystem Fit

**Where and how it fits:** It sits at the interface between ink! smart contracts and Python-based applications and tests. It complements existing Python Substrate libraries by adding typed client generation from metadata and a focused adapter for calls and estimation.

**Target audience:**  
- Smart contract developers who prefer Python for tests and tooling  
- Backend and data teams who need programmatic contract calls  
- Hackathon and education teams seeking minimal friction for contract interaction  

**Needs met:**  
- Typed clients from metadata to avoid manual mapping  
- Reliable `read` and `exec` with dry-run and estimation  
- Straightforward event decoding and account utilities  

**How needs were identified:**  
- Several developer reports show difficulty beyond basic examples  
- Address format confusion when mixing Substrate-style accounts and EVM-oriented tools  
- Repeated requests for practical examples and event subscription patterns that work in Python in a repeatable way  

**Similar projects in Polkadot/Kusama:** General Python Substrate libraries support contracts through runtime metadata and generic interfaces. To our knowledge, there is no widely adopted Python tool that generates typed clients for ink! metadata. This project consumes metadata from `cargo-contract` and wraps existing libraries rather than duplicating them.

**Similar projects in related ecosystems:** TypeScript has well-established contract client generators. The lack of a well-established Python equivalent creates friction for teams that standardize on Python.

---

## Team

**Team Name:** Dapps over Apps  
**Contact Name:** Abdulkareem Oyeneye  
**Contact Email:** team@dappsoverapps.com  
**Website:** www.dappsoverapps.com  

### Team Members & LinkedIn Profiles
- **Bolaji Ahmad** — Full Stack Engineer, PBA Alumni  
  https://linkedin.com/in/bolajahmad  
- **Abdulkareem Oyeneye** — Project Lead  
  https://linkedin.com/in/abdulkareem-oyeneye  
- **Emmanuel Charles** — Blockchain Developer & QA Engineer  
  https://linkedin.com/in/emmanuel-charles-0b0023250  
- **Kushimo Bashir** — Blockchain Engineer  
  https://www.linkedin.com/in/kushimo-bashir/  
- **Gospel Ifeadi** — Smart Contract Engineer  
  https://x.com/gospel70800  

### Team Code Repos of Past Works
- https://github.com/RegionX-Labs/Coretime-Notifier  
- https://github.com/r0gue-io/pop-cli  
- https://github.com/dappforce/subsocial-parachain  
- https://github.com/dappforce/grillchat  
- https://github.com/paritytech/polkadot-sdk  

### Team’s experience
Dapps over Apps specializes in Web3 developer tooling and education. Polkadot-specific experience includes contributions to RegionX Labs, Pop CLI, Subsocial, Grillchat, and the Polkadot SDK. Practical experience as Polkadot Blockchain Academy alumni and participation in multiple hackathons informs the team’s focus on accessible onboarding and effective developer experience.

---

## Development Status

We reviewed available Python Substrate libraries, confirmed there is no widely adopted typed client generator for ink! in Python, and created internal experiments that parse the contract metadata file and emit minimal Python call stubs. Outline examples for flipper and PSP22 are prepared with pytest fixture sketches for local nodes.

---

## Development Roadmap


### Overview

**Estimated Duration:** 3 months for build and release. A 6-month maintenance commitment is bundled into milestone 2 without any increase to the requested budget.  
**Full-Time Equivalent (FTE):** 1.5 FTE average across the period  
**Total Costs:** $30,000  

### Milestones and Deliverables

Mandatory items **0a** to **0e** will be delivered as part of each milestone as applicable.

#### Milestone 1 — Code generator and core runtime  
**Budget:** $18,000  

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | Apache 2.0 open source license. |
| 0b. | Documentation | Inline code documentation and a beginner tutorial that covers install, code generation from metadata, connection to the `substrate-contracts-node`, and first `read` and `exec` calls. |
| 0c. | Testing and Testing Guide | Unit tests for metadata parsing and code generation and for runtime calls. End-to-end tests that deploy and call the example contract on the `substrate-contracts-node`. A testing guide explains how to run both suites. |
| 0d. | Docker | A Dockerfile that runs the `substrate-contracts-node` and the end-to-end test suite. |
| 0e. | Article | A public article or workshop that shows the flow from metadata to typed client and successful calls on the `substrate-contracts-node` and one live contracts parachain. |
| 1. | inkpy codegen and core runtime | `inkpy codegen` reads an ink! contract metadata file and generates a typed Python package with constructors, messages, events, and errors. The runtime adapter provides `read` and `exec`, dry-run-based estimation, and SS58 and AccountId helpers. Examples include flipper and a PSP22-style token. CI runs on Linux and macOS for Python 3.9 to 3.12. |

#### Milestone 2 — DX fixtures, release, and maintenance  
**Budget:** $12,000  

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | Apache 2.0 open source license. |
| 0b. | Documentation | Cookbook examples and quickstart updates. |
| 0c. | Testing and Testing Guide | Expanded tests for events and error surfaces and fixtures. Guide updated accordingly. |
| 0d. | Docker | Updated image for release validation and live-chain smoke tests. |
| 0e. | Article | Release note article explaining the fixtures, event iterators, and live-chain smoke test results. |
| 1. | Fixtures, release, and maintenance | Pytest fixtures for local node, compiled contract, and deployed contract. Event iterator utilities and clearer result or error decoding. Smoke tests against one live contracts parachain for `read` and `exec`. Version 1 release to PyPI and GitHub with a compatibility table. **6 months of maintenance** included in this milestone covering triage, critical fixes, and routine compatibility updates with short monthly notes. |

---

## Budget Breakdown

All costs are contained within the 2 milestones and total **$30,000**. 
| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | --- |
| Personnel | Lead engineer | $12,000 | 0.6 FTE for 3 months | $12,000 | Architecture and code-generator core and runtime adapter core |
| Personnel | Senior developer | $10,000 | 0.5 FTE for 3 months | $10,000 | Metadata parser, events and errors, fixtures, CI |
| Personnel | Developer documentation and QA | $6,000 | 0.25 FTE for 3 months | $6,000 | Documentation, cookbook, tutorial, tests, Docker |
| Subcontracts / subscriptions | Cloud runners and CI minutes | $2,000 | Standard usage | $2,000 | CI and release automation |
|  |  |  |  | **$30,000 Total** |  |

---

## Future Plans

**Long-term maintenance and development:** During the 6 months after release we will provide triage, critical fixes, and routine compatibility updates as part of milestone 2. After that period we plan to continue under community governance with small bounties and follow-on grants if the community requests larger features such as cross-contract code generation or XCM helpers.

**Short-term use and promotion:** We will publish examples, a workshop, and a short video to help developers adopt the tool in tests and CI. We will engage with contracts parachain communities to collect feedback and prioritize improvements.

**Long-term vision:** A stable and well-used Python path for ink! that complements Rust and TypeScript and expands the contributor and user base for contracts in the Polkadot and Kusama ecosystems.

---

## Additional Information

**Work already done:** Ecosystem review and internal experiments for metadata parsing and minimal call stubs. Outline examples and fixture plans.

**Other contributions:** We will disclose any external contributions and collaborators in the repository.

**Other funding:** This proposal is not funded elsewhere. If we later apply to other entities we will disclose the details and will scope work to avoid duplication and to respect open governance.

**Non-overlap statement:** To our knowledge there is no widely adopted Python tool that generates typed clients from ink! contract metadata. Existing Python Substrate libraries enable contract interaction through generic interfaces. This project builds on those libraries, adds typed client generation, and targets immediate developer experience gains without duplicating existing efforts.
