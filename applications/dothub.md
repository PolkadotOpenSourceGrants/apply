# Dothub - Decentralized Link Page Platform

## Project Overview

- **Tagline:** The Web3 link page platform for creators and blockchain projects
- **Brief Description:** Dothub is a Web3-enabled link aggregation platform similar to Linktree, built on blockchain technology. It allows users to create beautiful, customizable link pages with added features for showcasing NFT collections and receiving cryptocurrency donations directly on their page.
- **Polkadot Integration:** Built on Polkadot blockchain for data storage, user authentication via wallet connection, and secure page management. Supports DOT transactions for tipping creators and NFT integration.
- **Team Interest:** I'm passionate about building tools that enhance the creator economy and provide Web3 creators with specialized features for showcasing their work and connecting with their audience.

### Project Details

**Technology Stack:**
- Frontend: Nuxt.js 3 with Vue.js
- UI Framework: Nuxt UI with Tailwind CSS
- Blockchain:
  - Polkadot Asset Hub (for initial phase)
  - Polkadot People
- Deployment: Cloudflare Workers (NuxtHub)

**Core Components:**
- **User Authentication:** Wallet-based authentication using Polkadot addresses
- **Link Management:** CRUD operations for social media links and custom URLs
- **Page Customization:** Theme selection and custom styling options
- **NFT Integration:** Showcase NFT collections
- **Analytics Dashboard:** Track clicks, views, and engagement metrics
- **Cryptocurrency Tipping:** Allow visitors to send DOT tokens to creators
- **Blockchain Storage:** Store page data and configurations on Polkadot blockchain

### Ecosystem Fit

**Position in Ecosystem:**
Dothub fits into the Polkadot ecosystem as a user-facing dApp that demonstrates practical Web3 applications for everyday creators and influencers. It serves as an onboarding tool for new users to experience blockchain technology through a familiar use case.

**Target Audience:**
- Content creators and influencers interested in Web3 features
- NFT artists wanting to showcase their collections alongside other links
- Web3 developers and blockchain project teams
- Creators interested in crypto payment options

**Needs Addressed:**
- **Web3 Creator Support:** Native integration for creators to showcase NFT collections and digital assets
- **Crypto Payment Integration:** Direct cryptocurrency payment options for creator monetization
- **Polkadot Ecosystem Tools:** User-friendly applications that demonstrate practical blockchain use cases
- **Creator Economy Enhancement:** Additional monetization channels through blockchain technology
- **Community Building:** Tools for Web3 communities and projects to showcase their work

**Evidence of Need:**

**Market Demand for Link Aggregation:**
The widespread use of Linktree across X (Twitter) platform demonstrates clear market demand for link aggregation tools. This presents an opportunity to serve the Web3 creator community with blockchain-integrated features:

- **Growing Web3 Creator Economy:** Increasing number of NFT creators, blockchain projects, and crypto-focused content creators need specialized tools
- **Crypto Payment Demand:** Many creators want to accept cryptocurrency payments but lack integrated solutions
- **NFT Showcase Needs:** Digital artists and NFT creators need platforms to display their collections alongside other links
- **Polkadot Ecosystem Growth:** Need for more user-facing applications that demonstrate practical blockchain utility

**Market Opportunity:**
- Increasing adoption of Web3 and blockchain applications
- Rising popularity of NFTs and creator economy
- Growing Polkadot ecosystem needing user-friendly tools

**Similar Projects:**
After reviewing Polkadot Forum and OpenGov, I found limited direct competitors focusing on decentralized link aggregation.

**Different Approach:**
- Focus on creator economy and monetization
- NFT integration for digital artists
- Polkadot-native with DOT token utility
- Emphasis on beautiful, customizable designs

## Team

- **Team Name:** Dothub Labs
- **Contact Name:** Preschian Febryantara
- **Contact Email:** preschian27@gmail.com
- **Website:** https://github.com/preschian

### Team members

- Preschian Febryantara

#### LinkedIn Profiles

