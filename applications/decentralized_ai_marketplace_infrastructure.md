# Decentralized AI Marketplace Infrastructure 

- **Team Name:** Caibrain Labs
- **Payment Details:**
  - **DOT**:16S6Dtj6ZgefFvABokxfyoM1cEM7gvxqxf94AvoCEe9DrZ9b
- **Requested DOT:** 30K USD in DOTs.

## Project Overview :page_facing_up:

The project was formerly known as Deitos Network that started as a decentralized big data & AI platform adquired a Web3 Foundation grant listed below:

https://github.com/w3f/Grants-Program/blob/master/applications/Deitos_Network.md
Deitos Network has transitioned into a more dedicated AI services platform focused on a marketplace of model inferences that is the purpose of this grant.

### Overview

The Decentralized AI Marketplace Infrastructure is a utility that enables any Polkadot-SDK-based network to implement an AI model ownership framework where model owners can deploy their models on a decentralized network of infrastructure providers and offer inferences to any consumer needing to embed AI services into their solutions. Key features of this tool include:
- Model ownership and management in form of NFT.
- A marketplace for AI models inferences offered by infrastructure providers.
- An automated bot in charge of  bidding engine to provide the best rates for inferences when more than one provider offers the same model inferences.
- User agreements between consumers and infrastructure providers for a fixed cost for a fixed number of inferences.
- On-chain and off-chain Polkadot-SDK integration for transmitting input and output messages.

***Project Motivation:*** 
The AI explosion in 2022 clearly demonstrated the perfect match between AI and blockchain and the need to make AI more accessible with fairer resource distribution across all participants. Currently, AI is highly concentrated in the hands of big players who not only have the resources to train massive models but also the influence to dominate the market, often pushing startups and mid-sized companies aside. To address this, it is critical to provide communities with better access to resources, enabling them to compete and shifting the ownership of this key technology from large corporations to decentralized communities. This project would ensure a fairer distribution of resources and promote wider participation in AI development.

### Project Details

Conceptually the AI inferences marketplace supports 3 different actors:

- Model Owners: User(s) that register the model ownership on-chain receiving royalties for every inference executed from its model. Their ownership secured by NFTs minted on the blockchain. 
- Infrastructure providers: Provide the necessary infrastructure to deploy and offer a model inference.
- Consumers: End users needing AI inferences for different purposes.

<img width="843" alt="upload_415b196befed33f5b63d5096f9d0c927" src="https://github.com/user-attachments/assets/00b02718-1d6a-4a91-95ce-41702919c8e5" />

These actors are coordinated and orchestrated by the blockchain powered by the Polkadot-SDK framework, which tracks agreements and interactions among them. However, it is important to note that the blockchain alone is not sufficient to complete the entire process of a user requesting an inference from a model and the model returning the response back to the user.

For this reason, certain services need to be deployed on the infrastructure provider's side to handle off-chain AI activities. These activities will eventually be registered on the blockchain.

### User Flow:

<img width="1085" alt="upload_75168ddf02295aa21ab48b2f35c2980a" src="https://github.com/user-attachments/assets/a143ba40-c494-486c-b6fb-15db959e6dad" />

Each model can be hosted by multiple infrastructure providers, ensuring fair competition for the best price and service for consumers needing inferences for a specific model.

The process begins with the consumer placing a request for a specific number of inferences for a model. This provides the consumer with predictability regarding costs over a certain period.

Once the network registers the request for a given number of inferences for a model, each infrastructure provider starts bidding to offer the best rate. This allows the consumer to select the most cost-effective deal. For example, **Infrastructure Provider #1** is likely to be selected as it offers the best rate per inference.

However, it is important to highlight that managing multiple requests manually would require significant effort from infrastructure providers. Monitoring every network request and manually bidding for each one would be inefficient. To solve this, every infrastructure provider operates bidding engine that listens for incoming requests on the network. This engine automates the bidding process, allowing providers to respond quickly and efficiently.

With all bids available, the consumer can then select the infrastructure provider that best fits their needs and once confirmed, the agreement among both actors is ready to start sending inferences request to the infrastructure provider that won the auction.

## Architecture & Design

**Wingman**

To enhance usability and reduce operational costs on the blockchain, the project offers an automation bot called Wingman. Wingman can operate within the same ecosystem that hosts a full node and dockerized AI models. The bot provides a RESTful API, allowing for easy initialization and real-time configuration adjustments. Once properly configured, Wingman automates the provider’s operations on the network, monitoring the blockchain and responding accordingly. Its functions include bidding on market orders, tracking active agreements, and executing AI models.

