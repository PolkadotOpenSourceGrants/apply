# Kacheri  Diaries AI



## Project Overview



*Tagline:* Kacheri Diaries AI – Justice, Simplified with AI & Secured by Blockchain.

*Description:* Kacheri Diaries AI is an intelligent legal assistant platform designed to digitise and democratise access to legal services in India. It features dual interfaces for lawyers and clients, offering AI-powered document analysis, case tracking, legal research tools, and automated drafting support. With a focus on transparency, efficiency, and accessibility, Kacheri Diaries AI bridges the gap between legal professionals and citizens by simplifying complex legal workflows. Through smart automation and intuitive design, the platform aims to transform traditional legal practice into a modern, tech-driven experience.

*Integration with Blockchain:* To ensure the integrity and security of legal records, Kacheri Diaries AI integrates blockchain technology for evidence management, document vaulting, and audit trails. Each critical file—such as affidavits, witness statements, or evidence—is encrypted, time-stamped, and stored with a tamper-proof certificate. This not only safeguards the authenticity of documents but also ensures transparency in legal proceedings. Blockchain integration provides a verifiable, decentralised ledger that is particularly valuable in sensitive legal contexts where data manipulation could alter outcomes.

*Motivation:* India’s legal system faces challenges of delay, document mismanagement, lack of access, and limited transparency. Lawyers spend disproportionate time on administrative tasks while clients remain uninformed about their case progress. The motivation behind Kacheri Diaries AI stems from a vision to bring speed, structure, and trust to the Indian legal ecosystem. By combining AI’s analytical power with blockchain’s security, our platform empowers legal professionals to work smarter and helps clients stay informed, secure, and confident in their legal journey. Our goal is to enable a tech-driven, paperless, and accountable legal infrastructure that serves every citizen equally.



### Project Details



**Overview of the Technology Stack to be Used**



*Frontend:*

•⁠  ⁠React.js with TypeScript for responsive and modular UI

•⁠  ⁠TailwindCSS for utility-first styling

•⁠  ⁠Progressive Web App (PWA) support for mobile-first usage



*Backend:*

•⁠  ⁠Node.js with Express for server-side logic

•⁠  ⁠Python (FastAPI) for AI/ML model integration and microservices



*Database:*

•⁠  ⁠PostgreSQL for structured legal records and case data

•⁠  ⁠MongoDB for flexible document storage

•⁠  ⁠IPFS (InterPlanetary File System) for decentralised document storage linked with blockchain



*AI & NLP Stack:*

•⁠  ⁠OpenAI/GPT API or custom-trained transformer models for:

  - Document summarisation

  - Legal research insights

  - Argument generation

•⁠  ⁠Tesseract.js for OCR (Optical Character Recognition)



*Blockchain Layer:*

•⁠  ⁠Polygon / Ethereum Layer 2 for gas-efficient smart contracts

•⁠  ⁠Smart contracts for timestamping, file integrity, and access logging

•⁠  ⁠Chainlink oracles for cross-chain verification and court-related event triggers



*Cloud Infrastructure & DevOps:*

•⁠  ⁠AWS (S3, EC2, Lambda) or GCP for scalable deployment

•⁠  ⁠Docker and Kubernetes for containerisation and orchestration

•⁠  ⁠GitHub Actions for CI/CD pipelines



**Documentation of Core Components, Protocols, and Architecture**

*Core Components:*

•⁠  ⁠*OCR Engine*: Scans and digitises case files, feeding into NLP modules

•⁠  ⁠*Document Summariser & Classifier*: Categorises, tags, and summarises legal documents

•⁠  ⁠*Blockchain Evidence Vault*: Upload and verify legal documents via tamper-proof hashing

•⁠  ⁠*Smart Calendar & Reminder Engine*: Syncs hearing schedules, deadlines, and action points

•⁠  ⁠*Client-Lawyer Communication Interface*: Secure chat and voice messaging

•⁠  ⁠*Legal Draft Builder*: Generates contracts, notices, and petitions using guided AI templates



*Architecture:*

•⁠  ⁠Microservices architecture using RESTful APIs and message queues (e.g., RabbitMQ)

•⁠  ⁠Stateless backend with JWT authentication and role-based access control

•⁠  ⁠Decentralised evidence flow with smart contracts for auditability and ownership tracking

