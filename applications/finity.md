# Finiti Analytics

## Project Overview  

**Tagline:**  
*Institutional-grade data and analytics for the Polkadot ecosystem.*  

**Brief Description:**  
Finiti Analytics is a next-generation analytics platform delivering institutional-grade data, research, and insights into the blockchain and digital asset ecosystem. With this proposal, we aim to build advanced, interactive dashboards for Polkadot that provide real-time intelligence on network activity, validator performance, staking, treasury flows, and economic metrics.  

The dashboards will empower investors, developers, researchers, and policymakers with transparent and actionable insights into Polkadot’s on-chain activity, protocol health, and market dynamics. 
![alt text](https://www.notion.so/image/attachment%3Ab58de14d-dfcc-4871-b97a-d5aa11d3e6b3%3A15976247-e003-4ac2-8cb7-2f6c32fd9682.png?table=block&id=1d937d64-d8bc-802b-8fa6-c4289a801d62&spaceId=aab87fb6-78d5-40ca-824f-a6c7886402b7&width=1190&userId=&cache=v2) 

**Relation to Polkadot/Kusama:**  
Our project will integrate directly with the Polkadot ecosystem by connecting to relay chain and parachain nodes, extracting raw data via **Node Metrics Exporters**, storing metrics with **Prometheus**, and visualizing them in **Grafana dashboards**. 

**Why We Are Interested:**  
As long-term contributors to decentralized technologies, our team recognizes the critical need for accessible, high-quality analytics in the Polkadot ecosystem. Current solutions are fragmented, limited in scope, or difficult to navigate. By reducing informational friction and presenting comprehensive, verifiable data, we will foster a more transparent, data-driven environment for ecosystem participants.  

## Project Details

### Objective

Despite the growing availability of blockchain data, the crypto ecosystem continues to suffer from a lack of comprehensive, accessible, and high-quality analytics. While numerous dashboards, blogs, and communication channels attempt to surface insights, gaining a clear and cohesive understanding of on-chain activity and protocol-level developments remains a significant challenge.  

This fragmentation creates a high barrier to informed decision-making. Without a centralized, data-rich environment, investors, developers, and users often operate with an incomplete picture—resulting in the misallocation of resources, both in terms of time and capital.  

**Finiti Analytics Dashboards** aim to address this gap by delivering unified, intuitive, and actionable analytics tools that empower stakeholders to make decisions based on **real-time, data-driven insights**. By reducing informational friction and increasing transparency, these dashboards will play a critical role in improving decision quality across the blockchain ecosystem.  


### Dashboard Metrics

The dashboards will feature a broad set of key performance indicators across several domains. These will include but not limited to the following: 

#### **Overall Network Activity**
- **Active accounts** (wallets engaging in transfers, staking, governance, etc.)  
- **Extrinsics submitted** (transfers, staking ops, governance votes, XCM messages)  
- **Cross-chain transfers (XCM messages)** between parachains and the relay chain  
- **Relay chain throughput & block time consistency** (6s block production target)  

#### **Decentralization & Staking**
- **Active validators on the relay chain** (~400 max)  
- **Total DOT staked**  
- **Staking ratio** (percentage of circulating DOT staked)  
- **Nominator distribution & validator concentration** (stake spread across validators)  
- **Parachain slot distribution** (number of parachains, category diversity)  

#### **Financial & Economic Metrics**
- **DOT circulating vs. total supply** (inflationary tokenomics)  
- **Market capitalization of DOT**  
- **Staking rewards & inflation rate** (annualized issuance for staking)  
- **Network fees & burned DOT** (transaction fees, slashing, governance costs)  
- **Treasury balance & historical expenditures** (funded by slashing, fees, inflation)  
- **Parachain crowdloan funds raised** (DOT locked for parachain slots)  

---

### Architecture

The **Finiti Analytics platform** is built on a modular and scalable architecture designed to collect, process, and visualize real-time blockchain data.  

![Finiti Analytics Architecture](https://www.notion.so/image/attachment%3Ab5f3e5d6-288d-4512-91f2-5f985fbcc7b2%3Aad3aa687-6408-476d-be0f-29c496353014.png?table=block&id=1d937d64-d8bc-8072-a156-ccaeb4c73ba2&spaceId=aab87fb6-78d5-40ca-824f-a6c7886402b7&width=1420&userId=&cache=v2)

- **Metrics Collection:** Blockchain node data gathered using **Node Metrics Exporter**.  
- **Data Storage:** Managed with **Prometheus** for reliable metric handling.  
- **Visualization:** Dashboards built with **Grafana** for flexible, real-time analytics.  
- **Data API:** A custom API layer exposes structured metrics for developers and third-party apps.  
- **Frontend:** Modern React-based web application provides user dashboards and visualizations.  
 

This architecture ensures data integrity, scalability, and user-friendly dashboards, making insights accessible to developers, researchers, and institutional users alike.  



## Ecosystem Fit

### Where does your project fit?  
Finiti Analytics provides a unified analytics layer for Polkadot, turning raw blockchain data into real-time insights. It covers network activity, staking health, treasury flows, and parachain adoption, offering transparency and accessibility currently missing from the ecosystem.  

### Target Audience  
- **Parachain teams** – track adoption and performance  
- **Wallets & dApps** – integrate reliable analytics  
- **Investors & analysts** – evaluate staking, treasury, and economics  
- **Researchers & policymakers** – access transparent network insights  

### Needs Addressed  
- **Transparency** in governance, staking, and treasury operations  
- **Actionable insights** for investors and developers  
- **Accessibility** for non-technical stakeholders  

### Comparable Projects  
- **Subscan** – block explorer, lacks protocol-level analytics  
- **Polkastats** – staking-focused, no cross-domain metrics  

 
 

## Team

- **Team Name:** UniversalDot
- **Contact Name:** Igor Stojanov  
- **Contact Email:** info@universaldot.foundation  
- **Website:** [www.universaldot.foundation](https://www.universaldot.foundation/)  


### Team Members  

**Product Lead: Igor Stojanov**  
Igor Stojanov is a seasoned Software Architect with a diverse international background, currently based in Eindhoven, The Netherlands. He holds a B.Sc. in Computer Science from the United States and a Master’s degree from Eindhoven University of Technology. Igor has worked for major multinational organizations including **Philips**, **Signify**, **TYMLEZ**, and **BearingPoint**. He is the founder of the UniversalDot Foundation, dedicated to building innovative software for the decentralized internet. He also graduated from the first **Blockchain Academy PBA in Cambridge**.  

- [GitHub](https://github.com/stojanov-igor)  
- [LinkedIn](https://www.linkedin.com/in/igor-stojanov-96364ba/)  
- [Website](https://igorstojanov.com/)  



**Frontend Developer: Stefan Vukovic**  
Stefan Vukovic is a skilled **Web Developer** with 3 years of experience building secure, high-performance web applications. He is proficient in Python, Django, DRF, and PostgreSQL on the backend, and React, Next.js, TypeScript, and HTML/CSS on the frontend. Stefan delivers fast, responsive, and user-friendly solutions, translating designs into functional applications with precision and clarity.  



### Team Code Repos  
- [https://github.com/Finity](https://github.com/UniversalDot/finiti)  



### Team’s Experience  
The team has experience in:  
- **Blockchain development** – prior work includes contributions under the W3F Grants Program.  
- **Scalable architecture design** – building modular systems for data collection, processing, and visualization.  
 

The team combines **technical expertise**, **industry experience**, and a strong commitment to **open-source innovation** in the Polkadot ecosystem.  



## Development Status

Finiti Analytics is already under **active development**, with core infrastructure and components in place. The team has built an early **proof-of-concept** and a **demo version** of the platform that showcases key dashboard functionality, including real-time data collection, processing, and visualization.  

### Current Progress
- **Data Pipeline:** Metrics are being collected from blockchain nodes using exporters and stored via **Prometheus**.  
- **Visualization Layer:** **Grafana dashboards** integrated for visual exploration of metrics.  
- **Web Application:** A **React-based frontend** provides the initial user interface for dashboards.  


A **demo environment** is available for review:  
👉 [https://finitianalytics.com](https://finitianalytics.com/)  

**Demo Credentials:**  
- Email: [demo@finitianalytics.com](mailto:demo@finitianalytics.com)  
- Password: `123456`  

![Demo](https://www.notion.so/image/attachment%3A46ca805e-44ca-40de-ba7a-5851b5083779%3AScreenshot_2025-04-22_at_15.37.31.png?table=block&id=23137d64-d8bc-80c8-829a-e2788b240e46&spaceId=aab87fb6-78d5-40ca-824f-a6c7886402b7&width=1420&userId=&cache=v2)
![Demo](https://www.notion.so/image/attachment%3A06be6617-7d85-4031-aa32-b89a63d5ab28%3AScreenshot_2025-04-22_at_15.39.13.png?table=block&id=23137d64-d8bc-802b-b0c0-c922e62bb1fb&spaceId=aab87fb6-78d5-40ca-824f-a6c7886402b7&width=1420&userId=&cache=v2)


### Prior Work & Research
- **W3F Grants Experience:**  
  - [Grant Proposal](https://github.com/w3f/Grants-Program/pull/2159)  
  - [Milestone Delivery](https://github.com/w3f/Grant-Milestone-Delivery/pull/1145)  

 
- **Design Iterations:**  
  Preliminary **mockups** and **architecture diagrams** have been created to guide implementation and validate system design.  



## Development Roadmap

### Overview
- **Estimated Duration:** 3 months  
- **Full-Time Equivalent (FTE):** ~1.5 FTE  
- **Total Costs:** 30,000 USD  



### Milestones & Deliverables  

#### 🚀 Milestone 1: Core Infrastructure & MVP Dashboard  
**Duration:** 2 Months   
**Funding Requested:** 18,000 USD  

| Number | Deliverable | Specification |
| ------ | ----------- | ------------- |
| 0a. | License | All Grafana Dashboards will be released under Apache 2.0 license. |
| 0b. | Documentation | Inline documentation and a short setup guide. |
| 0c. | Testing & Testing Guide | Unit tests for core metrics|
| 0d. | Docker | Dockerfiles for Prometheus for easy testing. |
| 0e. | Article | Publish article introducing MVP dashboard and use cases. |
| 1. | Infrastructure Setup | Basic cloud environment with CI/CD pipelines. |
| 2. | Metrics Collection & Storage | Integrate Node Metrics Exporter and Prometheus. |
| 3. | MVP Web Dashboard | React-based dashboard showing accounts, validators, and transactions. |



#### 🌐 Milestone 2: Refinement & Expanded Metrics  
**Duration:** 1  Month 
**Funding Requested:** 12,000 USD  

| Number | Deliverable | Specification |
| ------ | ----------- | ------------- |
| 0a. | License | Apache 2.0 license for all complete Grafana dashboards code. |
| 0b. | Documentation | Extend documentation with API reference and quickstart guide. |
| 0c. | Testing & Testing Guide | Expand test coverage for additional metrics. |
| 0d. | Docker | Updated Dockerfiles |
| 0e. | Article | Publish article summarizing results and next steps. |
| 1. | Additional Dashboard Metrics | Add staking ratio, validator activity, and treasury balance. |
| 2. | UI Enhancements | Improve layout, add filtering and responsiveness. |
| 3. | Production Demo Deployment | Publicly accessible demo version deployed with monitoring. |

### Budget Breakdown  

| Category | Item | Cost | Duration | Total | Description |
| -------- | ---- | ---- | -------- | ----- | ----------- |
| **Personnel** | Frontend Developer (React) | $4,000/month | 2 months (0.5 FTE) | $4,000 | MVP dashboard |
| | Backend Developer (API, Prometheus) | $5,000/month | 2 months (0.5 FTE) | $5,000 | Metrics pipeline + API |
| | Product Lead / PM | $5,000/month | 3 months (0.5 FTE) | $7,500 | Oversight + architecture |
| | **Subtotal (Personnel)** |  |  | **$16,500** | |
| **Infrastructure & Tools** | Cloud Hosting | $300/month | 3 months | $900 | Lightweight setup |
| | Monitoring & Dev Tools | $200/month | 3 months | $600 | Basic monitoring + CI/CD |
| | **Subtotal (Infra & Tools)** |  |  | **$1,500** | |
| **Data & Analytics Stack** | Prometheus + Exporters | One-time |  | $2,500 | Setup & configuration |
| | Grafana integration | One-time |  | $2,500 | Dashboards setup |
| | API development | One-time |  | $3,000 | REST endpoints |
| | **Subtotal (Data & Analytics)** |  |  | **$8,000** | |
| **Web App UX** | Dashboard UI/UX Design | One-time |  | $2,000 | Layout & mockups |
| | React frontend (charts + filters) | One-time |  | $2,000 | MVP implementation |
| | **Subtotal (Web App)** |  |  | **$4,000** | |
| **Total Estimated Budget** |  |  |  | **$30,000** | |



## Future Plans

In the short term, our focus is on delivering a **robust MVP** that provides key insights into Polkadot’s network activity, staking, and treasury. After the grant-funded phase, we plan to:  

- **Expand Analytics Coverage** – introduce more advanced metrics (cross-chain activity, economic models, parachain slot dynamics).  
- **Develop API Integrations** – allow parachain teams, wallets, and dApps to easily embed analytics into their products.  
- **Community Engagement** – publish research, tutorials, and case studies to help stakeholders adopt the platform.  

For long-term sustainability:  
- We will explore a **freemium model**, offering core dashboards openly while advanced features can be extended for enterprise use cases.  
- Maintenance and further development will be supported by a combination of **community funding**, **research collaborations**, and **partnerships with ecosystem projects**.  
- The team intends to continue contributing to the **Polkadot analytics stack**, ensuring open, transparent data access.  

---

## Additional Information

- **Work Completed:**  
  - A demo version of the platform is available for preview: [https://finitianalytics.com](https://finitianalytics.com/)  
    - Email: [demo@finitianalytics.com](mailto:demo@finitianalytics.com)  
    - Password: `123456`  
  - Early integrations with **Prometheus**, **Grafana**, and **React frontend** are functional.  

- **Previous Grants:**  
  - Successfully completed prior W3F grants:  
    - [Grant Proposal](https://github.com/w3f/Grants-Program/pull/2159)  
    - [Milestone Delivery](https://github.com/w3f/Grant-Milestone-Delivery/pull/1145)  


- **Contact:**  
  📧 info@universaldot.foundation  
  🌐 [www.universaldot.foundation](https://www.universaldot.foundation/)  

### Out of Scope

To manage expectations, the following are **not** part of this project:  
- Direct financial advisory services (e.g., trading signals, investment advice).  
- Custodial services or asset management functionality.  

