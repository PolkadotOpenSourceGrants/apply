# Polkadot Multi-Chain Solver

## Project Overview

A cross-chain routing service that finds optimal swap paths across Polkadot parachains with an intent-based API for wallets and dApps to access liquidity on HydraDX, Moonbeam, and Acala.

**Integration with Polkadot:**
- Connects to 3 parachains via Substrate RPC (subxt, jsonrpsee)
- Aggregates 44 DEX pools
- Uses intent-based architecture with Sr25519 signatures
- Provides unified routing API for cross-parachain swaps

**Why we're building this:**
Polkadot has $580M in liquidity spread across parachains. Wallets need to integrate each DEX separately, which takes weeks of work. This project provides a single intent-based API endpoint that handles routing across all of them.

### Project Details

**Technology Stack:**
- Rust (edition 2024)
- RPC Integration: subxt 0.37, jsonrpsee 0.24
- API Framework: Axum 0.7
- Graph Algorithms: petgraph 0.6 (Dijkstra)
- Cryptography: sp-core 34.0 (Sr25519 signatures)
- Testing: tokio-test, integration tests with live RPC

**Architecture Overview:**

*Project Structure:*
```
polkadot-solver/
├── crates/
│   ├── solver/          # HTTP API server
│   │   ├── main.rs      # Server entry point
│   │   └── api/         # Request handlers, models, storage
│   ├── intent/          # Intent domain model + validation
│   ├── routing/         # Route finding engine (Dijkstra)
│   └── parachains/      # Parachain connectors (RPC integration)
└── README.md            # Project documentation with API reference
```

*Key Components:*

1. **Intent Module** (`crates/intent/src/lib.rs`)
   - Intent struct with validation logic
   - Sr25519 signature verification
   - Deadline, amount, user validation

2. **Routing Engine** (`crates/routing/src/lib.rs`)
   - Graph-based routing (petgraph)
   - Dijkstra's algorithm for shortest path
   - Fee-based cost function
   - max_hops constraint validation

3. **Parachain Connectors** (`crates/parachains/src/`)
   - HydraDX: Omnipool LRNA hub model
   - Moonbeam: UniswapV2-style DEX pools
   - Acala: aUSD-centric AMM pools

4. **HTTP API** (`crates/solver/src/api/`)
   - POST /intents - Submit intent, get route
   - GET /intents/:id - Retrieve intent + route
   - GET /intents - List all intents
   - GET /health - Health check

**PoC/MVP Evidence:**
- **GitHub Repository:** https://github.com/mitsuaki-u/polkadot-solver
- **Status:** Phase 1 MVP complete and operational
- **Live Demo:** API runs on localhost:8080, connects to live parachains
- **Test Coverage:** 9 passing unit tests
**API Specifications:**
See README.md for complete reference. Example:

```bash
# Submit intent to swap DOT → USDC
curl -X POST http://localhost:8080/intents \
  -H "Content-Type: application/json" \
  -d '{
    "sell_asset": {"chain": "hydradx", "token": "DOT"},
    "sell_amount": "10000000000000",
    "buy_asset": {"chain": "hydradx", "token": "USDC"},
    "min_receive": "50000000",
    "deadline": "2025-12-03T12:00:00Z",
    "user": "d43593c715fdd31c61141abd04a99fd6822c8558854ccde39a5684e7a56da27d",
    "max_hops": 3
  }'

# Response: 201 Created with route
{
  "id": "d43593c715fdd31c-DOT-1764695336330",
  "status": "routed",
  "route": {
    "steps": [
      {"from": {"chain": "hydradx", "token": "DOT"},
       "to": {"chain": "hydradx", "token": "LRNA"}},
      {"from": {"chain": "hydradx", "token": "LRNA"},
       "to": {"chain": "hydradx", "token": "USDC"}}
    ]
  }
}
```

**Scope:**

This grant focuses on routing logic and liquidity awareness. Out of scope:
- On-chain execution (route finding only, not execution)
- Cross-chain bridges (single-parachain routes only)
- Dynamic pool updates (pools fetched at startup)
- Database persistence (in-memory storage)
- Production hardening (rate limiting, API keys, etc.)

### Ecosystem Fit

**Where does your project fit into the ecosystem?**

Developer infrastructure for cross-chain routing. 

**Target audience:**