•⁠  ⁠Modular AI services connected via REST and/or gRPC endpoints



**Any PoC/MVP or Prior Work**

 ⁠A working *OCR + summarisation pipeline* has been developed using Tesseract.js and HuggingFace Transformers.

•⁠  ⁠A basic *blockchain-integrated evidence upload prototype* using IPFS + Ethereum smart contracts has been successfully tested.

•⁠  ⁠Created draft templates and NLP models trained on publicly available legal documents and court judgements (e.g., Indian Kanoon cases).

•⁠  ⁠Built internal testing UI with case file upload, auto-classification, and AI-generated summaries for mock cases.



**Mockups / UI Designs**



We have designed preliminary UI mockups for:

•⁠  ⁠*Client Dashboard*: Visual case timeline, document uploads, legal status bar

•⁠  ⁠*Lawyer Interface*: Case overview, smart reminders, draft builder, AI research tab

•⁠  ⁠*Blockchain Vault UI*: Upload → hash → timestamp flow with verification QR code

•⁠  ⁠*Lawyer Discovery Module*: Filters, profile cards, consultation booking system.



**Data Models / API Specifications of Core Functionality**



*Sample Data Models:*

•⁠  ⁠⁠ User ⁠: { userID, role, name, contact, verified }

•⁠  ⁠⁠ Case ⁠: { caseID, userID, lawyerID, caseType, status, hearingDates[], summary, evidence[] }

•⁠  ⁠⁠ Document ⁠: { docID, caseID, type, OCRtext, summary, blockchainHash, uploadTimestamp }

•⁠  ⁠⁠ Message ⁠: { messageID, senderID, receiverID, text/audio, timestamp }



*Sample API Endpoints:*

•⁠  ⁠⁠ POST /upload/document ⁠: Upload legal documents for OCR + blockchain

•⁠  ⁠⁠ GET /case/:id/summary ⁠: Fetch AI-generated summary

•⁠  ⁠⁠ POST /generate/draft ⁠: AI-assisted document creation

•⁠  ⁠⁠ GET /vault/:docID/verify ⁠: Validate blockchain record

•⁠  ⁠⁠ GET /lawyer/discover ⁠: Search and filter lawyers.



**What the Project is *Not / Will Not Provide**



•⁠  ⁠*Not a substitute for legal advice or licensed legal counsel: Kacheri Diaries AI is an **assistive tool*, not a replacement for human lawyers.

•⁠  ⁠*Will not offer real-time legal representation in court*: The platform supports preparation and management, but does not appear on behalf of clients in court.

•⁠  ⁠*Not a public blockchain platform*: The blockchain features are used strictly for private, secure recordkeeping—not for public ledger access.

•⁠  ⁠*No end-to-end litigation services*: Kacheri Diaries AI focuses on document and workflow management, not full-scale litigation or arbitration processes.

•⁠  ⁠*Will not provide legal opinion or case outcome prediction*: We deliberately avoid predictive analysis that may bias legal decisions or outcomes.



### Ecosystem Fit



*Where and How Does Your Project Fit into the Ecosystem?*

Kacheri Diaries AI fits into the *Polkadot ecosystem* as a *legaltech application focused on decentralised justice infrastructure, bringing blockchain-backed document integrity, secure identity, and transparent case management to India’s legal sector. Leveraging **substrate-based chains* or integrating with *parachains* like KILT (for decentralised identity) or Crust/IPFS (for file storage), our project introduces *verifiable evidence flows and trusted data interoperability* to a field that has historically lacked digitisation and transparency.



By integrating blockchain for *proof-of-integrity* and *tamper-proof recordkeeping, we contribute to Polkadot’s broader vision of building **real-world, interoperable, decentralised applications* that go beyond finance and touch governance and civil systems.



*Who Is Your Target Audience?*



Kacheri Diaries AI has a two-fold user base:



•⁠  ⁠*Legal Professionals (Lawyers & Law Firms)*:

  - Use AI tools for drafting, legal research, scheduling, and document automation.

  - Store and access evidence securely through blockchain-backed verification.



•⁠  ⁠*Clients (Citizens, Startups, SMEs, and Litigants)*:

  - Individuals seeking justice, legal clarity, or representation.

  - Particularly helpful for underrepresented or rural users who lack legal literacy.

  - Startups and businesses needing quick contract drafting, dispute documentation, and evidence protection.



