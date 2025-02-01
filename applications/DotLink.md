# DotLink: Lightweight Polkadot IoT SDK

## Project Overview

### Tagline
**DotLink**: Enabling IoT devices to seamlessly interact with the Polkadot ecosystem through a lightweight, cross-platform SDK.

### Brief Description
DotLink is an open-source, lightweight SDK designed to enable seamless blockchain interactions for Internet of Things (IoT) devices using the Polkadot ecosystem. Our mission is to provide a minimal, efficient, and cross-platform solution for connecting resource-constrained devices to decentralized networks.

### Integration with Polkadot/Kusama
DotLink integrates with the Polkadot ecosystem by providing a lightweight SDK that allows IoT devices to interact with Polkadot parachains and other Substrate-based blockchains. This enables IoT devices to participate in decentralized applications (dApps), submit transactions, and query blockchain state, all while operating within the constraints of limited computational resources.

### Team Motivation
Our team is passionate about bridging the gap between IoT and blockchain technology. We believe that IoT devices can play a crucial role in the decentralized future, and we aim to make it easier for developers to integrate these devices into the Polkadot ecosystem. By creating a lightweight SDK, we hope to empower developers to build innovative IoT applications that leverage the security and interoperability of Polkadot.

---

## Project Details

### Technology Stack
- **Primary Language**: C/C++ (for embedded systems)
- **Alternative Implementation**: Embedded Rust
- **MicroPython Bindings**: For easier integration with Python-based IoT platforms
- **Cryptography**: Elliptic Curve Cryptography (ECC) for secure key management and transaction signing
- **Networking**: WebSocket and HTTP for communication with Polkadot nodes

### Core Components
1. **Connectivity Module**: Handles network connections, including WebSocket and HTTP, with automatic reconnection capabilities.
2. **Cryptography Module**: Manages key generation, transaction signing, and signature verification.
3. **Blockchain Interaction Module**: Facilitates state queries, event subscriptions, and metadata retrieval.

### PoC/MVP
We are currently in the process of developing a **proof-of-concept (PoC)** that will demonstrate basic blockchain interactions, such as transaction signing and state queries, on an ESP32 microcontroller. The PoC will include a minimal implementation of the SDK, showcasing its core functionality in a controlled environment. While the PoC is not yet complete, we have made significant progress in designing the architecture and implementing key components in both C/C++ and MicroPython. Once finalized, the PoC will serve as the foundation for the **Minimum Viable Product (MVP)**, which will expand on these capabilities to support a wider range of IoT devices and use cases.

### Mockups/Designs
- **UI Components**: Since DotLink is primarily an SDK, there are no UI components. However, we provide example applications that demonstrate how to use the SDK in various IoT scenarios.
- **API Specifications**: The SDK will include a well-documented API for developers to interact with Polkadot parachains.

### What DotLink is *Not*
- DotLink is not a full-featured blockchain node. It is designed for lightweight interactions and does not support running a full node on IoT devices.
- DotLink does not provide a graphical user interface (GUI). It is a developer-focused SDK for integrating IoT devices with Polkadot.

---

## Ecosystem Fit

### Where and How DotLink Fits into the Ecosystem
DotLink fills a critical gap in the Polkadot ecosystem by enabling IoT devices to interact with the blockchain. This opens up new possibilities for decentralized IoT applications, such as supply chain tracking, smart cities, and environmental monitoring.

### Target Audience
- **IoT Developers**: Developers building IoT applications that require blockchain integration.
- **Polkadot/Substrate Developers**: Developers looking to extend their dApps to IoT devices.
- **Embedded Systems Engineers**: Engineers working on resource-constrained devices who need a lightweight SDK for blockchain interactions.

### Needs Addressed
- **Resource Efficiency**: IoT devices often have limited computational power and memory. DotLink addresses this by providing a minimal and efficient SDK.
- **Interoperability**: DotLink enables IoT devices to interact with Polkadot parachains, facilitating cross-chain communication.
- **Security**: DotLink includes robust cryptographic operations to ensure secure transactions and data integrity.

