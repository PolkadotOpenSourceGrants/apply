# Polkadot Events Transparency & Resource Platform

## Project Overview

- **Tagline:** An open-source transparency and resource platform for the Polkadot/Kusama events ecosystem.
- **Description:** This project delivers a comprehensive platform providing real-time analytics for the Events Bounty, a centralized hub of high-quality resources for event organizers, and community engagement tools like a Telegram notification bot. It addresses critical ecosystem needs for transparency in treasury spending and democratizes access to event organization tools.
- **Relation to Polkadot/Kusama:** The platform directly enhances the transparency and efficiency of the Polkadot/Kusama treasury spending (specifically the Events Bounty), serves the community of builders and event organizers within the ecosystem, and integrates with Polkadot.js for identity and verification. It is built as a decentralized, community-owned resource.
- **Team Interest:** Our team is deeply embedded in the Polkadot ecosystem and has identified a clear gap in transparency and resource management for events. We are motivated to build a public good that increases accountability, reduces redundant work, and empowers community members to host successful events, thereby strengthening the entire network.

### Project Details

**Technology Stack:**
- **Frontend:** Next.js 15 (App Router), TypeScript, Tailwind CSS, shadcn/ui
- **Backend/Database:** Supabase (PostgreSQL, Authentication, Realtime, Edge Functions)
- **Integrations:** Polkadot.js API, Monday.com API, Telegram Bot API
- **Infrastructure:** Vercel (Frontend Hosting), Docker, Redis (Caching)
- **License:** Apache 2.0

**Core Components & Architecture:**
The architecture is a modern, full-stack application centered on a Supabase PostgreSQL database. The Next.js frontend interacts with the database via Supabase's client and server-side libraries. Real-time updates for events and funding status are powered by Supabase Realtime. Serverless Edge Functions handle secure operations like webhook processing from Monday.com and Telegram. Redis caching ensures high performance for notification services and real-time data delivery. Polkadot.js is integrated for on-chain identity and verification purposes.