*What Need(s) Does Your Project Meet?*



•⁠  ⁠*Trust & Transparency in Legal Documents: Legal systems suffer from document tampering and data fraud. Blockchain ensures **verifiable authenticity*.

•⁠  ⁠*Efficiency for Legal Professionals*: Reduces repetitive tasks like summarising, drafting, and scheduling, thus saving time.

•⁠  ⁠*Access to Legal Services*: Empowers clients with limited resources to understand and track their legal matters.

•⁠  ⁠*Secure Evidence Management: No more lost documents or unverified records – the platform ensures **immutable storage*.

•⁠  ⁠*Digital Transformation of Indian Courts*: Supports India’s goal of eCourts and paperless hearings with backend tech and client education.



*Are There Any Other Projects Similar to Yours in the Polkadot Ecosystem?*



#### a) *If so, how is your project different?*

While *decentralised identity (KILT), **data storage (Crust), and **DAO governance tools* exist within Polkadot, very few (if any) projects are addressing the *legaltech vertical with a client-facing and lawyer-supporting AI platform*.



What makes Kacheri Diaries AI different:

•⁠  ⁠Combines *AI + Blockchain* specifically for legal workflows

•⁠  ⁠Designed for the *Indian judiciary system*, a massive, underserved ecosystem

•⁠  ⁠Dual-interface targeting both lawyers and litigants

•⁠  ⁠Rich features like *draft generators, argument builders, and smart court templates*



#### b) *If not, why might such a project not exist yet?*

Legaltech is a *complex and highly localised* industry—each country has its own system, laws, and language barriers. This has likely deterred global Web3 players from entering the space. Additionally, *few teams combine deep domain knowledge in both law and AI/blockchain*, which is crucial to build a platform like Kacheri Diaries AI.



India, with its large backlog of cases and push for digital governance, provides a unique and *high-impact opportunity* for such a solution to emerge—and we aim to pioneer that within the Polkadot ecosystem.



## Team Details



**Team Name:** Kacheri Diaries LLP

**Contact Name:** Samarth Shukla

**Contact Email:** info@kacheridiaries.com

**Website:** www.kacheridiaries.com



*Team members*



Samarth Shukla - Founder | CEO 

Aditya Daryani - CoFounder | CMO

Devansh Srivastava - CoFounder | CFO 

Mehul Mendhiratta - Operations Head 



#### LinkedIn Profiles



https://www.linkedin.com/in/samarth-shukla-418144170/

https://www.linkedin.com/in/adityadaryani/

https://www.linkedin.com/in/devansh-srivastava-12a409313/

https://www.linkedin.com/in/mehul-mendhiratta-455bab27a/



## Development Roadmap



*Overview*

•⁠  ⁠*Estimated Duration*: 3 Months  

•⁠  ⁠*Full-Time Equivalent (FTE)*: 2.5 FTE (2 full-time devs, 1 part-time AI/blockchain researcher)  

•⁠  ⁠*Total Costs: *$10,000 USD**



*Mandatory Deliverables*



| Number | Deliverable | Specification |
|--------|-------------|---------------|
| 0a. | *License* | The entire codebase will be released under the *MIT License* to ensure community accessibility and wide adoption. |
| 0b. | *Documentation* | We will provide *inline documentation* for all major components. Additionally, a *user and developer guide* will be written that explains the architecture, installation process, and usage of the lawyer and client interfaces with blockchain integration. |
| 0c. | *Testing and Testing Guide* | All core modules will have *>=90% unit test coverage, including OCR, smart contract logic, and document handling. A **testing manual* will explain how to run tests using Jest (frontend) and PyTest/Mocha (backend/blockchain). |
| 0d. | *Article* | An in-depth *medium/blog article* will be published detailing the project's background, motivation, Polkadot integration, challenges solved, architecture choices, and outcomes. It will also cover how to deploy and contribute to the project. |



*Milestone 1 – AI-Powered OCR and Summarisation Engine*



*Cost*: $5,000  

*Duration*: 1.5 months  

 ⁠*Deliverables*:

  - Implement OCR document scanning pipeline using *Tesseract.js*.

  - Integrate *AI-based summarisation module* using HuggingFace transformers for legal text.

  - Build backend endpoints (⁠ /upload ⁠, ⁠ /summarise ⁠) in *FastAPI*.

  - Store results in MongoDB/Postgres linked to case IDs.

  - Create minimal UI for document upload and summary display.