### Evidence of Need

- **Forum Discussions**: Discussions on the Polkadot Forum ([Polkadot Forum](https://forum.polkadot.network/)) have highlighted the need for lightweight solutions for IoT devices. Below are some key discussions that demonstrate the growing interest in IoT and resource-constrained device integration within the Polkadot ecosystem:
  - [Introducing the Robonomics Smart Home Demo Stand: Smarter, Safer Homes](https://forum.polkadot.network/t/introducing-the-robonomics-smart-home-demo-stand-smarter-safer-homes/2868)  
    This discussion showcases the potential of IoT devices in smart home applications and the need for lightweight solutions to integrate them with Polkadot.
  - [Elastic Scaling](https://forum.polkadot.network/t/elastic-scaling/7185)  
    Highlights the importance of scalability in blockchain networks, particularly for IoT use cases where thousands of devices may need to interact with the blockchain.
  - [Discussion: Highest Priority Pallet Functionality](https://forum.polkadot.network/t/discussion-highest-priority-pallet-functionality/3289)  
    Explores the need for optimized pallet functionality to support resource-constrained devices, such as IoT sensors and actuators.
  - [Exploring Geo Data, Real-Time Mapping, and AI Opportunities on Polkadot](https://forum.polkadot.network/t/exploring-geo-data-real-time-mapping-and-ai-opportunities-on-polkadot/10842)  
    Discusses the potential of IoT devices in geo-data collection and real-time mapping, emphasizing the need for lightweight SDKs to enable seamless integration.
  - [ATR Network: A Multimodal Supercomputing Network for Decentralized Private Data Training](https://forum.polkadot.network/t/atr-network-a-multimodal-supercomputing-network-for-decentralized-private-data-training/7645)  
    Highlights the importance of decentralized data processing, which can benefit from IoT devices connected to the Polkadot ecosystem.
  - [The Power of Vehicle Data for Everyone: LinkedCar](https://forum.polkadot.network/t/the-power-of-vehicle-data-for-everyone-linkedcar/6182)  
    Demonstrates the potential of IoT devices in the automotive industry and the need for lightweight solutions to connect vehicles to the blockchain.
  - [DC: Decentralized Cloud](https://forum.polkadot.network/t/dc-decentralized-cloud/6345)  
    Explores the concept of decentralized cloud computing, which can leverage IoT devices for edge computing and data collection.

- **Hackathon Projects**: Several hackathon projects have attempted to integrate IoT devices with Polkadot, but none have provided a reusable SDK like DotLink. These projects often face challenges related to resource constraints and lack of optimized tools, further emphasizing the need for a lightweight SDK tailored for IoT devices.

---

### Similar Projects
- **Polkadot.js**: A JavaScript library for interacting with Polkadot, but it is not suitable for resource-constrained IoT devices.
- **Substrate Connect**: A lightweight client for Substrate-based blockchains, but it is not optimized for IoT devices.

### Differentiation
DotLink is specifically designed for IoT devices, with a focus on minimal resource usage and cross-platform compatibility. Unlike Polkadot.js and Substrate Connect, DotLink provides a lightweight SDK that can run on microcontrollers like ESP32 and Arduino.

---

## Team

### Team Name
**MontaQ Labs**

### Contact Information
- **Contact Name**: Abhiraj Mengade
- **Contact Email**: abhiraj.mengade@outlook.com
- **Website**: [DotLink GitHub](https://github.com/MontaQLabs/DotLink)

### Team Members
1. **Abhiraj Mengade**
   - **Role**: Cloud Engineer at Oracle, Blockchain Developer
   - **LinkedIn**: [Abhiraj Mengade](https://www.linkedin.com/in/abhiraj-mengade)
   - **GitHub**: [abhiraj-mengade](https://github.com/abhiraj-mengade)
2. **Haoyang Li**
   - **Role**: UI/UX Designer, Rust Developer
   - **LinkedIn**: [Haoyang Li](https://www.linkedin.com/in/haoyang-li)
   - **GitHub**: [haoyang-li](https://github.com/haoyang-li)

### Team Code Repos
- [DotLink SDK](https://github.com/MontaQLabs/DotLink)

### Team's Experience
- **Abhiraj Mengade**: PBA Singapore Graduate (Distinction), Winner of OneBlock Bangkok Hackathon, EthIndia Hackathon '22 and '24, and AngelHack Polkadot Hackathon Europe.
- **Haoyang Li**: PBA Singapore Graduate, Winner of the 3rd Varathon, with expertise in Rust development and system security.

---

## Development Status

### Current Progress
- **PoC**: Currently performing research on implementation SDK in Micropython and C/C++
- **Research**: We have conducted extensive research on lightweight cryptography and IoT device constraints.
- **Documentation**: Initial documentation and API specifications are available on GitHub.

---

## Development Roadmap

### Overview
- **Estimated Duration**: 6-9 months  
- **Full-Time Equivalent (FTE)**: 2 FTE  
- **Total Costs**: $30,000 USD  

### Milestones

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | **License** | Apache 2.0 |
| **0b.** | **Documentation** | Inline code documentation and a basic tutorial |
| **0c.** | **Testing and Testing Guide** | Comprehensive unit tests and a testing guide |
| **0d.** | **Docker** | Dockerfile for testing the SDK |
| **0e.** | **Article** | Publish an article explaining the SDK's functionality |
| **1.** | **Core SDK (C/C++)** | Implement core functionality (connectivity, cryptography, blockchain interaction) in C/C++ |
| **2.** | **Core SDK (MicroPython)** | Implement core functionality (connectivity, cryptography, blockchain interaction) in MicroPython |
| **3.** | **Example Applications** | Provide example applications for ESP32, Arduino, and Raspberry Pi |

---

## Budget Breakdown

| Category | Item | Cost | Amount | Total | Description |
| --- | ---- | --- | --- | --- | --- |
| **Personnel** | **Senior C/C++ Developer** | $12,000 USD | 1 FTE | $18,000 USD | Leading the implementation of the SDK in C/C++, focusing on core functionality and optimization for IoT devices. |
| **Personnel** | **MicroPython Developer** | $9,000 USD | 0.5 FTE | $9,000 USD | Implementing the SDK in MicroPython and ensuring cross-platform compatibility. |
| **Equipment** | **Development Hardware** | $3,000 USD | 1 | $3,000 USD | Purchase of IoT devices for testing (ESP32, Arduino, Raspberry Pi). |
| **Miscellaneous** | **Contingency** | $3000 USD | 1 | $3000 USD | Buffer for unforeseen expenses (not required in this budget). |
| --- | --- | --- | **Total** | **$30,000 USD** |  |

---

### Notes:
1. **Timeline**: The project is planned for **6-9 months** to deliver a **Minimum Viable Product (MVP)**.  
2. **Personnel**:  
   - A **Senior C/C++ Developer** will lead the core implementation of the SDK, ensuring it is optimized for resource-constrained IoT devices.  
   - A **MicroPython Developer** will focus on implementing the SDK in MicroPython and ensuring cross-platform compatibility.  
3. **Equipment**: Funds are allocated for purchasing IoT devices (ESP32, Arduino, Raspberry Pi) for testing and development.  

---

## Future Plans

### Long-Term Maintenance
We plan to establish a community around DotLink to ensure its long-term maintenance and development. We will also seek additional funding through grants and partnerships.

### Short-Term Goals
- Enhance the SDK with additional features based on community feedback.
- Promote DotLink through workshops, hackathons, and online tutorials.

### Long-Term Vision
Our long-term goal is to make DotLink the go-to SDK for IoT developers looking to integrate their devices with the Polkadot ecosystem. We aim to support more platforms and provide advanced features like cross-chain interoperability.

---

## Additional Information

### Work Done
- Conducted research on lightweight cryptography and IoT device constraints.

### Funding
- Currently self-funded. We are exploring additional funding opportunities.

### Other Applications
- None
