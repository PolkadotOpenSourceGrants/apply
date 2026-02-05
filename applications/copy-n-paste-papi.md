# PAPI Copy-n-Paste

## Project Overview

**Tagline:** Stop scrolling through docs – start building.

**Description:**
PAPI Copy-n-Paste is a development platform for the Polkadot-API (PAPI) that combines interactive documentation, live blockchain interaction, code generation, and agent-friendly outputs. Developers can explore pallets and extrinsics, execute transactions from connected wallets, query live blockchain data, subscribe to real-time state changes, and interact with smart contracts across multiple chains.

The next stages expand the tool in three directions:

1. **Agentic developer workflows** via an MCP-style API server and AI-optimised exports.
2. **A Remix-style, in-browser contract IDE** for ink! and Solidity interaction.
3. **An AI-assisted Substrate pallet builder** that generates pallets from structured spec sheets and large test suites using a TDD loop.

**Integration with Polkadot/Kusama:**
The app uses the PAPI library to connect to multiple Substrate chains (Polkadot, Kusama, Polkadot Asset Hub, Polkadot People, Moonbeam, Astar, Acala, Hydration, and others). By generating code that calls PAPI methods, it reduces boilerplate and accelerates dApp development. Standardised AI-friendly markdown exports plus an MCP server will make PAPI easier to consume from tools like Claude, Cursor, Continue, and other LLM-powered agents.

**Motivation:**
PAPI docs and examples are fragmented, forcing developers to jump between dev.papi.how, GitHub examples, and their editor. This project offers a single interactive playground to learn by doing, reducing context-switching and speeding up onboarding. Feedback from PBA Bali classmates, ecosystem developers, and direct conversations with the PAPI team shows strong demand for an interactive, code-generating learning environment.

---

## Project Details

**Technology stack & architecture:**
Next.js web app with TypeScript, Tailwind CSS, and shadcn/ui components. Monorepo with a core package for chain metadata and PAPI helpers. Turbo and pnpm for build management.

### Deliverables (overall)

**Interactive explorer**

* Expanded chain support including Polkadot, Kusama, Polkadot Asset Hub, Polkadot People, and major parachains (Moonbeam, Astar, Acala, Hydration, Aleph Zero where possible).
* Intuitive UI for browsing pallets, storage, extrinsics, and events with contextual help and surfaced Rust doc comments.

**Live code generator**

* Real-time transaction and storage query snippets with parameter validation.
* Idiomatic TypeScript code using PAPI best practices and real parameter values from executed calls.

**Demo / use-case dashboard**

* A gallery of “recipes” (Token transfer dApp, Simple staking dashboard, Governance voting helper, etc.) that:

  * Pre-configure relevant pallets and calls.
  * Show the full flow end-to-end.
  * Generate reusable snippets and starter templates.

**CLI integration**

* Built-in interface for `create-papi-app` so users scaffold projects directly from the webapp.
* Templates aligned with recipes, so devs go from “try in browser” to “clone + run locally”.

**Contract interaction module**

* Remix-style interface for ink! and EVM contracts.
* Address validation and contract type detection (ink!/EVM).
* Metadata fetching from explorers, registries, IPFS, manual upload.
* Dynamic method interface generation with parameter forms.
* Real-time event monitoring and storage inspection for ink! contracts.
* Local-first execution, then chain integrations to major parachains.

**In-browser code editor**

* Bidirectional REPL:

  * Use UI to execute actions and generate code.
  * Edit single-file code inline in browser.
  * Re-execute and keep UI state in sync.
* Editor modes for:

  * TypeScript PAPI calls.
  * ink! contracts (compile, deploy, interact).
  * Solidity contracts (compile, deploy, interact).

**Agentic tooling integration**

* MCP server exposing PAPI metadata, pallets, calls, and examples for agentic IDE queries.
* AI-optimised markdown exports capturing:

  * Exact calls performed.
  * Types and parameter shapes.
  * Short structured descriptions for LLM context windows.
* Example prompts and docs on using Copy-n-Paste PAPI with AI agents.

**Searchable docs & inline references**

* Extract Rust doc comments from metadata and pallet crates with links to canonical docs (docs.rs, dev.papi.how).
* Fuzzy search (⌘K) across pallets, methods, events, and doc comments.

**Documentation & tutorials**

* Getting-started guides for:

  * Queries and extrinsics.
  * Demo recipes.
  * Contract IDE usage.
  * AI agent workflows.
  * Pallet builder spec-to-tests-to-code pipeline.

**Tests & deployment**

* Unit, integration, and E2E tests for common flows.
* Dockerfiles for reproducible development and production builds.

**UX & wallet improvements**

* Wallet picker flow when multiple wallets are installed.
* Core performance + clarity improvements.

**Limitations:**
Client-side dev and interaction tooling only. No full IDE features, advanced debugging, or version control. Wallet integration via browser extensions.

