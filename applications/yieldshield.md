# YieldShield

## Project Overview

Your savings account is fully insured, you earn a small risk-free yield, and your bank gets rich. What if you could make high DeFi yields completely risk-free with a decentralized insurance protocol? 
That's exactly the problem that YieldShield solves. It's a decentralized, highly capital-efficient insurance protocol that uses a tranche-based risk allocation. It serves as the DeFi abstraction layer, making decentralized finance usable for everyone, and will disrupt traditional savings accounts.

<img src="https://i.postimg.cc/KjJZ0nXJ/yieldshield1.png" alt="YieldShield" width="500"/>

The upcoming deployment of the REVM on the Polkadot Hub will help Polkadot catch up when it comes to DeFi. However, Polkadot currently offers very few advantages and incentives for external teams to bring liquidity to the network. YieldShield on the Hub, offering a unique user experience and significantly increasing the TVL of Polkadot.   

### Project Details

- Technology stack: Solidity, Ponder, Next.js 
- Documentation: https://www.yieldshield.dev/docs/overview 
- Mockups/designs of any UI components

<img src="https://i.postimg.cc/ZYcKYh9W/ys-ui1.png" alt="YieldShield" width="500"/>
<img src="https://i.postimg.cc/jqXdqrWL/ys-ui2.png" alt="YieldShield" width="500"/>
<img src="https://i.postimg.cc/WpnbpPDk/ys-ui3.png" alt="YieldShield" width="500"/>
<img src="https://i.postimg.cc/CMNLMVZG/ys-ui4.png" alt="YieldShield" width="500"/>

- What your project is *not* or will *not* provide or implement:

YieldShield relies on yield-generating protocols like Morpho, Aave, etc., that can be integrated into YieldShield via receipt tokens. Theoretically, these tokens can also be bridged to Polkadot, but ideally, the protocols will be deployed on the hub itself. 

### Ecosystem Fit

- Where and how does your project fit into the ecosystem?

