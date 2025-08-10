# ADC AssetGuard + AI — Polkadot/Substrate Integration

## Project Overview
**One-liner:** Open-source multi-chain asset validator with **AI risk scoring**, **ISO 20022–inspired XML export**, and planned **Polkadot/Substrate integration** to assess NFTs/tokens on Polkadot parachains.  

**Current Live Demo:** https://adc-assetguard-ai.onrender.com  

**Problem.** Users and builders face scam NFTs/tokens and opaque asset risk across chains. In Polkadot, there is no dedicated open-source tool that scores asset risk, generates audit-ready reports, and can be extended to parachains.  

**Solution.**  
- Build and open-source a Polkadot/Substrate integration module for ADC AssetGuard + AI.  
- Initial parachains: **Moonbeam** (EVM) and **Astar** (EVM + Substrate).  
- Features:
  - Fetch on-chain asset metadata from parachains.
  - Run **AI risk scoring** (signals: contract provenance, holder distribution, age, tx patterns, blacklist flags).
  - Export **ISO 20022–inspired XML** reports for audits.
  - Provide public API + UI for easy testing.
- Future (post-grant): mobile app version (Android/iOS), enhanced AI engine, bot alert system, and full on-chain reporting.

**Founder Status:** Solo founder (Muhammad Yusri Adib, ADCX Lab). All current development, AI logic, API integration, and UI have been done individually without external funding. Upon receiving the grant, I will onboard a small technical team to accelerate delivery and long-term maintenance.

---

## Team
- **Muhammad Yusri Adib (ADCX Lab)** — Solo founder & developer  
  GitHub: https://github.com/ADCoinX  
  LinkedIn: https://www.linkedin.com/in/yusri-adib-455aa8b7  
  Email: admin@autodigitalcoin.com  
  Telegram: @ADCoinhelpline  
  Twitter: https://twitter.com/AdCoinMy  

---

## Previous Work / MVP Links
- Live validator (multi-chain global version): https://adc-assetguard-ai.onrender.com  
- Validator codebase (on request — public repo planned for grant delivery)  

---

## Technical Approach
- **Backend:** Python (Flask), modular adapters per chain.
- **Polkadot/Substrate:**  
  - Use `substrate-interface` Python library for RPC queries.
  - Target Moonbeam (EVM) & Astar (EVM/Substrate) in Milestone 1.
- **AI Scoring:** Rule-based + heuristics (age, holders, liquidity/tx patterns, blacklist sources), pluggable for parachain-specific signals.
- **Export:** ISO 20022–inspired XML generator (audit-style), schema documented.
- **UI:** HTML/CSS/JS frontend (lightweight) connected to backend APIs.
- **Docs:** README + API reference (endpoints, params, examples), integration guide.

---

## License
MIT (OSI-approved). Code produced under this grant will be open-source and not depend on closed-source components.

---

## Ecosystem Benefit
- Adds a **reusable OSS Polkadot connector** for asset due diligence.
- Improves user safety across parachains.
- Provides audit-style evidence reports for exchanges, wallets, and auditors.
- Extensible for more parachains and asset types.

---

## Maintenance
- Ongoing maintenance in public repo.
- Accept community PRs; publish minor updates post-grant.
- Establish dedicated dev team upon receiving funding.

---

## Milestones & Budget

**Total Grant Request:** $30,000 USD (in DOT)  
**Founder Salary:** $1,500 USD/month × 4 months = $6,000 USD  
**Development & Infrastructure:** $24,000 USD

---

### Milestone 1 — Polkadot/Substrate Connector (Moonbeam + Astar)
- **Grant amount:** $15,000 USD  
  - Development: $11,000 USD  
  - Founder salary: $4,000 USD (2 months × $1,500)
- **Timeline:** 8 weeks from acceptance
- **Deliverables:**
  1. Open-source adapter module for Moonbeam & Astar:
     - Asset/contract metadata fetch
     - Owner/holder snapshot & distribution metrics
  2. Integration with AssetGuard AI scoring pipeline
  3. Public API endpoints + example queries
  4. Documentation:
     - Setup & run locally
     - How to add new parachains
  5. Public demo for at least 3 sample assets per chain
- **Acceptance criteria:**
  - Code compiles & runs from clean clone
  - Returns asset metadata + AI score
  - Documentation enables reproducibility

---

### Milestone 2 — ISO XML Export + Public Demo & Docs
- **Grant amount:** $15,000 USD  
  - Development: $13,000 USD  
  - Founder salary: $2,000 USD (~1.33 months × $1,500)
- **Timeline:** 6 weeks after Milestone 1
- **Deliverables:**
  1. ISO 20022–inspired XML export for Polkadot adapter results
  2. Web demo to validate asset & download XML report
  3. Developer docs: endpoint reference, XML schema, integration guide
  4. Test suite for adapter & XML generator
  5. Short video walkthrough embedded in README
- **Acceptance criteria:**
  - XML validates against published schema
  - Demo live & reproducible locally
  - Tests pass in CI

---

## Future Plans (Post-Grant)
- Mobile app version (Android/iOS)
- AI engine upgrade with ML-based anomaly detection
- Automated bot alerts for high-risk assets
- Full on-chain reporting for public audits

---

## Risks & Mitigations
- **API/Indexing variance across parachains:** Use adapter pattern; document differences.
- **Data gaps:** Flag missing fields clearly.
- **Scope creep:** Stick to milestone deliverables; extras moved to future roadmap.

---

## What this project is NOT
- Not a token sale, exchange, or gambling platform.
- Not a closed-source SaaS; all grant-funded code will be MIT-licensed.

---

## Closing Statement
I am building this completely solo, with no funding, because I believe the Polkadot ecosystem deserves strong, transparent, and open-source security tooling.  
This grant is not just funding — it is the chance for me to expand from a solo developer into a small team, deliver on my vision for AI-powered asset validation, and make this tool a core part of Polkadot's safety infrastructure.  
I genuinely want this grant as it will allow me to dedicate my full energy to building, integrating, and maintaining this project for the community, while ensuring it remains open-source and accessible to everyone.
