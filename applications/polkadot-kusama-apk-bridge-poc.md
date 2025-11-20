# Polkadot-Kusama APK Bridge: A Proof-of-Concept for Trustless Cross-Chain Communication

## Project Overview

This project proposes the development of a Proof-of-Concept (PoC) for a Polkadot-Kusama bridge utilizing Aggregated Public Key (APK) proofs. The primary goal is to establish a **cost-efficient**, trustless, and **highly optimized** mechanism for cross-chain communication between the Polkadot and Kusama ecosystems as an example. By aggregating validator signatures into a single proof, this bridge **significantly reduces on-chain verification costs**. This architecture demonstrates the viability of using APK proofs for **gas-efficient**, secure, and scalable interoperability among networks of independent consensus systems within the Polkadot ecosystem and beyond like Ethereum, specifically showcasing the messaging of verified block headers.

### Project Details

This PoC will focus on the core cryptographic and on-chain components required for the APK proof-based bridge. The technology stack will primarily involve Rust for Substrate development and Solidity for smart contracts on Kusama AssetHub, if a suitable environment is available.. The architecture will involve a custom APK proof crate implementing `bls12_377` + `bw6_761` and `bls12_381` + `bw6_767` curves, a relayer, and an APK proof verifier smart contract on Kusama AssetHub.

**Key components and their interactions:**

*   **APK proof relayer:** This service will be responsible for listening to validator set signatures (using BEEFY) from a polkadot full node with ecdsa-bls signature mode enabled and relay the message with the generated proof to the target chain/contract. After a pre-defined wait-and-listen period and upon accumulating sufficient signatures, it generates the aggregated BLS signature and aggregated public key for the received keys alongside the bitfield indicating participating validators and  the APK proof. This proof will then be submitted to the remote chain/smart-contract over RPC.

*   **Kusama AssetHub Smart Contract:** This smart contract acts as the destination chain and will verify the received APK proof and BLS signature, using pairing operations over the outer curve (`BW6-761` and `BW6-767`) and updates its state with validated block headers. The assumption here is that the validator set commitment is updated on the Kusama side smart contract on Asset Hub.

* **Cryptography Stack:**  

| Component              | Curve / Type | Purpose |
| --- | --- | --- |
| **Inner Curve (IC)**   | `BLS12-377` or `BLS12-381` | Aggregation of validator public keys and signatures; all APK proof computations happen here.|
| **Outer Curve (OC)**   | `BW6-761` or `BW6-767`     | Verification of APK proofs. Ensures efficiency and correctness of aggregated public keys and BLS signatures. |
| **APK Proof Crate**    | Generic over IC + OC       | Generates and verifies aggregated public keys; produces SNARK proof over OC. |

#### Key cryptographic properties:

- Aggregated public keys cannot be faked by malicious relayers.
- Relayers cannot submit an invalid signature without being detected.
- Pairing checks between IC and OC ensure succinct and trustless verification on-chain.
- Supports dual curve configuration: BLS12-377 + BW6-761 and BLS12-381 + BW6-767.

This makes the PoC flexible, future-proof, and compatible with both existing validator sets and potential ecosystem standards.

**What this project is _not_ or _will not_ provide or implement:**

*   A full-fledged, production-ready bridge with all the complexities of a complete cross-chain messaging system. This is a PoC to demonstrate the core cryptographic and on-chain verification mechanisms.
*   A comprehensive user interface or extensive off-chain infrastructure beyond the necessary relaying mechanisms.

### Ecosystem Fit

The current GRANDPA + Beefy based cross-chain bridges in the Polkadot/Kusama ecosystem are practical for Kusama but become prohibitively expensive for other chains, such as Ethereum. Aggregated Public Key (APK) proofs, which compress validator signatures into a single, lightweight proof, offer a more efficient alternative. Our PoC of the APK Bridge demonstrates this enhancement, significantly reducing both data and computational overhead while enabling high-performance cross-chain trustless verification. Beyond improving efficiency within the Polkadot ecosystem, APK proofs make it feasible to extend trustless bridges to other chains where the current GRANDPA+BEEFY model is impractical, expanding the reach of the ecosystem and unlocking new interoperability opportunities while maintaining security and decentralization. This PoC not only demonstrates the feasibility of APK-based bridging but also establishes a foundation for scalable, low-cost trustless cross-chain communication across multiple blockchain ecosystems. This will benefit:

*   **Parachain developers:** By providing a robust mechanism for cross-chain data verification.
*   **Dapp developers:** Enabling them to build applications that span both Polkadot, Kusama and other chains, leveraging assets and functionalities from multiple networks.
*   **The broader Polkadot/Kusama community:** By enhancing overall security and decentralization of cross-chain interactions, inspiring APK-bridge deployment to multiple other chains, thereby increasing the Polkadot userbase.