*Verification*:

  - Reviewer can upload sample case files (PDFs/images) and view digitised + summarised outputs via test frontend.

  - Test cases to validate summarisation accuracy, OCR success rate, and metadata tagging.



*Milestone 2 – Blockchain-Based Document Vault + Legal Draft Preset Builder*



*Cost*: $5,000  

*Duration*: 1.5 months  

*Deliverables*:

  - Create smart contracts (Solidity) on *Polygon testnet* to:

  - Hash and timestamp document uploads

  - Verify authenticity and prevent tampering

  - Integrate with *IPFS* for decentralised document storage.

  - Build UI for users (clients/lawyers) to:

  - Upload documents to the vault

  - Verify documents with QR/transaction hash

  - Add AI-based *legal draft builder*: Generate notices/agreements using OpenAI + editable templates.



*Verification*:

  - Reviewer uploads a document → system returns hash + transaction + IPFS link.

  - Reviewer tests document verification.

  - Reviewer uses draft builder to generate a legal contract and edit key fields (name, date, clauses, etc.).

  - All source code, testnet contracts, and IPFS links provided for verification.



## Budget Breakdown by Milestone



| Milestone | Deliverables | Cost (USD) | Estimated Completion |
|-----------|--------------|------------|-----------------------|
| 1 | *AI-Powered OCR & Document Summarisation Engine<br>• OCR-based client file scanning system<br>• AI-powered document summarisation (legal-specific)<br>• Backend APIs & frontend UI for document upload and viewing<br>• Database integration for client file management | *$5,000** | *1.5 months* |
| 2 | *Blockchain-Based Document Vault + Legal Draft Preset Builder<br>• Smart contracts for document verification & timestamping<br>• IPFS integration for decentralised legal file storage<br>• UI for document hash verification<br>• AI-powered legal draft builder with editable templates | *$5,000** | *1.5 months* |
| *Total* |  | *$10,000* | *3 months* |



## Future Plans



After the successful completion of the Fast-Grant, *Kacheri Diaries AI* will continue to scale its features, expand market reach, and deepen integration within the *Polkadot ecosystem*. Our roadmap for the next phase includes:





*Continued Development*

*Smart Calendar & Case Tracker*: We plan to implement an AI-powered legal calendar and hearing management tool that syncs with local court schedules and sends intelligent reminders.

*Voice-to-Text Dictation for Lawyers*: Integrate voice input and transcription features, helping lawyers dictate notes or arguments directly into case files.

*Court-Specific Templates*: Add jurisdiction-based formatting for courts like the Indian Supreme Court, High Courts, etc., increasing document submission efficiency.

*Conflict Checker Module*: To alert lawyers of any potential conflicts of interest based on client history and previous cases.

*Mobile App Interface*: Build mobile-first access for clients and advocates, especially targeting rural India.



---



## Funding Strategy

To support our long-term roadmap, we plan to pursue:

*Web3 Ecosystem Grants* from parachains such as *KILT* (for decentralised identity), *Crust Network* (for decentralised storage), and *Moonbeam* (for smart contract expansion).

*Equity-Free Legaltech Accelerators* from the Indian government and international legal innovation hubs.

*Venture Capital* through strategic legaltech and AI-focused VC firms after the next MVP milestone, particularly targeting those supporting *GovTech and RegTech*.

*Revenue Streams* from tiered SaaS offerings for lawyers/firms, contract auto-generation, and document verification APIs.



*Vision & Ecosystem Impact*

We aim to become *the default decentralised legal assistant* across emerging economies, starting with India. By bringing *transparency, accessibility, and integrity* into the legal space using *Polkadot’s infrastructure*, we hope to:

•⁠  ⁠Increase trust in legal systems through *verifiable, tamper-proof digital evidence*.

•⁠  ⁠Empower 1.4B+ citizens with transparent legal representation tools.

•⁠  ⁠Serve as a *legal bridge* connecting government, judiciary, and citizens through Web3 technology.



We envision Kacheri Diaries AI evolving into a *composable legal infra-layer* that other Polkadot dApps can plug into for authentication, legal compliance, dispute resolution, or evidence handling.