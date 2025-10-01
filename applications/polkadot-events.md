# Polkadot Events Transparency & Resource Platform

## Project Overview

- **Tagline:** An open-source transparency, resource, and community collaboration platform for the Polkadot/Kusama events ecosystem.
- **Description:** This project delivers a comprehensive platform providing real-time analytics for the Events Bounty, a centralized hub of high-quality resources for event organizers, community-driven verification tools, and engagement features like a Telegram notification bot. It addresses critical ecosystem needs for transparency in treasury spending, democratizes access to event organization tools, and enables verifiable accountability through community participation.
- **Relation to Polkadot/Kusama:** The platform directly enhances the transparency and efficiency of the Polkadot/Kusama treasury spending (specifically the Events Bounty), serves the community of builders and event organizers within the ecosystem, and integrates with Polkadot.js for identity and verification. It is built as a decentralized, community-owned resource that complements existing infrastructure like dotevents.xyz.
- **Team Interest:** Our team is deeply embedded in the Polkadot ecosystem and has identified a clear gap in transparency, resource management, and post-event accountability for events. We are motivated to build a public good that increases accountability, reduces redundant work, empowers community members to host successful events, and provides verifiable proof of event impact, thereby strengthening the entire network.

### Project Details

**Technology Stack:**
- **Frontend:** Next.js 15 (App Router), TypeScript, Tailwind CSS, shadcn/ui
- **Backend/Database:** Supabase (PostgreSQL, Authentication, Realtime, Edge Functions, Storage)
- **Integrations:** Polkadot.js API, Monday.com API, Telegram Bot API, IPFS (for decentralized storage)
- **Infrastructure:** Frontend Hosting, Docker, Redis (Caching)
- **License:** Apache 2.0

**Core Components & Architecture:**
The architecture is a modern, full-stack application centered on a Supabase PostgreSQL database. The Next.js frontend interacts with the database via Supabase's client and server-side libraries. Real-time updates for events and funding status are powered by Supabase Realtime. Serverless Edge Functions handle secure operations like webhook processing from Monday.com and Telegram. Redis caching ensures high performance for notification services and real-time data delivery. Polkadot.js is integrated for on-chain identity and verification purposes. Supabase Storage and IPFS provide decentralized media management for community-contributed content.

