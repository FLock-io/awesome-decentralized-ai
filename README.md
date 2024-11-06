# ✨ SoK: Decentralized AI (DeAI)

The centralization of Artificial Intelligence (AI) presents significant challenges, including susceptibility to single points of failure, embedded biases, data privacy issues, and scalability limitations. These challenges are particularly evident in closed-source large language models (LLMs), where user data is collected and potentially misused without sufficient oversight. To address these issues, blockchain-based decentralized AI (DeAI) has emerged as a promising solution, leveraging the strengths of both blockchain and AI technologies. Blockchain provides transparency, security, and decentralization, which enhance the trustworthiness and efficiency of AI systems.

In this work, we present a Systematization of Knowledge (SoK) for blockchain-based DeAI protocols, providing a detailed taxonomy of current approaches and analyzing their impact on security, decentralization, and scalability. We systematically review academic literature and industry practices to explore the benefits of DeAI, such as improved security and decentralized data management, as well as the challenges, including scalability, computational overhead, and data privacy. Additionally, we examine the functionalities of existing DeAI platforms, evaluate their approaches to decentralization and security, and identify potential vulnerabilities.  We identify significant opportunities for integrating blockchain and AI to create a more democratized, transparent, and privacy-preserving ecosystem, while highlighting the technical and theoretical challenges that remain.

This repo contains the list of papers and protocols surveyed in our SoK paper.