YieldShield offers Polkadot a decentralized insurance protocol, which is a unique feature in the DeFi space and will likely attract additional users. So far, only [Flying Tulip](https://flyingtulip.com/) plans to integrate a [decentralized insurance solution](https://docs.flyingtulip.com/product-suite/ft-insurance/). However, YieldShield has the advantage of not relying on centralized claim assessors or oracles for the claim process and is more capital-efficient. Besides this, YieldShield will be compatible with the upcoming Polkadot Stablecoin and the DeFi products that will integrate it. That way, YieldShield will offer Polkadot users the ability to insure their PUSD and earn yield safely. Finally, YieldShield is also compatible with the products offered in Hydration, as they have a similar receipt token structure to Aave. 

- Who is your target audience (parachain/dapp/wallet/UI developers, designers, your own user base, some dapp's userbase, yourself)?

The initial target will be crypto users who are not DeFi degens. Essentially, users who know how to interact with a chain, but don't invest in DeFi vaults and strategies, because they don't understand the underlying risks. In the future, we aim to collaborate with wallet providers, crypto neo-banks, and other relevant entities.   
  
- What need(s) does your project meet?

Reducing the risk that is associated with DeFi. 
  
- How did you identify these needs? Please provide evidence in the form of (scientific) articles, forum discussions, case studies, or raw data.

- e.g., https://www.accenture.com/content/dam/accenture/final/industry/banking/document/Accenture-Global-Banking-Consumer-Study-2025-Report.pdf. But we have done a lot of research regarding the topic and are happy to share some of our internal research documents. 

- Are there any other projects similar to yours in the Polkadot/Kusama ecosystem? 

[CoverMax](https://github.com/zalatar242/CoverMax-DeFi) also uses a tranch-based insurance protocol. However, as the original [research paper points out](https://arxiv.org/pdf/2212.10308), the design is too complex for regular users, given that they can buy insurance only for a fixed time, have to pay for it upfront, and constantly need to monitor the risk/collateralization.   

- Are there any projects similar to yours in related ecosystems?

[Nexus Mutual](https://nexusmutual.io/) is the only insurance protocol that remains operational. However, they are relatively centralized, operate one big pool, and they depend on claim assessors to decide on a claim.  

## Team

- **Team Name:** YieldShield
- **Contact Name:** David Hawig
- **Contact Email:** info@yieldshield.ai
- **Website:** https://www.yieldshield.dev/

### Team members

#### LinkedIn Profiles 

- https://www.linkedin.com/in/david-hawig-206a44b1/
- (happy to share the other members on a call or via email)

### Team Code Repos

- https://github.com/YieldShield (still private)

Please also provide the GitHub accounts of all team members. If they contain no activity, references to projects hosted elsewhere are also fine.

- https://github.com/Noc2

### Team's experience

David Hawig worked for the Web3 Foundation for over six years and was responsible for creating the initial version of this template. All team members possess extensive knowledge of Polkadot.  

## Development Status

Academic publications relevant to the problem: 
- https://arxiv.org/pdf/2212.10308
- https://arxiv.org/pdf/2410.09341
  
Previous interface iterations, such as mock-ups and wireframes:
- see the above images

## Development Roadmap

### Overview

- **Estimated Duration:** 3 Months
- **Full-Time Equivalent (FTE):**  1 FTE
- **Total Costs:** 24,000 USD

### Milestone 1: Core Logic

- **Estimated duration:** 2 months
- **FTE:**  1
- **Costs:** 16,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | GPLv3 |
| 0b. | Documentation | We will provide both **inline documentation** of the code and a basic **tutorial** that explains how a user can... See the [delivery guidelines](https://github.com/PolkadotOpenSourceGrants/delivery/blob/master/delivery-guidelines.md#documentation) for details. |
| 0c. | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness. In the guide, we will describe how to run these tests. See the [delivery guidelines](https://github.com/PolkadotOpenSourceGrants/delivery/blob/master/delivery-guidelines.md#testing-guide) for details. |
| 0d. | Docker | We will provide a Dockerfile(s) that can be used to test all the functionality delivered with this milestone. |
| 0e. | Article | We will publish an **article** that explains how users on Polkadot are able to use the product in the future. |
| 1. | SplitRiskPool.sol | We will create a Solidity smart contract that has two withdrawal and two deposit functions, one each for users and one for underwriters. The smart contract divides the risk into insured tokens, which can be immediately withdrawn at any time, and underwriter tokens, which earn an additional commission but have a 28-day lock-in period before they can be withdrawn. The smart contract will be thoroughly tested and implement various security measures (such as SafeERC20, OpenZeppelin Math, ReentrancyGuard, etc.), as well as the necessary view functions for the UI, and the ability to set limits for maximum and minimum withdrawals. Additionally, tokens need to be whitelisted for SplitRiskPool.sol   |
| 2. | SplitRiskPoolFactory.sol | The factory contract for deploying and managing SplitRiskPool instances, including the necessary view functions, the logic to validate pools, and to create pools.  |
| 3. | Next.js Front-end | We will develop a UI based on the above mock-ups that allows users to interact with the SplitRiskPool as well as the SplitRiskPoolFactory. The charts will initially serve as placeholders. |
| 3. | Deployment| The smart contract will be deployed on either the Polkadot Hub test network or, if any issues arise, on the Moonbeam test network. The front-end will directly interact with the deployed testnet version |

### Milestone 2: Ponder

- **Estimated duration:** 1 months
- **FTE:**  1
- **Costs:** 8,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | GPLv3  |
| 0b. | Documentation | We will provide both **inline documentation** of the code and a basic **tutorial** that explains how a user can. |
| 0c. | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness. In the guide, we will describe how to run these tests. See the [delivery guidelines](https://github.com/PolkadotOpenSourceGrants/delivery/blob/master/delivery-guidelines.md#testing-guide) for details. |
| 0d. | Docker | We will provide a Dockerfile(s) that can be used to test all the functionality delivered with this milestone. |
| 0e. | Article | We will publish an **article** that explains how to use Ponder for a Polkadot Hub or Moonbeam project |
| 1. | Ponder | We will integrate https://ponder.sh/ into the project and implement the indexing solution to index all events. |
| 2. | Next.js Front-end | The front-end will no longer query data from the RPC node, but rather rely on the indexing solution. It will be able to show diagrams |
| 3. | Deployment| The smart contract will be deployed on either the Polkadot Hub test network or, if any issues arise, on the Moonbeam test network. The indexer will index events from the smart contract deployed on the testnet. |

### Budget Breakdown 


| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Full-Stack Developer | 8,000 USD | 1 FTE | 24,000 USD | We estimate that one person works on this for three months |
| --- | --- | --- | **Total** | **24,000 USD** |  |


## Future Plans

We are currently in the process of raising an angel round and plan to follow up with a seed round. The protocol itself will charge a small fee in the future that will long-term finance it. The project will mostly be promoted via cooperation with other protocols that we integrate with or teams that benefit from our services. 

## Additional Information

We haven't received any other funding so far, and want to deploy also on Polkadot simply because of our knowledge of the ecosystem. We believe the upcoming DeFi ecosystem in Hub will significantly benefit from a secure insurance protocol like YieldShield.