![upload_7c9833965c7d8579e8a7352203600c89](https://github.com/user-attachments/assets/7ad77283-2aee-4a07-bb6d-a10938ad1a3b)

### DX Network 
Since model payloads can be large and the blockchain itself is not suitable for transferring substantial data, this solution introduces a separate peer-to-peer network for data exchange (Dx). This network is optimized for the quick sharing of relatively small data off-chain. The current implementation is embedded within the Polkadot-SDK node and accessible through an RPC API relying on two methods:

**dx_upload(key, data)** method uploads arbitrary data to the network under the specified key, which is the hash of the data being uploaded.

**dx_download(key)** method performs a search for the data by its hash on the network and returns to the caller.

### Execution

Once the agreement between the consumer and provider is established, the consumer obtain  AI models inferences using the provider’s infrastructure. This is done by posting the request’s payload on the Dx network and registering its hash on the blockchain. The provider is notified of the new request, downloads the payload, executes the specified AI model, and sends back the response. The response follows the same procedure as the request: it is uploaded to the Dx network, and its hash is recorded on the blockchain. Upon completion of this process, the model owner receives their royalty payment.

![upload_417f0036280aec525312e91565aceb2b](https://github.com/user-attachments/assets/4d4f0816-5e25-4132-9533-1847589bbe18)

### Ecosystem Fit

Help us locate your project in the Polkadot/Substrate/Kusama landscape and what problems it tries to solve by answering each of these questions:

- **Where and how does your project fit into the ecosystem?**

AI is becoming important in many areas like businesses, organizations, and foundations. Our project provides a decentralized infrastructure to host AI models, allowing any Polkadot-based project to use a safe and distributed platform for their AI needs.

- **Who is your target audience (parachain/dapp/wallet/UI developers, designers, your own user base, some dapp's userbase, yourself)?**

Because AI model inferences can be used in many ways, our project's target audience is wide. It includes parachain developers, dapp developers, wallet developers, UI developers, designers, and more.

- **What need(s) does your project meet?**

Right now, big companies control most AI services. This makes it hard for decentralized projects that need AI, because relying on big tech companies can risk their independence. Our project solves this by building a decentralized AI infrastructure that rewards everyone who participates, making sure it's fair for everyone involved.

- **How did you identify these needs? Please provide evidence in the form of (scientific) articles, forum discussions, case studies, or raw data.**

- [AI in the Public Interest: Confronting the Monopoly Threat](https://www.openmarketsinstitute.org/publications/report-ai-in-the-public-interest-confronting-the-monopoly-threat)
- [Evaluating Natural Monopoly Conditions in the AI Foundation Model Market](https://www.rand.org/content/dam/rand/pubs/research_reports/RRA3400/RRA3415-1/RAND_RRA3415-1.pdf)
- [Nvidia DOJ Investigation: AI](https://www.theguardian.com/commentisfree/2024/sep/13/nvidia-doj-investigation-ai)
- [Shaping the Future of Generative AI](https://www.linuxfoundation.org/blog/shaping-the-future-of-generative-ai)
- [Decentralized AI: The Power and the Necessity](https://computing.smu.edu.sg/newsletter/decentralized-ai-power-and-necessity)

- **Are there any other projects similar to yours in the Substrate / Polkadot / Kusama ecosystem?**
  - **If so, how is your project different? Please identify and assess any projects addressing the same need and explain how your project is distinct. Feel free to include applicable research data, statistics, or metrics.**
  - **If not, please indicate why such a project might not have been possible, successful, or attempted.**

The closest project in the Polkadot ecosystem is, in our opinion, **Phala Network**, because it focuses on privacy and security in AI. Phala uses Trusted Execution Environment (TEE) technology to make sure AI runs securely and privately, protecting data from unauthorized access. This solves trust issues in decentralized AI by providing secure computing solutions.

Privacy in AI is very important right now, and  technologies like Trusted Execution Environment (TEE), Fully Homomorphic Encryption (FHE), or Zero-Knowledge Machine Learning (ZKML) are being closely studied. Although Phala is one of the most advanced in this area, TEE technology has faced some concerns about security. Still, we think it offers the best balance between performance and security.

Our **Decentralized AI Marketplace** infrastructure does not force any specific privacy technology. It allows different privacy technologies to be integrated because its off-chain messaging system is flexible enough to support any kind of encrypted message.

- **Are there any projects similar to yours in related ecosystems?**

In other ecosystems, there are several projects with similar goals:

**0G**

0G is a decentralized AI operating system designed to provide scalable infrastructure for AI and Web3 applications. It offers a modular architecture that enables seamless interoperability between different blockchain networks, aiming to eliminate fragmentation and enhance connectivity.

**Sahara AI**

Sahara AI is a decentralized blockchain platform that enables individuals and organizations to create, share, and monetize AI models, datasets, and applications collaboratively. It emphasizes data ownership, security, and equitable compensation for contributors, fostering a transparent and inclusive AI ecosystem.

**Fetch.AI**

Fetch.AI is an open platform that provides tools for building and deploying AI applications and services at scale. It focuses on creating autonomous AI agents capable of performing various tasks, facilitating automation across industries. 

> Please note that the data provided in this section is for administrative and informational purposes only. All beneficiaries of a grant must also be listed in the KYC/KYB process during the application phase. See our [FAQ](https://grants.web3.foundation/docs/faq#what-is-kyckyb-and-why-do-i-have-to-provide-this-data) for more info.

### Team members

- Hector Bulgarini: Senior Software Developer and Team Lead
- Hernan Borelli: Product & Project Manager
- Alexander Kalankhodzhaev: Senior Blockchain and protocol Engineer

### Contact

- **Contact Name:** Hector Bulgarini / Hernan Borelli
- **Contact Email:** contact@caibrainlabs.com
- **Website:** https://caibrainlabs.com/

### Legal Structure

- **Registered Address:** To be provided privately with curators.
- **Registered Legal Entity:** To be provided privately with curators.
  
### Team's experience

Hector: With over 15 years in the technology sector, Hector focused on blockchain and Polkadot tech stack evidenced by his work at Parity and the graduation from the first Cambridge cohort of the Polkadot Academy. Hector also have founded and led multiple startups showing a strong entrepreneurial spirit.

Hernan: Hernan holds a degree in project management and development. Since 2020, he has been deeply involved in promoting and developing the Polkadot ecosystem in Spanish-speaking countries.

Alex: With a rich experience spanning over 15 years as a software engineer, Alex has worked across various companies and domains. For the past 5 years, he has specialized as a blockchain engineer. Alex is a significant contributor to a substrate node developed in Java, which can be found here: substrate-client-java.

Additionally, he currently maintains GO-LINQ, a language integrated query (LINQ) library for Go. More about it can be found here: GO-LINQ.

### Team Code Repos

- Alex: https://github.com/kalaninja
- Hector: https://github.com/hbulgarini

### Team Code Repos

https://github.com/caibrain-labs?tab=repositories

### Team LinkedIn Profiles

- Hector: https://www.linkedin.com/in/hector-bulgarini/
- Hernan: https://www.linkedin.com/in/hernan-borelli-62296261
- Alex: https://www.linkedin.com/in/kalaninja/


## Development Status :open_book:

The code is nearly complete; however, we are currently in the final phase of preparing some features from the product perspective, completing documentation, and reviewing the most recently added functionalities.

You can find some of Deitos Network’s previous code here:
https://github.com/Deitos-Network

It’s important to note that significant changes have been made on the infrastructure providers side, reflecting a new strategic focus taken by the project stated in this grant.

## Development Roadmap :nut_and_bolt:

### Overview

- **Total Estimated Duration:** 4 weeks
- **Full-Time Equivalent (FTE):**  3 FTEs
- **Total Costs:** 30,000 USD.


### Milestone 1 Example — Basic functionality

- **Estimated duration:** 1 month
- **FTE:**  3
- **Costs:** 30,000 USD

> :exclamation: **The default deliverables 0a-0d below are mandatory for all milestones**, and deliverable 0e at least for the last one.

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 
| **0b.** | Documentation | We will provide both **inline documentation** of the code and a basic **tutorial** that explains how a user can start an environment with two infrastructure providers that have a [resnet](https://huggingface.co/docs/transformers/model_doc/resnet) model available. |
| **0c.** | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness. In the guide, we will describe how to run these tests. |
| **0d.** | Docker | We will provide a Dockerfile(s) that can be used to test all the functionality delivered with this milestone. |
| **0e.** | Article                     | We will publish an **article** detailing the architecture of the marketplace, including potential privacy features that could be incorporated in the future.                     |
| 1.  | Airo Node (Substrate Node)  | All business logic, ownership models, and incentives will reside within a Substrate node, serving as the foundational layer for all the workflows described. This node's runtime will include the NFT pallet, which will represent model ownership.                                                         |
| 2.  | Execution Pallet            | This pallet is a core component of the AI marketplace. It manages the execution and coordination with the Dx Network when running model inference per agreed terms. Additionally, it handles agreement registration between consumers and infrastructure providers.                                          |
| 3.  | Marketplace Pallet          | This pallet manages new agreement requests and negotiations between consumers and infrastructure providers. It records all interactions                     |
| 4.  | Dx Network                  | The Substrate node will include a fully implemented Substrate RPC with its own Kademlia P2P network, supporting the `dx_upload` and `dx_download` calls outlined in the architectural design.   |
| 5.  | Wingman                     | Automation of the bidding process for infrastructure providers will be managed by the Wingman service, included in this grant. The service will expose a RESTful API, enabling communication between the Substrate node and infrastructure providers.  |
| 6.  | Cockpit                     | A simple adaptation of the Substrate Frontend template with the react components setup to interact with the marketplace. |


## Future Plans

The primary goal of this grant is to offer the Polkadot community an out of the box solution for any team looking to implement their own AI Marketplace inferences and to serve this need not only in the Polkadot ecosystem, but also to even not-blockchain projects. 

In future grants or funding the following features could be added to the AI marketplace infrastructure:

- Models registration workflow and benchmarking.
- Enhanced UI with infrastructure provider/model owner stats.
- Add support for one privacy feature such as FHE for private inferences.

## Additional Information :heavy_plus_sign:

**How did you hear about the Grants Program?** Web3 Foundation Website / Medium / Twitter / Element / Announcement by another team / personal recommendation / etc.

As mentioned before, the project was formerly known as Deitos Network that started as a decentralized big data & AI platform adquired a Web3 Foundation grant listed below:

https://github.com/w3f/Grants-Program/blob/master/applications/Deitos_Network.md

Also as we are deeply involved with the Polkadot ecosystem, we followed all the converstaions and updates about the progress of this bounty.