---

## Ecosystem Fit

**Where and how does your project fit into the ecosystem?**
Copy-n-Paste PAPI fills a gap in Polkadot developer tooling by providing interactive PAPI discovery, live execution, and exact code generation. It bridges static docs and full dApp frameworks. The new phases extend this bridge to agentic workflows, contract development, and runtime development.

**Who is your target audience?**

* Parachain developers building on Substrate.
* dApp developers creating Polkadot-based apps.
* Frontend developers learning PAPI.
* Educational institutions teaching blockchain development.
* Hackathon teams needing rapid prototyping.
* Developers using AI coding tools who need structured, accurate PAPI context.

**What needs does your project meet?**

* Fragmented PAPI docs causing context-switching.
* Lack of interactive learning and experimentation.
* Missing code generation for common PAPI patterns.
* No unified, multi-chain contract interaction tool.
* Substrate pallet development remains hard even for experienced devs.
* AI agents struggle due to scattered and non-agent-friendly PAPI knowledge.

**How did you identify these needs?**

* PBA Bali experience building with PAPI.
* Feedback from classmates and ecosystem devs facing the same pain.
* Direct conversations with PAPI authors and leaders.
* Forum response and early preview users.

**Similar projects and relationship**

* **dev.papi.how (PAPI Console):** Official PAPI team console to browse metadata and run live storage/extrinsic calls on networks, mainly for developers who already know what they're looking for.
* **papi-simulator / PAPI Interactive Console:** Browser playground to write and execute Polkadot-API code against testnets with examples, focused on code-first experimentation.
* **polkadot.js Apps:** General Substrate UI for wallets, staking, governance, and extrinsic submission, not a PAPI learning or code-generation tool.
* **Copy-n-Paste PAPI:** Visual PAPI explorer plus live execution that instantly generates production TypeScript, scaffolds projects, and exports agent-friendly context.

**Difference from dev.papi.how**

* Interactive execution before coding.
* UI-guided understanding of inputs and outputs.
* Copy-paste production TypeScript from real executions.
* Project scaffolding via CLI.
* Agent-friendly markdown + MCP for LLM workflows.

---

## Team