**PoC/MVP:**
A functional Minimum Viable Product (MVP) is currently under active development. The video demonstration showcases a working prototype with a sophisticated UI, advanced filtering, and data integration: [**MVP Video Walkthrough**](https://www.youtube.com/watch?v=fm1YkXuMRXg). The codebase is available in the public repository: [https://github.com/developerfred/polkadot-events](https://github.com/developerfred/polkadot-events).

**What this project is NOT:**
- This is not a replacement for on-chain governance or treasury pallets.
- It will not implement its own funding mechanism; it is a transparency and visualization layer for existing processes (e.g., the Events Bounty).
- It is not an events hosting platform itself (like Luma or Eventbrite), but a meta-layer for managing and transparently tracking Polkadot-specific events.

### Ecosystem Fit

- **Where and how does your project fit into the ecosystem?**
  It fits into the ecosystem's operational infrastructure layer. It provides critical tooling for transparency (a core Web3 tenet) and community enablement, sitting between treasury management systems (OpenGov, Bounties) and the end-users (event organizers, community members).

- **Who is your target audience?**
  - **Primary:** Event organizers and applicants within the Polkadot/Kusama ecosystem.
  - **Secondary:** Treasury Council members, Polkadot ambassadors, and community members seeking to track the impact of treasury spending on events.
  - **Tertiary:** Developers building community tooling who can leverage our open API.

- **What need(s) does your project meet?**
  1. **Transparency:** A clear, public view of Events Bounty proposals, funding decisions, and outcomes.
  2. **Efficiency:** A single source of truth for event organization resources (brand assets, templates, guides).
  3. **Awareness:** Real-time notifications for upcoming events, proposal deadlines, and funding announcements.

- **How did you identify these needs?**
  The need is evidenced by:
  - **Data:** The Events Bounty's own reports (e.g., 286 submissions, 146 approved, ~$950k in negotiated savings) highlight the scale and need for transparent tracking.
  - **Forum Discussions:** Historical discussions on the Polkadot Forum regarding the transition from Web3 Foundation-led events to a decentralized model and the resulting infrastructure gap.
  - **Direct Feedback:** Community requests for better resource sharing and clarity on funding decisions.

- **Are there any other projects similar to yours in the Polkadot/Kusama ecosystem?**
  - **dotevents.xyz:** A basic event calendar. Our project is fundamentally different as it focuses on **funding transparency**, **advanced resource management**, and **community engagement tools**, far beyond a simple calendar listing.
  - **Polkadot Treasury Wiki/Websites:** Provide general information but lack real-time data integration, detailed analytics, and organizer-specific tools.
  Our project is unique in its integrated approach to transparency, resources, and engagement specifically for the events lifecycle.

- **Are there any projects in related ecosystems?**
  Projects like Luma (event registration) or Gitcoin (grant transparency) solve pieces of the puzzle in other ecosystems. This project aims to create a Polkadot-native synthesis of these concepts tailored to our specific governance and community structures.

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
- **Research:** We have analyzed the Events Bounty reports, studied the existing ecosystem tools (dotevents.xyz), and identified specific pain points through community engagement.

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
| **1.** | Integrated Database & API | A complete Supabase PostgreSQL backend with optimized tables for events, funding proposals, and resources. Full integration with the Monday.com API for automatic data synchronization. |
| **2.** | Transparency Dashboard | A public-facing dashboard displaying real-time analytics on Events Bounty data: approval rates, funding amounts, negotiation savings, and historical trends. |
| **3.** | Resource Hub | A functional system for categorizing, uploading, versioning, and downloading event organization resources (templates, guides, branding assets). Includes search and filtering. |
| **4.** | Core Frontend Application | A deployed Next.js application providing a user-friendly interface for the dashboard and resource hub, including authentication and role management. |

### Milestone 2 — Community Engagement & Advanced Features

- **Estimated Duration:** 6 weeks
- **FTE:** 1
- **Costs:** 14,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | Documentation will be updated to cover all new features, including the Telegram bot commands and advanced analytics. |
| **0c.** | Testing Guide | All new features will be covered by tests. The guide will be updated accordingly. |
| **0d.** | Docker | The Docker image will be updated to include all new functionalities from this milestone. |
| **0e.** | Article | We will publish a follow-up article/tutorial focusing on the community engagement features (Telegram bot) and advanced analytics. |
| **1.** | Telegram Notification Bot | A fully operational Telegram bot that users can subscribe to for real-time alerts on new events, proposal status changes, and deadline reminders. |
| **2.** | Advanced Analytics Engine | Implementation of predictive analytics and ROI calculation features for treasury spending, building on the base dashboard from Milestone 1. |
| **3.** | Polkadot.js Integration | Secure user authentication and identity verification via Polkadot.js wallet connection. |
| **4.** | Performance & Security | Comprehensive code review, Redis caching implementation, query optimization, and production deployment. |

### Budget Breakdown

 **Category:** Budget Breakdown positions are split within the following categories: 
 
- Personnel
- Equipment
- Subcontracts/Subscriptions

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | ---|
| Personnel | Product Lead | 70 USD/hr | 100 hrs | 7,000 USD | Project management, strategic planning, community engagement, and final quality assurance. |
| Personnel | Lead Full-Stack Developer | 70 USD/hr | 300 hrs | 21,000 USD | Architecture, development, testing, and deployment of the entire platform. |
| **Total** | | | | **28,000 USD** |  |

## Future Plans

Our long-term plan is to transition the platform into a fully community-owned and maintained public good.
- **Financing:** Post-grant, we will seek to establish a small recurring treasury tip or bounty for maintenance from the Polkadot OpenGov system, based on proven usage and value. The open-source nature will also allow for community donations and contributions.
- **Promotion:** We will actively promote the platform through Polkadot forums, social media channels, ambassador networks, and direct outreach to past event organizers.
- **Enhancement:** Future development will be guided by community feedback via GitHub Issues. Potential enhancements include integration with more parachain-specific event systems, a speaker directory, and advanced sponsorship management tools.
- **Long-term:** The team's intention is to ensure the project's sustainability and eventually hand over stewardship to a dedicated community DAO or team.

## Additional Information

- **Work Completed:** An MVP with core functionality is already under development, as visible in the public GitHub repository and the [**video demonstration**](https://www.youtube.com/watch?v=fm1YkXuMRXg). This de-risks the project significantly.
- **Other Funding:** This project has not been submitted for funding to any other entity. We are solely applying to the Polkadot Open Source Grants program.
- **Existing Contributions:** The development work to date has been self-funded by the team as a proof-of-concept.
- **Communication Plan:** We will provide bi-weekly development updates via the Polkadot Forum and GitHub repository, ensuring full transparency throughout the grant period.