**PoC/MVP:**
A functional Minimum Viable Product (MVP) is currently under active development. The video demonstration showcases a working prototype with a sophisticated UI, advanced filtering, and data integration: [**MVP Video Walkthrough**](https://www.youtube.com/watch?v=fm1YkXuMRXg). The codebase is available in the public repository: [https://github.com/developerfred/polkadot-events](https://github.com/developerfred/polkadot-events).

**What this project is NOT:**
- This is not a replacement for on-chain governance or treasury pallets.
- It will not implement its own funding mechanism; it is a transparency and visualization layer for existing processes (e.g., the Events Bounty).
- It is not an events hosting platform itself (like Luma or Eventbrite), nor a replacement for dotevents.xyz. Instead, it is a complementary meta-layer that adds transparency, collaboration tools, and accountability features for Polkadot-funded events.

### Ecosystem Fit

- **Where and how does your project fit into the ecosystem?**
  This project serves as a **complementary transparency and collaboration layer** for the Polkadot events ecosystem. Rather than replacing existing infrastructure, we enhance it by adding verifiable accountability mechanisms, community engagement tools, and multi-dimensional ROI tracking. We integrate with and amplify the value of existing platforms like dotevents.xyz by providing the missing pieces: funding transparency, community-driven verification, and measurable impact assessment. The platform sits at the intersection of treasury management (OpenGov, Bounties), community participation, and event execution.

- **Who is your target audience?**
  - **Primary:** Event organizers and applicants within the Polkadot/Kusama ecosystem who need transparency tools and community engagement features for funded events.
  - **Secondary:** Treasury Council members, Polkadot ambassadors, and governance participants seeking verifiable ROI data on event investments.
  - **Tertiary:** Event attendees from dotevents.xyz and other Polkadot events who want to contribute documentation, provide feedback, and verify their participation.
  - **Quaternary:** Developers building community tooling who can leverage our open API and data aggregation infrastructure.

- **What need(s) does your project meet?**
  1. **Investment Accountability:** Verifiable proof that funded events actually happened and achieved their stated objectives through community-contributed evidence (photos, check-ins, feedback).
  2. **Transparency:** Real-time public visibility into Events Bounty proposals, funding decisions, approval rates, and negotiation outcomes.
  3. **ROI Measurement:** Comprehensive, multi-dimensional impact tracking (social media reach, on-chain engagement, verified attendance, anticipatory interest, content performance) that enables data-driven treasury decisions.
  4. **Community Participation:** Tools that empower attendees to document events, verify their participation, and contribute to the ecosystem's collective knowledge.
  5. **Resource Efficiency:** Centralized access to event organization resources, reducing redundant work and improving event quality across the ecosystem.
  6. **Real-time Engagement:** Notification systems that keep the community informed and engaged with the events program.

- **How did you identify these needs?**
  The need is evidenced by:
  - **Quantitative Data:** The Events Bounty's own reports (e.g., 286 submissions, 146 approved, ~$950k in negotiated savings) demonstrate the scale of investment requiring transparent tracking and accountability mechanisms.
  - **Forum Discussions:** Recurring conversations on the Polkadot Forum about treasury accountability, the need for measurable ROI on event spending, and the infrastructure gap left by the transition from centralized (Web3 Foundation) to decentralized event management.
  - **Direct Community Feedback:** Explicit requests from community members for:
    - Verifiable proof of event execution and attendance
    - Better methods to document and share event experiences
    - Data-driven insights into which types of events deliver the best ROI
    - Tools to participate in post-event accountability
  - **Governance Context:** Growing emphasis across all Substrate chains on treasury spending accountability and the need for objective metrics to evaluate funding proposals.

- **Are there any other projects similar to yours in the Polkadot/Kusama ecosystem?**
  - **dotevents.xyz:** Serves as an excellent event calendar and aggregation platform. **Our project is explicitly designed to complement, not replace, dotevents.** We provide the collaboration and transparency layer for funded events listed on dotevents. Specifically:
    - **dotevents** handles: Event discovery, calendar listings, basic event information
    - **Our platform** adds: Treasury funding transparency, community-driven verification (photos, check-ins, feedback), ROI analytics, resource management, and accountability tools
    - **Integration approach:** We sync with dotevents data and enhance funded events with additional accountability features, creating a symbiotic relationship.
  
  - **Polkadot Treasury Dashboards/Wikis:** Provide general information but lack:
    - Real-time event-specific data integration
    - Community participation mechanisms
    - Post-event verification tools
    - Granular ROI analytics
    - Organizer-specific resources
  
  **Our unique value proposition:** We are the only platform purpose-built to bridge the gap between treasury funding decisions and verifiable on-the-ground event outcomes through community collaboration, while seamlessly integrating with existing tools like dotevents.

- **Are there any projects in related ecosystems?**
  Analogous concepts exist in other ecosystems but are fragmented:
  - **Gitcoin/Giveth:** Grant transparency and impact tracking (Web3)
  - **Luma/Eventbrite:** Event registration and management (Web2)
  - **Devfolio:** Hackathon management with some ROI features (Web2/Web3 hybrid)
  - **POAP/Sismo:** Proof of attendance protocols (Web3)
  
  Our project is the first to synthesize these concepts into a cohesive, Polkadot-native platform that respects the ecosystem's existing infrastructure (like dotevents) while filling critical gaps in accountability, transparency, and community engagement.

## Team

- **Team Name:** AIPOP Fun
- **Contact Name:** Fred
- **Contact Email:** codingsh @ pm.me
- **Website:** https://github.com/developerfred

### Team members

- Fred Silva [On-chain Identity](https://polkadot.subscan.io/account/13eJfzT8u1qKYkFDW6o7Ta19eGi9X8Y74cWLDComEVxbKGMa)

#### LinkedIn Profiles (if available)

- N/A

### Team Code Repos

- https://github.com/developerfred/polkadot-events
- https://github.com/developerfred/papi-simulator

### Team's experience

Our lead developer, Fred, has extensive experience building within the Polkadot ecosystem:
- **PAPI Simulator ([papi-simulator.aipop.fun](https://papi-simulator.aipop.fun/)):** A production-grade interactive tool for developers to learn and experiment with the `polkadot-api` library, demonstrating deep technical knowledge of Polkadot's core technology.
- **FastGrants Bot:** An operational Telegram bot that monitors and alerts users to Polkadot OpenGov Fast Grants, proving experience with real-time data integration and community tooling.
- **5+ years** of full-stack Web2/Web3 development experience with TypeScript, React, Node.js, and PostgreSQL.

## Development Status

We have conducted significant research and development prior to this application.
- **Open GitHub Repository:** Active development on the [`polkadot-events` platform](https://github.com/developerfred/polkadot-events) has begun, including database schema design, Supabase integration, and a functional frontend with advanced filtering.
- **MVP Video Demonstration:** A video walkthrough of the current working prototype is available, showcasing the implemented UI, data tables, and advanced filtering functionality: [**Watch the MVP Demo**](https://www.youtube.com/watch?v=fm1YkXuMRXg).
- **Prior Art:** The successful deployment and positive community reception of the [PAPI Simulator](https://papi-simulator.aipop.fun) proves our capability to deliver and maintain high-quality developer tools for the Polkadot ecosystem.
- **Research:** We have analyzed the Events Bounty reports, studied the existing ecosystem tools (dotevents.xyz), identified specific pain points through community engagement, and researched ROI measurement methodologies applicable to Web3 events.

## Development Roadmap

### Overview

- **Total Estimated Duration:** 3 months
- **Full-Time Equivalent (FTE):** 1 FTE
- **Total Costs:** 28,000 USD

### Milestone 1 — Core Transparency & Resource Hub

- **Estimated Duration:** 6 weeks
- **FTE:** 1
- **Costs:** 14,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | Inline code documentation and a comprehensive tutorial explaining how to navigate the transparency dashboard, submit resources, and use basic features. |
| **0c.** | Testing Guide | Core functions will be covered by unit and integration tests. A guide will describe how to run the test suite. |
| **0d.** | Docker | A Dockerfile will be provided to containerize the application for easy testing and deployment. |
| **0e.** | Article | We will publish a detailed article/walkthrough showcasing the platform's transparency features and how it benefits the community. |
| **1.** | Integrated Database & API | A complete Supabase PostgreSQL backend with optimized tables for events, funding proposals, resources, and user profiles. Full integration with the Monday.com API for automatic data synchronization of event submissions from the Events Bounty workflow. |
| **2.** | Transparency Dashboard | A public-facing dashboard displaying real-time analytics on Events Bounty data: approval rates, funding amounts, negotiation savings, historical trends, and event status tracking. Integration with dotevents.xyz data for comprehensive event visibility. |
| **3.** | Resource Hub | A functional system for categorizing, uploading, versioning, and downloading event organization resources (templates, guides, branding assets). Includes advanced search, filtering, and community rating system. |
| **4.** | Core Frontend Application | A deployed Next.js application providing a user-friendly interface for the dashboard and resource hub, including authentication via Polkadot.js and role management. |

### Milestone 2 — Community Collaboration, Engagement & Advanced Features

- **Estimated Duration:** 6 weeks
- **FTE:** 1
- **Costs:** 14,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | Comprehensive documentation covering all collaborative features including photo submissions, check-ins, moderation workflows, community feedback systems, Telegram bot commands, and advanced analytics methodologies. |
| **0c.** | Testing Guide | All collaborative and engagement features will be covered by unit, integration, and end-to-end tests. Updated guide provided. |
| **0d.** | Docker | Updated Docker image including all new collaborative and engagement functionalities. |
| **0e.** | Article | Publication of a detailed article explaining the community verification features, engagement tools, and their impact on event accountability and transparency. |
| **1.** | Event Photo Gallery System | A decentralized photo upload and gallery system where community members can contribute event photos post-event. Features include: IPFS storage integration for decentralized hosting, automatic metadata extraction (timestamp, location if available), moderation queue with reputation-based approval, photo verification by event organizers, and integration with funded events from dotevents.xyz. Supports bulk uploads and mobile-friendly interface. |
| **2.** | Digital Check-in System | QR code-based check-in functionality for event booths/venues allowing tracking of unique attendee interactions. Includes: Polkadot.js wallet authentication for verified check-ins, privacy-preserving attendance counting (no PII stored), booth-specific interaction tracking, duplicate prevention mechanisms, exportable attendance reports for treasury accountability, and anonymous analytics dashboard. Event organizers can generate unique QR codes per booth/session. |
| **3.** | Community Feedback & Comments | Moderated commenting system for post-event feedback and reviews. Features include: reputation-based moderation system, spam prevention and content filtering, constructive feedback guidelines and prompts, multi-dimensional rating system for different event aspects (organization quality, content relevance, networking opportunities, venue appropriateness), organizer response mechanisms, sentiment analysis aggregation for quick insights, and anonymous feedback option with abuse prevention. |
| **4.** | Telegram Notification Bot | A fully operational Telegram bot with the following capabilities: subscription management for personalized event updates, customizable notification preferences (upcoming events, funding decisions, proposal deadlines, new community contributions), real-time alerts when new photos or feedback are posted, interactive commands to query event data and ROI metrics, direct links to event pages and contribution opportunities, and multilingual support for the global Polkadot community. |
| **5.** | Advanced Analytics & ROI Engine | Implementation of multi-dimensional ROI tracking and predictive analytics including: Social Media ROI monitoring (X/Twitter mentions, LinkedIn engagement, sentiment analysis across platforms), Anticipatory Interest Index (Google Trends analysis in the week preceding events), Content Performance Score (YouTube Shorts, Instagram Reels, TikTok metrics for event-related content), On-chain Engagement Score (NFT claims, POAP distributions, wallet interactions), Verified Participation Metrics (check-in data vs. projected attendance, actual vs. estimated costs), and Comparative Benchmarking (ROI across event types, geographic regions, and organizer track records). Includes predictive models for future event planning and automated ROI report generation for treasury reporting. |
| **6.** | Polkadot.js Integration & Production Deployment | Secure user authentication and identity verification via Polkadot.js wallet connection, role-based access control (organizers, moderators, community members), comprehensive security audit and code review, Redis caching implementation for high-performance data delivery, database query optimization, rate limiting and DDoS protection, monitoring and error tracking setup, and full production deployment on Vercel with CDN configuration. |

### Budget Breakdown

 **Category:** Budget Breakdown positions are split within the following categories: 
 
- Personnel
- Equipment
- Subcontracts/Subscriptions

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Product Lead | 70 USD/hr | 100 hrs | 7,000 USD | Project management, strategic planning, community engagement, user research for collaborative features, integration coordination with dotevents.xyz, and final quality assurance. |
| Personnel | Lead Full-Stack Developer | 65 USD/hr | 323 hrs | 21,000 USD | Architecture, development, testing, and deployment of the entire platform including collaborative features (photo gallery, check-in system, feedback system), analytics engine, Telegram bot, and integration with existing ecosystem tools. Reduced hourly rate to accommodate expanded scope within budget. |
| **Total** | | | | **28,000 USD** |  |

## Future Plans

Our long-term plan is to transition the platform into a fully community-owned and maintained public good.
- **Financing:** Post-grant, we will seek to establish a small recurring treasury tip or bounty for maintenance from the Polkadot OpenGov system, based on proven usage and value. The open-source nature will also allow for community donations and contributions.
- **Promotion:** We will actively promote the platform through Polkadot forums, social media channels, ambassador networks, direct outreach to past event organizers, and live demonstrations at major Polkadot events.
- **Enhancement:** Future development will be guided by community feedback via GitHub Issues. Potential enhancements include:
  - Integration with additional parachain-specific event systems
  - Speaker directory and reputation system
  - Advanced sponsorship management tools
  - AI-powered event recommendations
  - Multi-language support expansion
  - Mobile application (React Native)
  - Enhanced gamification for community contributors
  - Integration with additional on-chain identity systems (e.g., Kilt Protocol)
- **Long-term:** The team's intention is to ensure the project's sustainability and eventually hand over stewardship to a dedicated community DAO or team. We envision this platform becoming the de facto standard for event transparency and accountability across all Substrate-based chains.

## Additional Information

- **Work Completed:** An MVP with core functionality is already under development, as visible in the public GitHub repository and the [**video demonstration**](https://www.youtube.com/watch?v=fm1YkXuMRXg). This de-risks the project significantly.
- **Community Feedback Integration:** The collaborative features outlined in Milestone 2 were directly informed by community feedback emphasizing the need for verifiable event accountability and participant engagement mechanisms that go beyond passive transparency.
- **Other Funding:** This project has not been submitted for funding to any other entity. We are solely applying to the Polkadot Open Source Grants program.
- **Existing Contributions:** The development work to date has been self-funded by the team as a proof-of-concept.
- **Communication Plan:** We will provide bi-weekly development updates via the Polkadot Forum and GitHub repository, ensuring full transparency throughout the grant period. Additionally, we will host monthly community calls to gather feedback and demonstrate progress on collaborative features.