- **Wallet developers** (primary): Wallet providers need cross-chain swaps without integrating 3+ DEX SDKs
- **dApp builders**: Portfolio trackers and trading UIs need simple swap functionality
- **Traders**: Need best prices across HydraDX, Moonbeam, Acala

**What need(s) does your project meet?**

Polkadot has $580M in liquidity split across HydraDX ($500M), Moonbeam ($8-10M), and Acala ($69M). Users get worse prices because they only check one chain. Wallets spend resources integrating each DEX separately.

**Evidence this is needed:**

- [Official Polkadot hackathon](https://github.com/polkadot-developers/hackathon-guide/issues/30) lists "Cross-Chain DEX Aggregator" as a priority project
- W3F funded PrivaDEX and Zenlink (both aggregators, but web apps not APIs)

**Are there any other projects similar to yours in the Substrate/Polkadot/Kusama ecosystem?**

**Yes - Comparison:**

| Project | Type | Integration | Our Difference |
|---------|------|-------------|----------------|
| **PrivaDEX** | Web app | UI only | We provide REST API for developers |
| **Zenlink** | DEX protocol | SDK/Pallet | We're simpler (HTTP API vs Substrate integration) |
| **Polkaswap** | SORA DEX | UI only | We're multi-parachain, they're SORA-specific |

**Similar projects on other chains:**

Ethereum has 1inch and CoW Protocol (intent-based). Solana has Jupiter. All process billions in volume. 

**What makes this different:**
- First intent-based routing API for Polkadot
- Open source
- REST API instead of web app (easier integration for wallets)
- Native HydraDX Omnipool support
 
## Team

**Team Name:** Polkadot Solver

**Contact Name:** Mitsuaki Uchimoto

**Contact Email:** mitsuaki@binarymail.me

**Github:** [github.com/mitsuaki-u](https://github.com/mitsuaki-u)

### Team members

- Mitsuaki Uchimoto

#### LinkedIn Profiles (if available)

https://www.linkedin.com/in/mitsuakiuchimoto/

### Team Code Repos

- This project: https://github.com/mitsuaki-u/polkadot-solver
- Personal: https://github.com/mitsuaki-u

### Team's experience

- 7 years blockchain development on L1 blockchain and SDK for sidechains
- Development of closed-source CLI based DEX trading platform in rust
- This MVP demonstrates: Substrate RPC integration (subxt, jsonrpsee), graph algorithms (Dijkstra), API design (Axum), cryptographic signatures (Sr25519), modular architecture (4 crates)

**Previous Projects:**
- [Lisk SDK](https://github.com/LiskArchive/lisk-sdk)
- 
## Development Status

**GitHub Repository:** https://github.com/mitsuaki-u/polkadot-solver

**Phase 1 MVP is complete.** The working code includes:
- Multi-chain pool aggregation (44 pools across 3 parachains)
- Fee-optimized routing using Dijkstra's algorithm
- RESTful API with intent submission
- Constraint validation (max_hops, deadlines)
- Cryptographic signatures (Sr25519)
- Unit test suite for core validation logic
- Documentation (README.md with API reference)

**Demo Programs:**
```bash
cargo run -p solver --bin demo           # Multi-chain routing
cargo run -p solver --bin intent_demo     # Intent validation
cargo run -p solver --bin sign_intent_demo # Cryptographic signing
```

Research included studying the HydraDX Omnipool (LRNA hub model), Moonbeam's UniswapV2 implementation, and Acala's aUSD AMM. Evaluated routing algorithms and chose Dijkstra for fee optimization.

**Code structure:** 4 modular crates (intent, routing, parachains, API) with error handling (thiserror) and async/await (Tokio). Unit tests cover intent validation, signature verification, and routing logic. Manual API testing performed using demo programs and curl commands.

## Development Roadmap

### Overview

- **Total Duration:** 12 weeks (3 months)
- **Full-time Equivalent (FTE):** 1.0 FTE
- **Total Costs:** $30,000 USD

### Milestone 1: Liquidity-Aware Routing (Reserve Data + AMM Calculations)

- **Duration:** 8 weeks
- **FTE:** 1.0
- **Costs:** $20,000 USD

#### Deliverables

| Number | Deliverable | Specification |
|--------|-------------|---------------|
| **0a.** | License | MIT (already in repository) |
| **0b.** | Documentation | Tutorial in README.md explaining how to run the solver and query routes |
| **0c.** | Testing and Testing Guide | Unit tests for reserve fetching and AMM calculations with execution instructions in README.md |
| **0d.** | Docker | Dockerfile for running the solver with all dependencies |
| **0e.** | Article | Technical article explaining liquidity-aware routing implementation, AMM formulas used, and integration guide for wallet developers |
| **1.** | Reserve Data Integration | Fetch and integrate liquidity pool reserves from HydraDX Omnipool, Moonbeam UniswapV2 pools, and Acala AMM. Filter low-liquidity pools to improve route quality. |
| **2.** | AMM Calculations | Implement accurate output amount calculation for all supported AMMs (UniswapV2, Omnipool, Acala). Calculate price impact and slippage for multi-hop routes. |

**Verification:**
- Pool data includes reserve information for all three chains
- API returns expected output amounts with price impact and slippage estimates
- Routes automatically exclude low-liquidity pools
- All unit and integration tests pass
- Documentation covers all new features

#### Budget Breakdown

**Personnel Costs:**
- Lead Developer: $20,000 (1.0 FTE, 8 weeks)
  - Reserve data integration for HydraDX, Moonbeam, and Acala
  - AMM calculations (constant product formulas, price impact, slippage)
  - Integration, testing, and documentation

**Equipment:** None required

**Subcontracts/Subscriptions:** None required

**Total Milestone 1:** $20,000 USD

---

### Milestone 2: Multi-Criteria Route Optimization

- **Duration:** 4 weeks
- **FTE:** 1.0
- **Costs:** $10,000 USD

#### Deliverables

| Number | Deliverable | Specification |
|--------|-------------|---------------|
| **0a.** | License | MIT |
| **0b.** | Documentation | Updated documentation explaining multi-criteria optimization, weight configuration, and benchmarking results |
| **0c.** | Testing and Testing Guide | Unit tests for composite scoring |
| **0d.** | Docker | Updated Dockerfile with optimization features |
| **0e.** | Article | Article on multi-criteria routing optimization and integration examples |
| **1.** | Multi-Criteria Routing | Implement composite scoring algorithm that considers fees, slippage, price impact, and liquidity depth. Support configurable weight parameters for different optimization profiles. |
| **2.** | Route Comparison | Provide multiple route options with different optimization profiles such as fee-optimized, balanced, and liquidity-optimized configurations. |
| **3.** | Benchmarking Suite | Performance testing framework comparing route quality against fee-only routing. Demonstrate measurable improvement in execution outcomes including total cost, slippage, and success rates. |
| **4.** | Performance Optimization | Optimize route calculation to maintain fast response times under typical load conditions. |

**Verification:**
- Routes demonstrably outperform simple fee-only routing in benchmarks
- API accepts weight configuration parameters
- Multiple route options returned with different trade-offs clearly indicated
- Benchmarking results documented with comparison data

#### Budget Breakdown

**Personnel Costs:**
- Lead Developer: $10,000 (1.0 FTE, 4 weeks)
  - Composite scoring algorithm implementation
  - Dijkstra refactoring for multi-criteria optimization
  - Benchmarking suite development and performance testing
  - Production documentation and integration examples

**Equipment:** None required

**Subcontracts/Subscriptions:** None required

**Total Milestone 2:** $10,000 USD

---

**TOTAL PROJECT COST:** $30,000 USD

---

## Future Plans

**Short-term (6 months):**
- Add more parachains: Bifrost, Interlay, Astar (target 6-10 total)
- Build TypeScript SDK
- Present at developer communities
- Optimize performance (route caching, connection pooling)

**Long-term (6-12 months):**
- On-chain execution via XCM (future grant or self-funded)
- WebSocket API for real-time updates
- 10+ parachains, multiple wallet integrations
- Production deployment with monitoring and SLA

**Maintenance:**

During the grant: full time development with weekly updates. After grant: part time maintenance by original developer plus community contributions. 

**Sustainability:**

Primary model is public good (MIT license). Optional revenue from small solver fees (0.01-0.05%) or hosted API ($500-2000/month). Estimated costs: $500-1000/month for hosting, RPC, and monitoring.

## Additional Information

**Work Already Completed for This Project:**
MVP with 44 pools across 3 parachains (HydraDX, Moonbeam, Acala), fee-based routing, RESTful API, test suite (9 passing tests), documentation (README.md with API reference), three demo programs, and modular architecture (4 crates).

**Are there any other teams who have already contributed (financially) to the project?**
No

**Previous Grants submitted for this project:**
None