Our approach with APK proofs offers a novel and potentially more efficient alternative focusing on scalability while demonstrating the capabilities of Web3Sum protocol developed by Web3 foundation. The `w3f/apk-proofs`, `w3f/ring-proofs` and `w3f/bls-beefer` repositories indicate ongoing research and development in this area, and our project aims to build upon and contribute to these efforts.

## Team

*   **Team Name:** Lipika Labs
*   **Contact Name:** Kumar Gunjan
*   **Contact Email:** gunjan.cn@gmail.com
*   **Website:** https://github.com/k-gunjan

### Team members

*   Kumar Gunjan

#### LinkedIn Profiles

*   Kumar Gunjan: https://www.linkedin.com/in/gunjan321/

#### Team Code Repos

- Kumar Gunjan: https://github.com/k-gunjan

### Team's experience

Kumar Gunjan: I bring 15 years of engineering experience spanning Telecom, Distributed system and Cyber security with deep specialization in blockchain development and the Polkadot ecosystem. I am a graduate of the Polkadot Blockchain Academy (Hong Kong cohort). I have demonstrated expertise through multiple successful Polkadot SDK-based projects, including Kylix Finance—delivered under the Web3 Foundation's Decentralized Futures Grant. My technical contributions span the full stack of decentralized infrastructure: I have architected an IPFS-based storage network, designed a zero-knowledge proof protocol, and contributed directly to the Polkadot ecosystem through merged PRs ([polkadot-sdk#3350](https://github.com/paritytech/polkadot-sdk/pull/3350), [substrate-front-end-template#270](https://github.com/jimmychu0807/substrate-front-end-template/pull/270)). My prior experience developing production-grade cross-chain bridges positions me uniquely to deliver the APK Bridge with the security, reliability, and architectural rigor this project demands.

## Development Status