## 📚 Table of Content (ToC)
- [SoK: Decentralized AI (DeAI)](#sok-decentralized-ai-deai)
  - [Table of Content (ToC)](#table-of-content-toc)
  - [0. Overview of DeAI Projects](#0-overview-of-deai-projects)
  - [1. Task Proposing](#1-task-proposing)
  - [2. Pre-Training](#2-pre-training)
    - [2.1. Data Preparation](#21-data-preparation)
      - [2.1.1. Industry](#211-industry)
      - [2.1.2. Academic Work](#212-academic-work)
    - [2.2. Compute](#22-compute)
      - [2.2.1. Industry](#221-industry)
      - [2.2.2. Academic Work](#222-academic-work)
  - [3. On-training](#3-on-training)
    - [3.1. Industry](#31-industry)
    - [3.2. Academic Work](#32-academic-work)
  - [4. Post-training](#4-post-training)
    - [4.1. Model Inference](#41-model-inference)
      - [4.1.1. Industry](#411-industry)
      - [4.1.2. Academic Work](#412-academic-work)
    - [4.2. Application](#42-application)
      - [4.2.1. Industry](#421-industry)
      - [4.2.2. Academic Work](#422-academic-work)
    - [4.3. Marketplace](#43-marketplace)
      - [4.3.1. Industry](#431-industry)
      - [4.3.2. Academic Work](#432-academic-work)

### 0. Overview of DeAI Projects

| Project          | Task Creation | Data Preparation |  Compute | Training | Inference | Marketplace | Application | Incentive Mechanism | Enhanced Security | Permission Control | Data Storage | Public Reference | Auditability | ML Assets Tokenization | Decentralization | Security Assumption                    |
|------------------|---------------|------------------|-----------------------|------------------------|----------------|-------------------|-------------|---------------------|-------------------|--------------------|--------------|------------------|--------------|------------------------|------------------|----------------------------------------|
| Bittensor        | ●             | ○                | ○                     | ●                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                | Staking                                |
| FLock            | ●             | ○                | ○                     | ●                      | ●              | ●                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                | Staking                                |
| Vana             | ●             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking, ZKP                           |
| Fraction AI      | ●             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking, Reputation-based consensus     |
| Ocean            | ●             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking                                |
| Numbers          | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | (Delegated) proof-of-stake             |
| The Graph        | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking?                               |
| Synternet        | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking?                               |
| OriginTrail      | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking?                               |
| ZeroGravity      | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Proof-of-stake                         |
| Grass            | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | ZKP                                    |
| OORT             | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking                                |
| KIP              | ●             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking?                               |
| Shinkai          | ●             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Staking                                |
| Filecoin         | ○             | ●                | ○                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                | Proof-of-Replication, Proof-of-Spacetime|
| Lilypad          | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Reputation & Dispute mechanism         |
| IO.NET           | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| NetMind          | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking, Proof of Authority(?)         |
| Render Network   | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| Akash            | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Nosana           | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Tromero          | ○             | ●                | ●                     | ●                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| OctaSpace        | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Inferix          | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Proof of Rendering                     |
| AlphaNet         | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| DeepBrain Chain  | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Exabits          | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| OpSec            | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking, Proof of Cloud, ZKP           |
| Gensyn           | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Proof-of-Learning, Staking             |
| Ritual           | ○             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| Numerai          | ○             | ○                | ○                     | ●                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                | Staking                                |
| Prime Intellect  | ○             | ○                | ●                     | ●                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| Commune AI       | ●             | ○                | ●                     | ○                      | ○              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Modulus          | ○             | ○                | ○                     | ○                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ZKP                                    |
| Hyperspace       | ○             | ○                | ○                     | ○                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Fraud Proof                            |
| Sertn            | ○             | ○                | ○                     | ○                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ZKP                                    |
| ORA              | ○             | ○                | ○                     | ○                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Fraud Proof                            |
| Allora           | ○             | ○                | ○                     | ○                      | ●              | ○                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Fetch AI         | ●             | ●                | ○                     | ○                      | ○              | ●                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | POW, Reputation-based scores           |
| Sentiment        | ○             | ○                | ○                     | ○                      | ○              | ●                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Sentient Protocol                      |
| Arbius           | ○             | ○                | ○                     | ○                      | ○              | ●                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | POW, Staking                           |
| Theoriq          | ○             | ○                | ○                     | ○                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Proof of Collaboration, Staking        |
| ELNA             | ○             | ○                | ○                     | ○                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Delysium         | ○             | ○                | ○                     | ○                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| OpenServ         | ●             | ○                | ○                     | ○                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| Autonolas        | ○             | ○                | ○                     | ○                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Staking                                |
| Compass Labs     | ○             | ○                | ○                     | ○                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| OpenAgents       | ○             | ○                | ○                     | ○                      | ○              | ●                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ?                                     |
| Immutable Labs   | ○             | ○                | ○                     | ○                      | ○              | ●                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Proof of Usage?, Ranking Systems       |
| SingularityNET   | ○             | ○                | ○                     | ○                      | ○              | ●                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Reputation Mechanism                   |
| SaharaAI         | ○             | ○                | ○                     | ○                      | ○              | ●                 | ○           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Proof-of-stake                         |
| Balance DAO      | ○             | ○                | ○                     | ○                      | ○              | ●                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | Nominated proof-of-stake               |
| NOYA             | ○             | ○                | ○                     | ○                      | ○              | ○                 | ●           | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                | ZKP                                    |

### 1. Task Proposing

### 2. Pre-Training

#### 2.1. Data Preparation

##### 2.1.1. Industry

- **Ocean** [[whitepaper](https://oceanprotocol.com/tech-whitepaper.pdf)] [[docs](https://docs.oceanprotocol.com/)] [[code](https://github.com/oceanprotocol)]
- **Vana** [[docs](https://docs.vana.org/docs/incentitives)] [[code](https://github.com/vana-com)]
- **Fraction AI** [[docs](https://docs.fractionai.xyz/)] 
- **Numbers** [[whitepaper](https://docs.numbersprotocol.io/introduction/whitepaper)] [[docs](https://docs.numbersprotocol.io/)] [[code](https://github.com/numbersprotocol)]

##### 2.1.2. Academic Work

#### 2.2. Compute

##### 2.2.1. Industry

- **Lilypad** [[docs](https://docs.lilypad.tech/lilypad)] [[code](https://github.com/lilypad-tech/lilypad)]
- **Gensyn** [[whitepaper](https://docs.gensyn.ai/litepaper)]
- **Render Network** [[whitepaper](https://framerusercontent.com/modules/assets/Wa2lC0JcjksdQEKLA1PAvTHXe3Y~o---EuM8cIAdZuUrwHjJw7JcrKvj9afAV9nk7wmVsbo.pdf)] [[docs](https://rendernetwork.com/getting-started/)]
- **IO.NET** [[docs](https://docs.io.net/docs/inception)] 
- **Akash** [[whitepaper](https://akash-web-prod.s3.amazonaws.com/uploads/2020/03/akash-econ.pdf)] [[docs](https://akash.network/docs/)] [[code](https://github.com/akash-network)]
- **NetMind** [[whitepaper](https://netmind-power.gitbook.io/white-paper)] [[docs](https://netmind-power.gitbook.io/netmind-power-documentation)] [[code](https://github.com/protagolabs/Netmind-examples)
]

##### 2.2.2. Academic Work

### 3. On-training
#### 3.1. Industry
- **Bittensor** [[whitepaper](https://bittensor.org/wp-content/uploads/2024/02/bittensor.org-whitepaper.pdf)] [[docs](https://docs.bittensor.com/)] [[code](https://github.com/opentensor/BitTensor)]
- **Numeraire** [[whitepaper](https://numer.ai/whitepaper.pdf)] [[docs](https://docs.numer.ai/)] [[code](https://github.com/erasureprotocol/NMR)]
- **Commune AI** [[whitepaper](https://ai-secure.github.io/DMLW2022/assets/papers/7.pdf)] [[docs](https://commune-t.pages.dev/docs/next/Introduction)] [[code](https://github.com/commune-ai)]
- **FLock** [[whitepaper](https://www.flock.io/whitepaper)] [[docs](https://docs.flock.io/)] [[code](https://github.com/FLock-io)]

#### 3.2. Academic Work

#### 4. Post-training

##### 4.1. Model Inference

###### 4.1.1. Industry

- **Allora** [[whitepaper](https://whitepaper.assets.allora.network/whitepaper.pdf)] [[docs](https://docs.allora.network/home/explore)] [[code](https://github.com/allora-network)]

- **Sertn** [[whitepaper](https://public.inferencelabs.com/sertn-whitepaper.pdf)] [[docs](https://docs.inferencelabs.com/)] [[code](https://github.com/inference-labs-inc)]

- **ORA** [[whitepaper](https://arxiv.org/abs/2401.17555)] [[docs](https://docs.ora.io/doc)] [[code](https://github.com/ora-io)]

###### 4.1.2. Academic Work

##### 4.2. Application

###### 4.2.1. Industry

- **Fetch** [[whitepaper](https://media.abnnewswire.net/media/en/whitepaper/rpt/96506-Fetch_WP.pdf)] [[docs](https://fetch.ai/docs/guides)] [[code](https://github.com/fetchai)]
- **Morpheus** [[whitepaper](https://mor.org/whitepaper)] [[docs](https://github.com/MorpheusAIs/Docs)] [[code](https://github.com/MorpheusAIs/Docs)]

###### 4.2.2. Academic Work

##### 4.3. Marketplace

###### 4.3.1. Industry

- **Balance AI** [[docs](https://docs.balanceai.network/)] [[code](https://github.com/balanceainetwork/task-oriented-agents-poc)]
- **SingularityNET** [[whitepaper](https://public.singularitynet.io/whitepaper.pdf)] [[docs](https://dev.singularitynet.io/docs/concepts/)] [[code](https://github.com/singnet/)]
- **Immutable** [[whitepaper](https://uploads-ssl.webflow.com/646557ee455c3e16e4a9bcb3/6499367de527dd82ab7475a3_Immutable%20Whitepaper%20Update%202023%20(3).pdf)] [[docs](https://docs.immutable.com/)] [[code](https://github.com/ImmutableLabs)]

###### 4.3.2. Academic Work