- [Preschian Febryantara](https://www.linkedin.com/in/preschian-febryantara/)

### Team Code Repos

- https://github.com/preschian/dothub

### Team's experience

**5+ Years Web Development Experience:** Extensive background in modern web development with comprehensive full-stack development skills.

**Current Role - Fullstack Developer at Koda.art:** Currently contributing as a fullstack developer at Koda.art, a platform within the Polkadot ecosystem. Through this role, I have gained comprehensive experience with:
- Polkadot.js API integration and substrate chain interactions
- Modern frontend frameworks in blockchain applications
- User experience design for Web3 applications
- Production deployment and maintenance of dApps
- Working with Polkadot NFT marketplace on AssetHub

This hands-on experience with production Polkadot applications provides deep insights into developer pain points and ecosystem needs, directly informing the development of user-facing dApps like Dothub.

## Development Status

**Current Status:** HTML prototype for demonstration purposes

**Live Demo Links:**
- **Landing Page:** https://dot-hub.gogeta.workers.dev/
- **Dashboard Interface:** https://dot-hub.gogeta.workers.dev/0xpresc/dashboard
- **User Profile Page:** https://dot-hub.gogeta.workers.dev/0xpresc/

The prototypes demonstrate the initial user experience flow and interface concept, built with Nuxt.js 3 and deployed on Cloudflare Workers. Note that the final design and functionality may evolve during production development to optimize for blockchain integration and user experience.

**Technical Research & Preparation:**
I have conducted research on blockchain integration techniques by building a similar Web3 link platform application ([research repository](https://github.com/preschian/solx)). This research has provided valuable insights into:
- NFT-based profile storage mechanisms
- Decentralized storage implementation strategies
- User authentication and blockchain data management

**Planned Implementation Architecture:**
Dothub will follow a similar approach, storing user data on-chain for permanent ownership and accessibility. The technical implementation will include:
- **On-chain Data Storage:** User profiles and link configurations stored on Polkadot blockchain
- **NFT-based Implementation:** Initial phase will utilize NFTs on AssetHub to accelerate development and deployment
- **Identity Integration:** Leverage Polkadot People Identity system for user slug generation based on existing Twitter verification data
- **Enhanced Verification:** Additional verification process within Dothub to ensure users have legitimate access rights to their claimed Twitter accounts
- **Hybrid Approach for Performance:** Analytics data and caching will remain off-chain, leveraging Cloudflare's infrastructure to provide optimal user experience
- **Ecosystem Integration:** Utilizing existing Polkadot infrastructure (People chain) for identity management while adding application-specific verification layers

This approach ensures data ownership benefits while maintaining fast, responsive user interactions through strategic use of both on-chain and off-chain components, plus seamless integration with existing Polkadot identity infrastructure.

## Development Roadmap

**Polkadot Open Source Grants only accept projects up to 3 months of duration and up to 2 milestones.**

### Overview

- **Estimated Duration:** 3 months
- **Full-Time Equivalent (FTE):** 1 FTE
- **Total Costs:** 30,000 USD

### Milestone 1: Blockchain Integration & Core Features (6 weeks)

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT License |
| 0b. | Documentation | I will provide comprehensive documentation including API docs, user guides, and developer tutorials for blockchain integration |
| 0c. | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness |
| 0d. | Docker | I will provide a Dockerfile that can be used to test all the functionality delivered with this milestone |
| 0e. | Article | I will publish a technical article explaining the architecture and benefits of blockchain-integrated link pages |
| 1. | Wallet Integration | I will implement complete Polkadot.js wallet integration with authentication and transaction signing |
| 2. | Identity Integration | I will integrate with Polkadot People chain for user identity verification and slug generation |
| 3. | AssetHub Integration | I will implement NFT-based profile storage using Polkadot AssetHub for user data and configurations |
| 4. | Link Management | I will develop fully functional link creation, editing, and deletion with blockchain storage |
| 5. | CI/CD Integration | I will implement continuous integration and deployment pipeline for automated testing and deployment |
| 6. | SEO Integration | I will implement comprehensive SEO optimization including meta tags, structured data, and performance optimization |
| 7. | Basic Theme Customization | I will implement basic theming and customization options for user pages |

### Milestone 2: Advanced Features & Production Deployment (6 weeks)

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 1. | Responsive Landing Page | I will create a fully responsive landing page optimized for all device sizes |
| 2. | Responsive Dashboard UI | I will implement a responsive dashboard interface for user management and analytics |
| 3. | Responsive User Page | I will build a responsive user profile page for displaying links and NFT collections |
| 4. | NFT Showcase Integration | I will implement functionality to display and showcase NFT collections that users own on their profile pages |
| 5. | Cryptocurrency Tipping | I will implement DOT token tipping system for creators |
| 6. | Analytics System | I will build a comprehensive analytics dashboard with blockchain-verified metrics |

### Budget Breakdown

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Full-Stack Developer | 10,000 USD/month | 3 months | 30,000 USD | Full-stack development including Substrate/Polkadot blockchain integration, Vue.js/Nuxt.js frontend development, and UI/UX implementation |
| --- | --- | --- | **Total** | **30,000 USD** |  |

## Future Plans

**Long-term Enhancement:**
- **Dothub Commerce:** Implementation of digital product sales, fundraising capabilities, and NFT-gated exclusive content features
- **Shortened URLs:** URL shortening service for improved link management and analytics
- **Cross-Chain Payment Support:** Enable cross-chain transfers for payments and tipping from multiple blockchain networks
- Community building and user acquisition

**Sustainability Strategy:**
- **Profitability Focus:** Implementation of 5% platform fee on commercial transactions to ensure long-term sustainability
- **Maintenance Funding:** Request additional funding for platform maintenance and development until profitability is achieved
- Transition to self-sustaining revenue model through platform fees

**Long-term Vision:**
- Make Dothub a leading Web3 link platform for creators and blockchain projects
- Expand features and integrations within the Polkadot ecosystem
- Build a comprehensive creator economy ecosystem with full commerce capabilities
- Open-source the entire platform for community contributions

## Additional Information

**Work Already Done:**
- HTML prototype demonstrating user experience and interface design
- Working demo deployed at https://dot-hub.gogeta.workers.dev/
- Technical research through blockchain development experience
- Modern frontend foundation with Nuxt.js 3 and Tailwind CSS

**Technical Approach:**
- Utilizing existing Polkadot infrastructure (AssetHub and People chain)
- Hybrid architecture balancing blockchain benefits with performance needs
- Focus on practical Web3 integration rather than blockchain-only solutions

**Community Engagement:**
- Planning to engage with Polkadot community through Twitter
- Committed to open-source development and community feedback