This project is currently in the research and design phase. We have conducted initial investigations into APK proofs, BLS signatures, and existing Polkadot/Kusama infrastructure components like off-chain workers and AssetHub smart contracts. We have identified `w3f/apk-proofs` and `w3f/bls-beefer` as key reference repositories for our implementation. Work in progress can be seen in a PR to `w3f/apk-proofs` [PR-47](https://github.com/w3f/apk-proofs/pull/47). Our prior work on a Web3 Foundation grant and contributions to the Polkadot SDK provide a strong foundation for this project.

## Development Roadmap

This project will be executed in three distinct milestones, each with clearly defined deliverables and verification steps. We anticipate the total duration of the project to be approximately 3 months.

### Overview

*   **Estimated Duration:** - 3 Months
*   **Full-Time Equivalent (FTE):** - 2.25 FTE
*   **Total Costs:** - 22,500 USD

### Milestone 1: Implementation of BLS12-381 based APK Proofs

- **Estimated Duration:** 3 weeks
- **Full-Time Equivalent (FTE):**  0.75 FTE
- **Total Costs:** - 7,500 USD

| Number | Deliverable | Specification |
| --: | --- | --- |
| 0a. | License | Apache 2.0 License. All code will be open-sourced under the Apache 2.0 license. |
| 0b. | Documentation | Comprehensive inline code documentation of code will be provided. |
| 0c. | Testing and Testing Guide | Unit tests for all core cryptographic functions.|
| 0d. | Docker | Dockerfiles for the APK proof exported modules will be provided.|
| 0e. | Article | A technical article explaining the design and implementation will be published.|
| 1. | APK Proofs crate implementation| **Specification:** Refactor the existing APK Proof implementation, showcasing support for BLS12-381 signatures, making it more general and adaptable for use in the Polkadot-Kusama APK Bridge. This involves identifying and isolating the hardcoded curve logic in the current implementation (e.g. `BLS12-377` and `BW6-761`), and designing a modular architecture that allows for easy integration of different elliptic curves, e.g. `BLS12-381` with `BW6-767`. We will utilize existing Rust libraries, such as `ark-bls12-381`, to implement `BLS12-381` based APK proof schemes and ensure compatibility with Polkadot's cryptographic standards. We will also implement a succinct non-interactive argument of knowledge (SNARK) to verify the correctness of the aggregated public key, referencing the APK proofs article for guidance. **Verification:** Comprehensive unit tests will verify the correctness of the new APK Proof implementation. Integration tests will ensure compatibility with other components of the Polkadot-Kusama APK Bridge. Documentation will include the architecture and design decisions, along with usage examples and guidelines for integration. |


### Milestone 2: APK Proof Generation and Relay

- **Estimated Duration:** 2 weeks
- **Full-Time Equivalent (FTE):**  0.5
- **Total Costs:** - 5,000 USD

| Number | Deliverable | Specification |
| --: | --- | --- |
| 0a. | License | Apache 2.0 License. All code will be open-sourced under the Apache 2.0 license. |
| 0b. | Documentation | Comprehensive inline code documentation of code will be provided. |
| 0c. | Testing and Testing Guide | Unit tests for all the updated feature of Polkadot node will be provided|
| 0d. | Docker | Dockerfiles for the APK proof relayer to facilitate easy setup and testing of the PoC. |
| 0e. | Article | A technical article explaining the design, implementation, and significance of the update targeting a technical audience within the Polkadot ecosystem will be provided in the third milestone |
| 1. | APK Proof Relayer | **Specification:** Use a Polkadot full node (building upon `bls-beefer` and `polkadot-sdk-solochain-template`) enabled with ecdsa-bls signature scheme for signing BEEFY payload. Upon accumulating sufficient signatures, the full node will extract BLS signatures and generate an APK proof. This APK proof will then be submitted to the APK verifier smart contract (on Kusama AssetHub) via RPC. This approach allows the Polkadot full node to generate BLS signatures and relayer service to generate the cryptographic proof and handle the cross-chain communication, ensuring that the BEEFY consensus remains lean and focused on its core responsibilities. This setup does not require the Polkadot full node itself to be a parachain, as Polkadot does not need to trust it directly; the commitment verification happens in the remote smart contract on the Kusama AssetHub.<br><br>**Verification:** Demonstration of the following: <br>• **1.a:** Enabled Polkadot node signs the BEEFY payload using BLS signature scheme<br>• **1.b:** Relayer pulls the correct signatures, aggregates them, and generates the APK proof<br>• **1.c:** Relayer sends proof along with payload and signature to the target smart contract on Kusama AssetHub<br><br>In this milestone, the node will call a dummy RPC endpoint and ultimately it will call the AssetHub smart contract in the third milestone when actual smart contract is deployed. |


### Milestone 3: Development of APK verifier Smart Contract and Integration

- **Estimated Duration:** - 1 month
- **Full-Time Equivalent (FTE):**  1.0
- **Total Costs:** 10,000 USD

| Number | Deliverable | Specification |
| --: | --- | --- |
| 0a. | License | Apache 2.0 License. All code will be open-sourced under the Apache 2.0 license. |
| 0b. | Documentation | Comprehensive inline code documentation will be provided. A detailed technical design document explaining the Kusama AssetHub smart contract and a tutorial demonstrating the end-to-end functionality of the bridge PoC will also be provided. |
| 0c. | Testing and Testing Guide | Unit tests for all core features of smart contract logic. An integration testing guide will be provided to demonstrate the interaction between all components. |
| 0d. | Docker | Dockerfiles for the APK bridge to facilitate easy setup and testing of the PoC. |
| 0e. | Article | A technical article explaining the contract features, targeting a technical audience within the Polkadot ecosystem. |
| 1. | APK verifier Smart Contract and Integration | **Specification:** Implement BW6 pairings in solidity and write a smart contract that verifies the received SNARK proof of aggregated public keys and BLS signatures. Smart contract will use pairings over BW6 to verify APK + BLS signatures. This contract will update its state with the validated header information. **Verification:** Deployment of the smart contract on Kusama AssetHub (or a testnet). Successful execution of the proof verification function within the smart contract. On-chain state updates reflecting the verified and updated headers. |

### Budget Breakdown

| Category | Item | Cost | Amount | Total | Description |
| --- | --- | --- | --- | --- | --- |
| Personnel | Lead Blockchain Developer | 10,000 USD | 2.25 months | 22,500 USD | Responsible for overall architecture, core development and documentation.|
| \--- | \--- | \--- | **Total** | **22,500 USD** | |

## Future Plans

Upon successful completion of this PoC, our future plans include:

*   **Further Optimization and Hardening:** Refining the APK proof generation and verification processes for even greater efficiency and security.

*   **Validator Set Update Protocol**: Implement a complete trustless protocol for tracking Polkadot relay chain validator set changes on the on-chain light client on Kusama side contract for APK bridge functionality.

*   **Broader Ecosystem Integration:** Collaborate with projects across the Polkadot ecosystem as well as other major chains, including Ethereum, to integrate the APK Bridge approach for a wide range of cross-chain use cases. This includes enabling trustless asset transfers, cross-chain messaging, and decentralized finance interoperability, effectively bridging Polkadot with external projects while maintaining security, efficiency, and scalability. By extending the APK Bridge beyond Polkadot-Kusama, we aim to foster a truly interconnected multi-chain ecosystem.

*   **Research Paper:** Publishing a detailed research paper explaining the entire system, its cryptographic underpinnings, and its implications for trustless interoperability.

## Additional Information

- Some work in progress can be seen in a PR to `w3f/apk-proofs` [PR-47](https://github.com/w3f/apk-proofs/pull/47).
- I declare that this product have not been submitted for funding to any other entities nor received any funding.