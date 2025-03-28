# Dedot

## Project Overview :page_facing_up:

### Overview

[Dedot](https://dedot.dev/) (previously named DelightfulDot) is a next-generation JavaScript client for [PolkadotSDK](https://github.com/paritytech/polkadot-sdk)-based blockchains, designed to address the complexities and overhead developers often encounter when building applications in the Polkadot ecosystem. 

The project began with [our first proposal to the W3F Grants Program](https://github.com/w3f/Grants-Program/pull/1907), which focused on building the foundations for a lightweight JavaScript client. The initial motivation was addressing the high memory consumption of existing solutions like [`@polkadot/api`](https://github.com/polkadot-js/api), especially when connecting to multiple networks simultaneously. This posed challenges for applications like wallets and portfolio trackers that need to connect to dozens or hundreds of networks. The first proposal successfully delivered the core architecture.

After successfully delivering the first proposal, we have continuously maintained and enhanced Dedot by adding more features & integrations such as:
- Support Metadata V15 & exposing fully typed Runtime Apis while still maintaining the backward compatibility with Metadata V14,
- Integrating [new JSON-RPC specifications](https://paritytech.github.io/json-rpc-interface-spec/introduction.html) while also keeping the support for legacy JSON-RPC.
- Enabling support for fully typed ink! smart contract interactions, integrating with Smoldot allowing dapps to smoothly connect with networks via light client, etc...

This progress so far underscores the practical need for a robust, developer-friendly library that remains closely aligned with ongoing protocol changes. With this follow-up proposal, we are seeking funding to continue the development of Dedot with new features and improvements. We intend to build on the foundations of Dedot by further refining its features and future-proofing it against forthcoming network developments. Our goal is to make the library more resilient, easy to integrate, and flexible, we believe Dedot will continue serving as a high-quality, go-to solution for JavaScript and TypeScript developers in the Polkadot ecosystem.

### Project Details

We propose to continue improving & adding more features & integrations into Dedot:

#### 1. Client API Improvements
 
We plan to improve the current Client APIs ([DedotClient](https://github.com/dedotdev/dedot/blob/main/packages/api/src/client/DedotClient.ts) & [LegacyClient](https://github.com/dedotdev/dedot/blob/main/packages/api/src/client/LegacyClient.ts)), which is built on top of both new & legacy JSON-RPC specs.
- [ChainHead API](https://paritytech.github.io/json-rpc-interface-spec/api/chainHead.html) Enhancements
  - Shared operations for parallel requests to the same on-chain resource (e.g., system events): This helps reduce bandwidth usage and avoids repeating work when different requests need access to the same data.
  - Automatic resubscription after reconnecting to a node: At the moment, subscriptions don't automatically recover when the connection is lost and then restored. Supporting this will make dapps more reliable in these situations, so developers don't have to manually handle resubscriptions.
- Transaction API Improvements
  - Better [SignerOptions](https://github.com/dedotdev/dedot/blob/ffd825052f48fdaeb26e4a66fc38cbec8f6a9580/packages/types/src/extrinsic.ts#L7-L21) for signing transactions:
    - Add support for custom asset type on chains using the [`ChargeAssetTxPayment`](https://github.com/paritytech/polkadot-sdk/blob/98c6ffcea6794d338514cf9bd84446d2f276cb63/substrate/frame/transaction-payment/asset-tx-payment/src/lib.rs#L174-L180) extension, allowing devs to define which assets can be used to pay fees.
    - Allow customization of signing block hash/number, transaction mortality, ... providing developers with greater flexibility when constructing transactions.
  - Default support for TransactionExtension (SignedExtension) that don't require external input when creating transactions.
    - For example, here is a list of [known extensions](https://github.com/dedotdev/dedot/tree/main/packages/api/src/extrinsic/extensions/known) supported by Dedot. If the connected network requires a different extension that doesn't need external data or input, Dedot can support it internally—eliminating the need for developers to define a new explicit extension when initializing clients.
  - Convenient chaining methods for transaction handling, such as: `untilBestChainBlockIncluded`, `untilFinalized`
    - For example, if developers need to submit a transaction and wait until it is finalized
      ```ts
        const client = await DedotClient.new(new WsProvider('wss://...')))
        client.tx.system.remark('Hello W3F')
            .signAndSubmit(alice, { signer }, ({ status }) => {
              if (status.type === 'Finalized') {
                // Do something when the transaction is finalized
              }
            })
      ```
    - With the chaining methods, it will be much more convenient to do so:
      ```ts
        const client = await DedotClient.new(new WsProvider('wss://...')))
        await client.tx.system.remark('Hello W3F')
            .signAndSubmit(alice, { signer })
            .untilFinalized();
        // Do something when the transaction is finalized
      ```

#### 2. `archive_*` prefixed JSON-RPC Integration

The [archive_* JSON-RPC methods](https://paritytech.github.io/json-rpc-interface-spec/api/archive.html) are set to [stabilize](https://forum.polkadot.network/t/stabilizing-the-archive-rpc-v2-methods/12058) soon, making it possible for developers to query historical blockchain data more easily. This unlocks a wider range of use cases like historical analysis and indexing—without relying on legacy JSON-RPC endpoints or building custom solutions.

We plan to:
- Improve the [`.at`](https://github.com/dedotdev/dedot/blob/ffd825052f48fdaeb26e4a66fc38cbec8f6a9580/packages/api/src/client/DedotClient.ts#L191-L197) method to accept finalized block hashes to create a SubstrateClient at a specific finalized block in the past allowing Storage Queries or Runtime Api executions, etc...
- Support [`.entries`](https://github.com/dedotdev/dedot/blob/ffd825052f48fdaeb26e4a66fc38cbec8f6a9580/packages/types/src/generic.ts#L110-L115) storage queries for finalized block hashes by falling back to archive JSON-RPCs when needed.
- Enable storage queries using `.pagedKeys` and `.pagedEntries` for working with large storage efficiently with pagination.

```ts
const client = await DedotClient.new(new WsProvider("wss://..."));

const finalizedBlockHash = '0x...';
const clientAt = client.at(finalizedBlockHash);

// fetch all nft item entries
await clientAt.query.nfts.item.entries()

// fetch a page of 10 nft item keys
await clientAt.query.nfts.item.pagedKeys({ pageSize: 10, startKey: '0x...' })

// fetch a page of 10 nft item entries
await clientAt.query.nfts.item.pagedEntries({ pageSize: 10, startKey: '0x...' })
```

#### 3. Metadata V16

The [new Metadata V16](https://github.com/paritytech/frame-metadata/blob/main/frame-metadata/src/v16.rs) introduces significant updates to the structure of metadata for Extrinsics, Pallets, and Runtime APIs. Supporting Metadata V16 lays the groundwork for upcoming features such as the new Transaction Format V5 and pallet view functions.

#### 4. New Transaction Format (v5)

Polkadot recently introduced the new [Transaction Format V5](https://github.com/paritytech/polkadot-sdk/pull/3685), which includes a more general transaction structure (without a signature) and updated terminology: Transaction (formerly Extrinsic) and Transaction Extension (formerly Signed Extension), now with [versioning support](https://github.com/polkadot-fellows/RFCs/pull/99).

We plan to update Dedot to fully support these changes while maintaining backward compatibility with the existing Extrinsic V4 format. This will help ensure Dedot stays aligned with evolving on-chain transaction standards.

#### 5. Pallet View Function
 
Another upcoming feature that's set to be stabilized soon is [Pallet View Functions](https://github.com/paritytech/polkadot-sdk/pull/7960) ([Forum Discussion](https://forum.polkadot.network/t/wasm-view-functions/1045)). These are read-only functions that allow access to a pallet's state from both inside and outside the runtime. They aim to provide a stable interface for querying pallet state without relying on direct storage access while evolving alongside the runtime.

Planned works:
- Organize view functions under a dedicated namespace, e.g: `client.views.[pallet].[function_name]`
- Automatically generate types and APIs for view functions when running [`dedot chaintypes`](https://docs.dedot.dev/cli#dedot-chaintypes) CLI
- Implementing execution and subscription to view functions

### Ecosystem Fit

#### Benefits of Dedot

Dedot provides JavaScript/TypeScript developers with a powerful yet efficient toolkit for building high-performance dapps in the Polkadot/Substrate ecosystem:

- **Memory Efficiency:** Significantly lower memory footprint enabling connections to multiple networks simultaneously without performance degradation - essential for wallets, portfolio trackers, and cross-chain dapps
- **Dual JSON-RPC Support:** Supports both new and legacy JSON-RPC specifications, allowing applications to work with networks at different upgrade stages and providing a gradual transition path
- **TypeScript-First Design:** Full type safety with auto-generated types from on-chain metadata, reducing errors and improving developer productivity
- **Modern API Design:** Intuitive, promise-based APIs with convenient chaining methods that align with contemporary JavaScript practices
- **Simplified Smart Contract Integration:** First-class support for ink! smart contracts with type-safe interfaces, eliminating the complexity of manual ABI handling
- **Light Client Support:** Native integration with Smoldot enables truly decentralized browser-based applications without relying on centralized RPC endpoints
- **Flexible Type System:** The [`@dedot/chaintypes`](https://docs.dedot.dev/getting-started/connect-to-network#pick-chainapi-interface-for-the-network-youre-working-with) package exposes Types & APIs for known supported chains for immediate development without additional setup steps

#### Alternative Solutions

##### Polkadot.js API (`@polkadot/api`)

[`@polkadot/api`](https://github.com/polkadot-js/api) has been the standard JavaScript interface for Substrate-based chains since the early days of the ecosystem. While widely adopted, it has certain limitations that Dedot aims to address. For a detailed analysis of these limitations, please refer to our [forum post on the limitations of Polkadot.js API](https://forum.polkadot.network/t/introducing-dedot-a-delightful-javascript-client-for-polkadot-substrate-based-blockchains/8956#p-20513-limitations-of-polkadotjs-api-polkadotapi-or-pjs-2).

Dedot maintains a similar API styling to Polkadot.js API, making migration easier for existing dapps with large codebases that would find it difficult to switch to a completely different syntax.

##### Polkadot-api (PAPI)

[PAPI](https://papi.how/) is another alternative solution addressing similar challenges:

- Focuses exclusively on the new JSON-RPC specifications
- Requires generating descriptors for types via CLI
- Clean-slate approach with different API patterns

The diversity of JavaScript/TypeScript clients in the ecosystem creates a healthy environment where developers can choose tools that match their specific requirements and preferences. Different approaches to similar problems drive innovation across all solutions, making the ecosystem more resilient by not depending on a single implementation.

By providing these capabilities, Dedot directly contributes to the Polkadot ecosystem's growth by enabling developers to build more sophisticated, performant, and user-friendly applications while ensuring smooth transitions as the underlying protocols evolve.

## Team :busts_in_silhouette:

- Team Name: Dedot Dev Team
- Contact Name: Thang X. Vu
- Contact Email: thang@dedot.dev
- Website: https://github.com/dedotdev

### Team members

- Thang X. Vu (Team Leader) - https://github.com/sinzii
- Tung Vu - https://github.com/1cedrus

### Team's experience

Dedot is a small but highly specialized team with extensive experience in JavaScript/TypeScript development and Polkadot ecosystem tooling. Founded with a mission to bring Web3 closer to the world, our team combines technical expertise with a practical understanding of developer needs in the blockchain space, consistently delivering high-quality, well-documented & tested code.

We have successfully delivered multiple grant-funded projects through the [W3F Grants Program](https://github.com/w3f/Grants-Program):

- [Typink](https://grants.web3.foundation/applications/typink): a fully type-safe React hooks library designed to accelerate ink! dApp development.
- [Dedot](https://grants.web3.foundation/applications/delightfuldot): a next generation Javascript Client for Polkadot & Substrate.
- [Coong Wallet](https://grants.web3.foundation/applications/coong_wallet): a website-based wallet solution to address the inconsistent wallet experience on mobile & desktop and bring a new approach to onboard new users to Polkadot & Kusama ecosystem.

### Team Code Repos

Project repositories will be hosted at https://github.com/dedotdev/dedot

## Development Status :open_book:

Our initial W3F grant proposal established the core architecture of Dedot. We successfully delivered all milestones, creating a solid foundation with support for Metadata V14, JSON-RPC interactions, and essential client APIs.

Since completing the initial grant, we've been actively expanding Dedot with new features and integrations to keep it aligned with the fast-moving Polkadot ecosystem. This includes:
- Supported Metadata V15 along with full exposure to Runtime APIs.
- Integrated the [latest JSON-RPC specification](https://paritytech.github.io/json-rpc-interface-spec/introduction.html).
- Supported seamless integration with ink! contracts, making it easier for dapp developers to interact with smart contract logic in a type-safe and developer-friendly way.
- Supported the Smoldot light client, enabling secure on-chain access directly from the browser.

With this follow-up proposal, we aim to build upon these foundations by implementing support for the latest protocol changes and adding new features that will keep Dedot at the forefront of JavaScript/TypeScript tooling for the Polkadot ecosystem. As the ecosystem continues to evolve with new transaction formats, metadata versions, and API specifications, it's crucial that developer tooling evolves alongside it to ensure seamless adoption of these improvements.

## Development Roadmap :nut_and_bolt:

### Overview

- **Total Estimated Duration:** 3 months
- **Full-Time Equivalent (FTE):**  1.5 FTE
- **Total Costs:** 30,000 USD

### Milestone 1: Client Improvements

- **Estimated duration:** 1.5 months
- **FTE:**  1.5
- **Costs:** 15,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | We will provide both **inline documentation** of the code as well as **online documentation** related to changes in this milestone on https://docs.dedot.dev |
| **0c.** | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness. In the guide, we will describe how to run these tests. |
| 1. | Client API Improvements | We'll deliver improvements as described in [Client API Improvements](#1-client-api-improvements)  |
| 2. | `archive_*` JSON-RPC V2 Integration | We'll deliver the integration as described in [`archive_*` prefixed JSON-RPC Integration](#2-archive_-prefixed-json-rpc-integration) |
| 3. | Support Metadata V16 | We'll deliver the support for new metadata as described in [Metadata V16](#3-metadata-v16) |


### Milestone 2: New Features & Integrations

- **Estimated duration:** 1.5 months
- **FTE:**  1.5
- **Costs:** 15,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | We will provide both **inline documentation** of the code as well as **online documentation** related to changes in this milestone on https://docs.dedot.dev |
| **0c.** | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness. In the guide, we will describe how to run these tests. |
| 1. | New Transaction Format (v5) Integration | We'll deliver the integration and support for [new Transaction Format V5](#4-new-transaction-format-v5)  |
| 2. | Pallet View Function | We'll deliver the view functions as described in the [Pallet View Function](#5-pallet-view-function) |


### Budget Breakdown

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Full-Stack Developer & Team Lead | 21,000 USD | 1 FTE | 21,000 USD | leading project with tech architecture for the full 3-month period |
| Personnel | Full-Stack Developer | 18,000 USD | 0.5 FTE | 9,000 USD | focused on execution and implementation for the full 3-month period |
| --- | --- | --- | **Total** | **30,000 USD** |  |

## Future Plans

- Continue to adopt latest changes
- XCM Utilities
- Compact Metadata