**Team Name:** illegalcall
**Contact Name:** Dhruv Sharma
**Contact Email:** [dhruvcoding67@gmail.com](mailto:dhruvcoding67@gmail.com)
**Website / GitHub:** [https://github.com/illegalcall](https://github.com/illegalcall)

**Team members:**
Dhruv Sharma, sole developer for development, design, testing, documentation.

**LinkedIn:**
[https://www.linkedin.com/in/d3v-dhruv/](https://www.linkedin.com/in/d3v-dhruv/)

**Repos:**

* PAPI Copy-n-Paste: [https://github.com/illegalcall/papi-copy-n-paste](https://github.com/illegalcall/papi-copy-n-paste)
* create-papi-app: [https://github.com/illegalcall/create-papi-app](https://github.com/illegalcall/create-papi-app)

**Experience:**
Built the prototype and CLI using Next.js 15, TypeScript, and PAPI. Attended PBA Bali in 2025, with training in Substrate, Rust, and Polkadot architecture. Collaborated with PAPI authors and validated the tool with community feedback.

---

## Development Status

Open-source under MIT. Fully functional web app and published CLI. Current capabilities:

* Live blockchain interaction with multi-RPC support.
* Real-time subscriptions via observables.
* Wallet-based extrinsic execution.
* Multi-chain switching.
* Interactive PAPI documentation.
* TypeScript code generation.
* Project scaffolding via CLI.

This grant focuses on:

1. Hardening v1.
2. Shipping agentic infra.
3. Delivering in-browser contract IDE + interaction.
4. Delivering AI papi dapp + substrate pallet builder with spec + TDD loop.

---

## Development Roadmap

**Total Duration:** 6 months
**FTE:** 1 FTE (solo developer)
**Total Budget:** 30,000 USD

### Milestone 1 – V1 Hardening + Agentic Infrastructure (Months 1-2)

**Payment:** 10,000 USD (development + maintenance)

**Scope:** Finalize existing tool with production-ready polish and build lightweight MCP-style API server for agentic IDEs (Claude, Cursor, Continue). No self-hosted inference. Local first.

| Number | Deliverable               | Specification                                                                                          |
| -----: | ------------------------- | ------------------------------------------------------------------------------------------------------ |
|     0a | License                   | All new code under MIT, dependency compatibility maintained.                                           |
|     0b | Documentation             | Inline docs, getting-started guide, tutorials for queries, extrinsics, and demo recipes.               |
|     0c | Testing & guide           | Unit tests, integration tests, E2E flows. pnpm test guide included.                                    |
|     0d | Docker                    | Dev + prod Dockerfiles for reproducible builds.                                                        |
|     0e | Article                   | Forum article on goals, architecture, usage, recipes.                                                  |
|      1 | Searchable docs           | Extract Rust doc comments, link canonical docs, fuzzy ⌘K search.                                       |
|      2 | Network expansion         | Explicit Asset Hub + People support, chain switcher, README list.                                      |
|      3 | Wallet UX                 | Wallet picker when multiple extensions. Tests + docs.                                                  |
|      4 | Markdown exports          | AI-optimised markdown for executed calls + examples for LLM workflows.                                 |
|      5 | MCP server v1             | Tooling endpoints exposing PAPI metadata, pallets, calls, types, examples. SSE transport where needed. |
|      6 | Agent workflows           | Example configs + prompts for Claude/Cursor/Continue to query MCP and use markdown exports.            |
|      7 | AI-optimised doc pipeline | Automated markdown export improvements: better type summarisation, call traces, chain context.         |
|      8 | Cost + ops plan           | Document operational costs and usage limits (AI API cost model, caching strategy, rate limiting).      |
|      9 | Maintenance plan          | Clear plan for prompt updates, doc refresh cadence, server ops tasks, and budget.                      |

**Note on maintenance:**
Milestone 1-2 payments include maintenance allocations for infrastructure operations (API usage, server costs), prompt refinement, version bumps, and ecosystem updates. Local-first architecture minimizes ongoing costs.

---

### Milestone 2 – Contract IDE + AI Pallet Builder (Months 3-6)

**Payment:** 20,000 USD (development + maintenance)

**Scope:** Build Remix-style in-browser IDE supporting **ink! + Solidity** with interaction capabilities. Develop AI-assisted Substrate pallet builder that generates pallets from structured specs and large test suites using a TDD loop. Local first.

| Number | Deliverable                | Specification                                                                                        |
| -----: | -------------------------- | ---------------------------------------------------------------------------------------------------- |
|     1a | IDE core                   | Monaco-based editor, file panel, console, templates for ink!/Solidity.                               |
|     1b | ink! compile pipeline      | Backend compile using deterministic Dockerised toolchain. Return WASM + metadata.                    |
|     1c | Solidity compile pipeline  | solc backend compile. Return ABI + bytecode.                                                         |
|     1d | Deploy + interact (local)  | Local sandbox execution for contracts, then UI for deploy/call.                                      |
|     1e | Contract interaction | ink! contract interaction flow. Solidity contract interaction (metadata and source hashes). |
|     1f | Chain integration v1       | After local flows stabilize, add deploy/call to 2-3 major contract parachains.                       |
|     1g | Contract docs + tutorials  | End-to-end guides: write → compile → deploy → interact → call.                                         |
|     2a | Spec sheet format          | Provide "business use case → spec → testcases" structured template and prompt guidance.              |
|     2b | Testcase ingestion         | AI generates 50-200 testcases from spec; user reviews/approves. Format as executable Substrate pallet tests. |
|     2c | TDD generation loop        | AI generates pallet, compiles, runs tests, iterates until all pass or safe stop.                     |
|     2d | Pallet quality gates       | cargo check/fmt, basic linting, weight scaffolding, event/error correctness checks.                  |
|     2e | Local runtime sandbox      | Auto-generate node template + integrate pallet locally for user verification.                        |
|     2f | Pallet docs + examples     | Tutorials with real specs (including privileged call patterns).                                      |

---

## Budget Breakdown

| Category  | Item        | Amount     | Description                                                                              |
| --------- | ----------- | ---------: | ---------------------------------------------------------------------------------------- |
| Personnel | Milestone 1 | 10,000 USD | V1 hardening, docs, tests, networks, UX, MCP server, agent workflows + maintenance.      |
| Personnel | Milestone 2 | 20,000 USD | Contract IDE for ink!/Solidity + interaction, AI pallet builder with spec + TDD + maintenance. |

**Total:** 30,000 USD

---

## Success Metrics

**Milestone 1 success**

* Searchable explorer with doc comments and typo-tolerant search.
* Asset Hub + People supported.
* Wallet picker fixed.
* AI Markdown export.
* MCP server queried successfully from Claude/Cursor.

**Milestone 2 success**

* ink! and Solidity contracts editable, compile and run end-to-end in browser.
* ink! contract interaction succeeds for common contracts.
* Local flows solid before chain integration.
* 2-3 parachain deploy targets supported after local validation.
* Pallets generated from spec + testcase suites with passing rates in sandbox.
* Compile + test iteration loop stable and predictable.
* Clear guidance on when pallet vs contract is appropriate.

---

## Future Plans (Unfunded Roadmap)

**JAM / Polkadot 3.0 integration**
Once JAM tooling and developer standards stabilise, adapt:

* PAPI discovery and generation to JAM APIs and service model.
* Contract IDE deploy/interact to JAM-compatible runtimes.
* Pallet builder to JAM patterns if runtime development model changes.

This is not funded in this grant, but will be a priority maintenance and follow-on scope.

