# Solana VM on Polkadot SDK

## Project Overview

> Run Solana programs in the Polkadot ecosystem.

This project aims to integrate Solana execution environment into the Polkadot SDK enabling Solana programs (smart contracts) to run on `Polkadot SDK`-based chains.
This integration will allow Solana programs to be deployed on Polkadot parachains and facilitate interaction with Solana wallets.

### Project Details

This project comprises the following components:

- **Solana VM**
  - `solana_rbpf`: Solana-flavoured eBPF (extended Berkeley Packet Filter) VM
  - `solana-sdk`: Solana SDK for developing Solana core and programs
  - Solana Runtime emulation: Provides program execution contexts and connects Solana VM with Polkadot SDK states.
  - `spl` (Solana Program Library): Standard smart contracts, e.g. `spl-token` equivalent to ERC-20
- **`pallet-solana`:** A pallet module integrated into `Polkadot SDK`-based chains
- **API Sidecar (Solana RPC emulation):** Emulated Solana RPC endpoints to support Solana wallets

While some Solana VM components are derived from the Solana project, significant challenges remain to adapt and run them within Polkadot SDK runtimes.

**Referencecs:**

- [Agave](https://github.com/anza-xyz/agave)
- [Solana BPF](https://github.com/anza-xyz/sbpf)
- [Solana Program](https://github.com/solana-program)

We will adapt these reference implementations and validate all modifications to ensure Solana programs run effectively inside Polakdot SDK runtimes.
Key components like Solana Runtime emulation, Solana RPC emulation, and `pallet-solana` will be developed from scratch.

Our primary focus is compatibility with Solana programs and wallets, though full emulation of Solana features is not intended.
For instance, Solana's high throughput by parallel processing is not supported by Polkadot SDK.

### Ecosystem Fit

Integrating Solana VM into the Polkadot ecosystem will attract Solana dApps and users by enabling seamless migration.
The `pallet-solana` module can be integrated into parachains, enabling compatibility with Solana.
Additionally, we may propose a dedicated system parachain for Solana compatibility to bridge the Polkadot and Solana ecosystems.

The Solana ecosystem has rapidly expanded, with projects like Eclipse introducing SVM (Solana VM) on Ethereum L2.
However, no existing project offers comprehensive Solana compatibility within the Polkadot ecosystem, aside from experimental efforts such as utilizing eBPF as a contract runtime, as discussed on the Polkadot forum.
[[link]](https://forum.polkadot.network/t/ebpf-contracts-hackathon/1084)

## Team

- **Team Name:** Haderech
- **Contact Name:** Jeeyong Um
- **Contact Email:** conr2d@haderech.com
- **Website:** https://github.com/haderech

### Team members

- Jeeyong Um
- Jungyong Um

#### LinkedIn Profiles

- https://www.linkedin.com/in/jeeyong-um
- https://www.linkedin.com/in/jungyong-um

### Team Code Repos

- https://github.com/noirhq/noir
- https://github.com/noirhq/solana-sdk

#### GitHub Profiles

- https://github.com/conr2d
- https://github.com/code0xff

### Team's experience

- Extensive open-source contributions (Polkadot SDK, Frontier, Cosmos SDK, EOS, etc.)
- Alumni of Polkadot Blockchain Academy (PBA)
  - First prize winner at PBA Demo Day

## Development Status

Proof of Concept implementations:

- `pallet-solana` PoC [[link]](https://github.com/NoirHQ/noir/tree/c681ad696586a686b5af1a2afab32d2f1a52acaa/frame/solana)
- `solana-sdk` with `no_std` support [[link]](https://github.com/NoirHQ/solana-sdk/tree/4ea2ba03098f440b934985a31ab00950387331b9/sdk)
- `solana_rbpf` with `no_std` support [[link]](https://github.com/NoirHQ/solana-sdk/tree/4ea2ba03098f440b934985a31ab00950387331b9/rbpf)

## Development Roadmap

### Overview

- **Estimated Duration:** 2 months
- **Full-Time Equivalent (FTE):** 2.5 FTE
- **Total Costs:** 30,000 USD

> Note that deliverables 0a to 0e are mandatory. Please adapt their specification to your project.

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | pallet-solana (GPLv3), sidecar (GPLv3), template-runtime (Unlicense) |
| 0b. | Documentation | Inline documentation of the code and a basic tutorial on integrating `pallet-solana` into Polkadot SDK runtimes |
| 0c. | Testing and Testing Guide | Complete unit and integration tests for vaildation |
| 0d. | Docker | Dockerfile for testing functionality |
| 0e. | Article | Publish an article on the Polkadot forum and public blogging platforms |
| 1. | Pallet Solana | Develop `pallet-solana` to process Solana transactions within Polkadot SDK runtimes |
| 2. | Publishing | Publish packages on `crates.io`, where feasible |
| 3. | Sidecar | Create Solana RPC emulation for wallet interaction |
| 4. | Template Runtime | Provide a template runtime with `pallet-solana` for testing and development |
| 5. | Minimal Testing UI | Develop a minimal web UI for testing wallet interactions |

### Budget Breakdown

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Blockchain Architect | 15,000 USD | 1.0 FTE | 15,000 USD | Architecture design and development |
| Personnel | Blockchain Developer | 10,000 USD | 1.5 FTE | 15,000 USD | Development, testing and documentation |
| --- | --- | --- | **Total** | **30,000 USD** |  |

## Future Plans

The outcomes of this project will be utilized in Haderech's ongoing projects, and be maintained and developed alongside the Polkadot SDK.

We plan to propose a system parachain, **dApp Hub**, that provides multi-VM support including EVM, WASM, Solana VM, and possibly PolkaVM and MOVE.

## Additional Information

- Our team developed a blockchain-based Covid-19 vaccination passport system in Korea, that was officially adopted by the Korean government. [[link]](https://pulse.mk.co.kr/news/english/9853356)
- The project leader, Jeeyong Um, was a top external contributor to the EOS blockchain project.
