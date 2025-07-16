## **Project Overview**

**Project DAVOS \- The AI-Powered Delegation Assistant**

**Description**

DAVOS is an open-source AI agent designed to improve the quality and clarity of delegation in Polkadot OpenGov. It helps users find delegates aligned with their values by creating transparent, explainable matches between token holders and active governance participants.

Governance participation remains low despite years of education and incentive programs. OpenGov has grown in complexity, and many token holders struggle to follow proposals or choose the right delegate. The result is blind delegation, inconsistent representation, or no participation at all. We believe that one of the core missing pieces is a trusted, user-friendly infrastructure that helps individuals meaningfully delegate their voice.

DAVOS addresses this by generating transparent, auditable profiles for both users and delegates, then computing compatibility scores to support value-aligned delegation. Matches are always explained, with clear reasoning and digest summaries of ongoing delegate activity to help users stay informed.

Think of DAVOS as your personal co-pilot for OpenGov, matching you with delegates who truly align with your principles.

The current grant will support the development of a working MVP. It will be usable from day one and is designed as a low-risk opportunity to test a high-impact idea for OpenGov.

## **Project Details**

DAVOS is built as an AI agent for delegation assistance that connects onchain activity, offchain discussions, and user preferences into a cohesive, explainable delegate-matching system.

The project architecture relies on:

* A frontend interface for users to explore and create profiles, view delegate matches, and receive tailored summaries.

* A backend system that fetches and indexes data from OpenGov referenda, delegate voting records, Polkassembly/Subsquare discussions, and other relevant public sources.

* A multi-model LLM reasoning pipeline that generates delegate profiles and computes compatibility scores between users and delegates.

* A transparent matching engine, with all code and reasoning logic published for auditability and user trust.

**Technology Stack**

* **Frontend**: React with Tailwind, deployed on IPFS

* **Backend**: Node.js server running LangChain for LLM orchestration, indexing logic, and API serving

* **LLMs**: GPT-4, Claude, and DeepSeek (multi-agent consensus to reduce hallucination)

* **Storage & compute**: Initial setup uses offchain storage, with a future plan to migrate reasoning into TEE-backed infrastructure

* **Data ingestion**: API access to Subsquare, Polkassembly, Subscan, GitHub, X (Twitter), and other public endpoints

* **Open Source**: All code will be open-sourced

**Methodology**

Our approach to delegate profiling, user-delegate matching, and reasoning transparency is documented in detail here:

[Design and Data Processing Methodology](https://docs.google.com/document/d/11kTTrIj4Hud7rQzRkgwkJaz8RL2Lib3gGsYXU_ih_TI/edit)

This document describes how we gather onchain and forum data, synthesize it into structured profiles, and use multiple LLMs in parallel to ensure robust, auditable results. All prompting logic will be open source and verifiable by the community.  
The document is open for comments and suggestions.

**What DAVOS is not**

* DAVOS is not an autonomous AI delegate. We explored this path and received mixed feedback from stakeholders. For now, we are focusing on the clearer, validated need for explainable delegation support.  
* It is not a governance system of its own, but a user-side assistant for interacting with OpenGov more effectively.

* DAVOS will not include smart contract logic or onchain delegation automation in the MVP.  
* It will not rely on proprietary or closed-source models or data sources.

## **Ecosystem Fit**

There are already many tools on OpenGov to display governance data, but none of them help users with a clear overview and interpretation of delegate behavior and find those who best represent their values. DAVOS fills this gap with explainable AI that turns raw onchain and offchain signals into actionable insights and personalized matches.

**Target Audience**

* New and existing DOT holders unfamiliar with OpenGov who need trusted guidance

* Community members seeking to delegate but unsure who to trust

* Emerging and smaller Delegates or DVs seeking better visibility and alignment with token holders

**Identified Needs and Validation**

* We conducted extensive validation through calls, community discussions, and AAG participation, and consistently heard two types of signals.   
  * On the problem side: “I don’t know who to delegate to,” “OpenGov is too complex,” and “I want to delegate but don’t want to do it blindly.”   
  * On the solution side, we received encouraging feedback such as: “OpenGov participation isn’t just about voting – it’s about finding the right expertise to evaluate complex decisions. This could really level up governance,” and “I do think some form of delegate matching is an interesting pursuit for the ecosystem.” These conversations confirmed both the pain points and the potential value of DAVOS.

* The DAVOS team presented at three AAG events (234, [242](https://x.com/TheKusamarian/status/1936514461013090766), and 244), where we received strong feedback from participants like Jay from KusDAO and other OpenGov delegates.

* We also got some skepticism from a few existing large delegates, which we believe is partially due to DAVOS introducing a leveling force in the delegation system. Today, token holders often delegate to the most visible or powerful delegates, not necessarily those who align with their values. This creates a feedback loop where large delegates grow larger, while smaller or newer ones remain overlooked. DAVOS helps rebalance this by surfacing matches based on transparent, values-based logic rather than reputation or token weight.  
* At the same time, we also received valid concerns about how DAVOS interprets delegate data. Some questioned whether the profiling would be accurate or whether the AI might misrepresent delegate positions. To address this, we published a [methodology](https://docs.google.com/document/d/11kTTrIj4Hud7rQzRkgwkJaz8RL2Lib3gGsYXU_ih_TI/edit) outlining our data pipeline and matching logic, and we designed the MVP to be transparent, auditable, and open to feedback from both users and delegates.  
* Many also recommended starting with grants and ecosystem programs, rather than OpenGov, and offered valuable perspectives on product scope, delegate inclusion, and what priorities DAVOS should take post-MVP.

**Why Polkadot**

Polkadot is the ideal ecosystem for DAVOS. OpenGov is powerful but complex, making usability a central challenge. At the same time, Polkadot is rapidly becoming a leader in AI-native infrastructure (e.g., Phala, Acurast), and DAVOS is one of the first application that complement this infra and can demonstrate how onchain AI agents can deliver real user-facing value in governance. 

## **Team**

* **Team Name:** DAVOS team

* **Contact Name:** Matteo Carbone

* **Contact Email:** matteo@substancelabs.xyz

* **Website:** [https://x.com/ProjectDavos](https://x.com/ProjectDavos)

### **Team Members**

* **Matteo Carbone** – Cofounder and Business Developer

  Focused on ecosystem design and DAO integrations. Former Product Manager at pNetwork. He leads DAVOS’s governance strategy and community engagement.

  X: [https://x.com/Carbonaut\_](https://x.com/Carbonaut_)

* **Thomas Bertani** – Cofounder and Lead Protocol Engineer

  A pioneer in decentralized finance and interop, Thomas brings deep experience in DAO tooling and governance infrastructure. He led the development of onchain voting, identity, and treasury systems across multiple networks.

  X: [https://x.com/thomasbertani](https://x.com/thomasbertani)

* **Enrico** – Full Stack & Protocol Developer

  Frontend/backend contributor to AI UX flows, DAO dashboards, and privacy-preserving agent infrastructure using TEEs.

  GitHub: [https://github.com/envin3](https://github.com/envin3)

* **Marco** – Senior DevOps Engineer

  Maintains secure infrastructure for blockchain services. Expert in Kubernetes, CI/CD, and blockchain node orchestration.

### **Team’s Experience**

The DAVOS team brings 5 to \>10 years of experience building smart contracts, DeFi applications, and DAO infrastructure across multiple L1 and L2. The team has designed and implemented advanced tooling for governance, voting, and decentralized identity, and is well-connected with contributors active in the Polkadot ecosystem.

## **Development Status**

Project DAVOS has not yet been implemented on-chain, but we have completed all necessary validation steps and are fully prepared to begin MVP development upon securing this grant.

Over the past few months, we have:

* Participated in three Alliance Assembly Gatherings (AAG 234, 242, and 244), where we introduced DAVOS, pitched the vision, and answered follow-up questions from the community and delegates

* Conducted extensive validation with stakeholders across the Polkadot ecosystem, including delegates, DVs, and governance-focused groups such as KusDAO, Trustless Core, and Polkadot Hungary

* Published a [detailed methodology document](https://docs.google.com/document/d/11kTTrIj4Hud7rQzRkgwkJaz8RL2Lib3gGsYXU_ih_TI/edit?usp=sharing) outlining how we plan to process data, profile users and delegates, and match them transparently and accurately

* Designed a [clickable Figma mockup](https://www.figma.com/proto/85DeEOtKTcQuaNq8UxFjYm/DAVOS-x-Polkadot---Kusama?node-id=2-599&t=pGPuMyGGNjQwFOk0-1&scaling=contain&content-scaling=fixed&page-id=0%3A1&starting-point-node-id=2%3A599&show-proto-sidebar=1) that demonstrates the UI and user flows for delegate matching and digest summaries

We are also a finalist team in the **PolkaBiz founder support program**, receiving mentorship and feedback to refine our roadmap and pitch (winners will be selected at the end of this month).

The current grant application asks for $25,000 to build a working MVP, covering six weeks of work. **This is a low-risk opportunity to test a high-impact delegation tool under real-world conditions**. If successful, we will return to OpenGov with a follow-up request to bring DAVOS to production scale.

## **Development Roadmap**

The development of DAVOS will be structured in two milestones over approximately six weeks. The goal is to deliver a fully usable MVP with real user and delegate profiles, a working matching system, and digestible governance insights.

This is not a prototype or mockup phase: the MVP will be functional from day one, ready to be tested with real user feedback.

* **Estimated Duration:** 6 weeks

* **Full-Time Equivalent (FTE):** 4

* **Total Costs:** $25,000 USD (15,000 USD for Milestone 1 and 10,000 USD for Milestone 2\)

### **Milestone 1: Delegate \+ User Ethos Profiling MVP**

**Timeline:** 3 weeks from secured grant

**Funding Requested:** $15,000

**Deliverables:**

* User Ethos: interface for selecting or editing governance profiles

* Delegate Ethos: political profiles based on onchain history and public communications

* Validation and Fine-Tuning of Data Gathering Algorithms, to ensure reliability and alignment with public delegate activity

* Matching Algorithm: personalized compatibility score between user and delegate

* Digest Summary Format: early implementation of digest logic (e.g., recent discussions and activity summaries)

* Initial UI Prototype with working flows

### **Milestone 2: Expanded Matching & Governance Dashboard**

**Timeline:** 3 weeks from completing Milestone 1

**Funding Requested:** $10,000

**Deliverables:**

* Configurable Matching Logic: more advanced alignment criteria and personalization options

* Real-Time Referenda Integration: active votes and up-to-date delegate positions

* Dashboard & UX Polishing: full UI with governance digest and compatibility views

* Finalized MVP with public release

##  Milestones table: 

| Number | Deliverable | Specification |
| ----- | ----- | ----- |
| 0a. | License | MIT |
| 0b. | Documentation | We will provide both inline documentation of the code and a written guide explaining how users can use DAVOS to match with delegates and view governance data. |
| 0c. | Testing and Testing Guide | We will provide comprehensive unit and integration tests for the core logic, with a testing guide detailing how to install, run, and verify each component. |
| 0d. | Docker | We will provide a Dockerfile that reproduces the working environment needed to run the DAVOS MVP in a self-contained setup. |
| 0e. | Article | We will publish an article walking through the MVP release, including key concepts (delegate profiling, user ethos, matching logic) and lessons learned. |
| 1\. | Delegate \+ User Ethos Profiling MVP |  |
| 1a. | User Ethos Interface | Users can define their governance preferences via editable profile templates or freeform input. |
| 1b. | Delegate Political Profile | Analysis of delegate positions using on-chain voting data and public off-chain materials (e.g. forum posts, Medium, X). |
| 1c | Validation and Fine-Tuning of Data Gathering Algorithms | Testing and adjusting data collection logic to ensure reliability and alignment with public delegate activity |
| 1d. | Matching Algorithm | Logic for computing compatibility between user ethos and delegate profiles, with explainable outputs. |
| 1e | Digest Summary Format | Initial format for daily/monthly digests summarizing active discussions and delegate actions. |
| 1f | First UI Prototype | A working frontend prototype allowing basic user onboarding and matchmaking visualization. |
| 2\. | Expanded Matching & Governance Dashboard |  |
| 2a. | Enhanced Matching Configurability | Users can adjust or refine how the matching is computed (e.g. weights, filters). |
| 2b. | Referenda \+ Vote Integration | Real-time integration of OpenGov referenda and delegate votes into the matching and digest modules. |
| 2c. | UX Improvements | UI updates and refinements based on early user feedback during MVP testing. |
| 2d. | Finalized Dashboard and Profiles | A complete version of the DAVOS MVP with usable dashboard and polished profiles for delegates and users. |

Cost breakdown: [Project DAVOS cost breakdown](https://docs.google.com/spreadsheets/d/1iX2v-iwj7F-AeRzcK4aGrgl6XC8dLXJc_aGl22GVFcI/edit?gid=0#gid=0)

| Milestone | Category | Hourly Rate | Hours | FTEs | Total |
| ----- | ----- | ----- | ----- | ----- | :---: |
| 1 | Technical Work | $120 | 100 | 2 | $12,000 |
|  | Business Development | $120 | 25 | 1 | $3,000 |
|  | Marketing | $100 | 0 | 0 | $0 |
|  |  |  |  |  | **$15,000** |
| 2 | Technical Work | $120 | 68 | 2 | $8,160 |
|  | Business Development | $120 | 9 | 1 | $1,080 |
|  | Marketing | $100 | 10 | 1 | $1,000 |
|  |  |  |  |  | **$10,240** |
|  |  |  |  | **TOTAL** | **$25,240** |

## **Future Plans**

After completing the MVP, we aim to continue developing DAVOS into a production-ready agent that can serve as critical infrastructure for OpenGov. Our next development phase will include:

* **Expanded Features**: We plan to introduce features such as direct delegation via the DAVOS interface, richer digest summaries, and broader data coverage (e.g., Discord, multisig activity, etc.).

* **Scalable Matching Engine**: We will enhance the matching system with more flexible logic, allowing users to fine-tune compatibility thresholds and include or exclude specific data sources.

* **Delegate Discovery and Reputation Layer**: As DAVOS becomes more integrated into the governance lifecycle, we will implement features that help highlight emerging delegates and encourage transparency and competition on merit, not just visibility or incumbency.

* **Sustainable Architecture**: All components will remain open source and modular. The LLM inference cost has been carefully evaluated and remains sustainable for the MVP and future growth, with low marginal cost beyond the initial processing of delegate profiles and proposals.

* **Decentralized Infrastructure Integration**: In line with our commitment to verifiability, we plan to integrate confidential inference infrastructure such as Phala and Acurast to ensure auditability and resistance to tampering. This will enable DAVOS to operate as a fully transparent AI assistant.

* **Post-MVP Validation**: We will re-evaluate the idea of DAVOS functioning as an autonomous delegate only after further testing and community feedback. While we initially considered it, feedback was mixed, and we have decided to focus on value-aligned delegation tooling first.

To support ongoing development and maintenance, we plan to pursue a second OpenGov proposal after successfully delivering the MVP and validating its utility. We are also exploring additional grant programs and collaborations within the ecosystem. Long term, DAVOS could evolve into a community-owned tool maintained by a DAO or collective, ensuring transparency, neutrality, and long-term sustainability.

