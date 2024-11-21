# ✨ SoK: Decentralized AI (DeAI)

The centralization of Artificial Intelligence (AI) presents significant challenges, including susceptibility to single points of failure, embedded biases, data privacy issues, and scalability limitations. These challenges are particularly evident in closed-source large language models (LLMs), where user data is collected and potentially misused without sufficient oversight. To address these issues, blockchain-based decentralized AI (DeAI) has emerged as a promising solution, leveraging the strengths of both blockchain and AI technologies. Blockchain provides transparency, security, and decentralization, which enhance the trustworthiness and efficiency of AI systems.

In this work, we present a Systematization of Knowledge (SoK) for blockchain-based DeAI protocols, providing a detailed taxonomy of current approaches and analyzing their impact on security, decentralization, and scalability. We systematically review academic literature and industry practices to explore the benefits of DeAI, such as improved security and decentralized data management, as well as the challenges, including scalability, computational overhead, and data privacy. Additionally, we examine the functionalities of existing DeAI platforms, evaluate their approaches to decentralization and security, and identify potential vulnerabilities.  We identify significant opportunities for integrating blockchain and AI to create a more democratized, transparent, and privacy-preserving ecosystem, while highlighting the technical and theoretical challenges that remain.

This repo contains the list of papers and protocols investigated in our SoK.

![Figure1](assets/figure1.png)
**Figure 1: Comparison of different machine learning paradigms: (A) Standalone Learning, (B) Centralized Learning, (C) Distributed
Learning (Data Parallelism), (D) Centralized Federated Learning, (E) Decentralized Federated Learning (Ring All-reduce), and
(F) Decentralized Learning.**

![Figure2](assets/figure2.png)
**Figure2: A DeAI model lifecycle consists of four phases: 1.trask proposing, 2.pre-training, 3.on-training, and 4.post-training.**


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

| Project                                                                                                 | Task Creation | Data Preparation | Compute | Training | Model Inference | Model Marketplace | Agents | Incentive Mechanism | Enhanced Security | Permission Control | Data Storage | Public Reference | Auditability | AI Assets Tokenization | Decentralization[^2] | Staking | Security Guarantee                 |
|---------------------------------------------------------------------------------------------------------|---------------|------------------|---------|----------|-----------------|-------------------|--------|---------------------|-------------------|--------------------|--------------|------------------|--------------|------------------------|---------------------|---------|------------------------------------|
| [Vana](https://docs.vana.org/docs/home)                                                                 | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | ZKP                                |
| [Fraction AI](https://docs.fractionai.xyz/)                                                             | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | Reputation                         |
| [Ocean](https://oceanprotocol.com/tech-whitepaper.pdf)                                                  | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | On-chain Consensus                 |
| [Numbers](https://docs.numbersprotocol.io/introduction/whitepaper)                                       | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Stake                     |
| [The Graph](https://github.com/graphprotocol/research/blob/master/papers/whitepaper/the-graph-whitepaper.pdf) | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | On-chain Consensus                 |
| [Synternet](https://www.synternet.com/post/data-layer-whitepaper)                                        | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Delivery/Consumption      |
| [OriginTrail](https://origintrail.io/documents/Verifiable_Internet_for_Artificial_Intelligence_whitepaper_v3_pre_publication.pdf) | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Knowledge                 |
| [ZeroGravity](https://0g-whitepaper.pdf)                                                                | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Random Access             |
| [Grass](https://grass-foundation.gitbook.io/grass-docs)                                                 | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | ZKP + Reputation                   |
| [OORT Storage](https://assets-global.website-files.com/625d3de8b54ed13b7c1d0362/63c0c95964ca24dccb32a45a_Oort_light_paper.pdf) | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Honesty                   |
| [KIP](https://kipprotocol.gitbook.io/wp)                                                                | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ◑                   | ◑       | On-chain Consensus                 |
| [Filecoin](https://filecoin.io/filecoin.pdf)                                                            | ○             | ●                | ○       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ●            | ●                | ●            | ●                      | ●                   | ○       | Proof-of-Replication/Spacetime     |
| [IO.NET](https://docs.io.net/)                                                                          | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Reward + Slash                     |
| [NetMind](https://netmind-power.gitbook.io/white-paper)                                                 | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Authority                 |
| [Render Network](https://framerusercontent.com/modules/assets/Wa2lC0JcjksdQEKLA1PAvTHXe3Y~o---EuM8cIAdZuUrwHjJw7JcrKvj9afAV9nk7wmVsbo.pdf) | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Reputation + Proof of Render       |
| [Akash](https://akash-web-prod.s3.amazonaws.com/uploads/2020/03/akash-econ.pdf)                         | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Tendermint Consensus               |
| [Nosana](https://docs.nosana.io/)                                                                       | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | On-chain Consensus                 |
| [Inferix](https://docs.inferix.io/inferix-whitepaper)                                                   | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Rendering                 |
| [OctaSpace](https://whitepaper.octa.space/octaspace-whitepaper.pdf)                                     | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | On-chain Consensus                 |
| [DeepBrain Chain](https://cryptowhitepapersonline.com/wp-content/uploads/2023/08/deepbrain-chain.pdf)   | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Delegated Proof of Stake           |
| [OpSec](https://docs.opsec.computer/)                                                                   | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Delegated Proof of Stake           |
| [Gensyn](https://docs.gensyn.ai/litepaper)                                                              | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Learning                  |
| [Lilypad](https://docs.lilypad.tech/lilypad)                                                            | ○             | ○                | ●       | ○        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                   | ●       | Mediators + On-chain consensus     |
| [Bittensor](https://bittensor.com/whitepaper)                                                           | ◑             | ○                | ○       | ●        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Yuma Consensus                     |
| [FLock.io](https://www.flock.io/whitepaper)                                                             | ◑             | ○                | ○       | ●        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | FLock Consensus                    |
| [Numerai](https://numer.ai/whitepaper.pdf)                                                              | ○             | ○                | ○       | ●        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ◑       | On-chain Consensus                 |
| [Commune AI](https://commune-ai-docs)                                                                   | ◑             | ○                | ○       | ●        | ○               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ○                      | ◑                   | ●       | Yuma Consensus                     |
| [Modulus](https://modulus-white-paper)                                                                  | ○             | ○                | ○       | ○        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ○       | zkML                               |
| [Hyperspace](https://hyperspace-white-paper)                                                            | ○             | ○                | ○       | ○        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ○       | Fraud Proof                        |
| [Sertn](https://public.inferencelabs.com/sertn-whitepaper.pdf)                                          | ○             | ○                | ○       | ○        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ◑       | ZKP + FHE[^3] + MPC                |
| [ORA](https://arxiv.org/abs/2401.17555)                                                                 | ○             | ○                | ○       | ○        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | opML                              |
| [Ritual](https://docs.ritual.net/)                                                                      | ○             | ○                | ○       | ○        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | On-chain Consensus                 |
| [Allora](https://whitepaper.assets.allora.network/whitepaper.pdf)                                        | ○             | ○                | ○       | ○        | ●               | ○                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | CometBFT                           |
| [Fetch.AI](https://fetch.ai/blog/fetch-ai-economics-white-paper)                                        | ○             | ○                | ○       | ○        | ○               | ○                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Stake                     |
| [Arbius](https://arbius.ai/paper.pdf)                                                                   | ○             | ○                | ○       | ○        | ○               | ●                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Useful Work               |
| [Theoriq](https://theoriq-white-paper)                                                                  | ○             | ○                | ○       | ○        | ○               | ○                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof of Contribution/Collaboration |
| [Delysium](https://delysium.gitbook.io/whitepaper)                                                      | ○             | ○                | ○       | ○        | ○               | ○                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | On-chain Consensus                 |
| [OpenServ](https://docsend.com/view/6khsz4xw7ue8us5d)                                                   | ○             | ○                | ○       | ○        | ○               | ○                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ○       | On-chain Consensus                 |
| [Autonolas](https://olas.network/documents/whitepaper/Whitepaper%20v1.0.pdf)                            | ○             | ○                | ○       | ○        | ○               | ○                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Tendermint Consensus               |
| [ELNA](https://docs.elna.ai/elna-whitepaper)                                                            | ○             | ○                | ○       | ○        | ○               | ○                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | On-chain Consensus                 |
| [OpenAgents](https://arxiv.org/abs/2310.10634)                                                          | ○             | ○                | ○       | ○        | ○               | ○                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ○       | On-chain Consensus                 |
| [SingularityNET](https://public.singularitynet.io/whitepaper.pdf)                                       | ○             | ○                | ○       | ○        | ○               | ●                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ○       | Multi-Party Escrow                 |
| [SaharaAI](https://assets.saharalabs.ai/files/litepaper.pdf)                                            | ○             | ○                | ○       | ○        | ○               | ●                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof-of-Stake                     |
| [Shinkai](https://download.shinkai.com/Shinkai_Protocol_Whitepaper.pdf)                                 | ○             | ○                | ○       | ○        | ○               | ●                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | ZKP + MPC                          |
| [Balance DAO](https://docs.balanceai.network/)                                                          | ○             | ○                | ○       | ○        | ○               | ●                 | ●      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ●       | Proof-of-Stake                     |
| [Immutable Labs](https://assets.website-files.com/646557ee455c3e16e4a9bcb3/6499367de527dd82ab7475a3_Immutable%20Whitepaper%20Update%202023%20(3).pdf) | ○             | ○                | ○       | ○        | ○               | ●                 | ○      | ●                   | ●                 | ●                  | ○            | ●                | ●            | ●                      | ◑                   | ◑       | Green Proof of Work                |
| [Prime Intellect](https://docs.primeintellect.ai/introduction)                                       | ○             | ○                | ●       | ●        | ●               | ○                 | ○      | ○                   | ○                 | ○                  | ○            | ○                | ○            | ○                      | ○                   | ○       | Centralized Server                 |

**Decentralization**: We mark most existing DeAI solutions as 'partially' decentralized as they have centralized or off-chain components.

**FHE**: Fully Homomorphic Encryption.

**Prime Intellect**: We also present the project which aims to build DeAI without leveraging blockchain.

### 1. Task Proposing

#### 1.1 Academic Work

- **Trusted ai in multiagent systems: An overview of privacy and security for distributed learning**. C. Ma et al. Proceedings of the IEEE, vol. 111, no. 9, pp. 1097–1132, 2023. [[paper](https://arxiv.org/abs/2202.09027)]

- **Applications of distributed machine learning for the internet-of-things: A comprehensive survey**. M. Le et al. IEEE Communications Surveys & Tutorials, 2024. [[paper](https://arxiv.org/abs/2310.10549)]

- **Reinforcement learning: A survey**. L. P. Kaelbling et al. Journal of Artificial Intelligence Research, vol. 4, pp. 237–285, 1996. [[paper](https://arxiv.org/abs/cs/9605103)]

- **Markov games as a framework for multi-agent reinforcement learning**. M. L. Littman. Machine Learning Proceedings 1994, Elsevier, 1994, pp. 157–163. [[paper](https://www.sciencedirect.com/science/article/abs/pii/B9781558603356500271)]

- **UPDeT: Universal Multi-agent Reinforcement Learning via Policy Decoupling with Transformers**. S. Hu et al. International Conference on Learning Representations, 2021. [[paper](https://arxiv.org/abs/2101.08001)]

### 2. Pre-Training

#### 2.1. Data Preparation

##### 2.1.1. Industry

- **Ocean** [[whitepaper](https://oceanprotocol.com/tech-whitepaper.pdf)] [[docs](https://docs.oceanprotocol.com/)] [[code](https://github.com/oceanprotocol)]
- **Vana** [[docs](https://docs.vana.org/docs/incentitives)] [[code](https://github.com/vana-com)]
- **Fraction AI** [[docs](https://docs.fractionai.xyz/)] 
- **Numbers** [[whitepaper](https://docs.numbersprotocol.io/introduction/whitepaper)] [[docs](https://docs.numbersprotocol.io/)] [[code](https://github.com/numbersprotocol)]

##### 2.1.2. Academic Work

- **Data preprocessing in data mining**. S. García, J. Luengo, and F. Herrera. 2016. [[paper](https://link.springer.com/book/10.1007/978-3-319-10247-4)]

- **An introduction to variable and feature selection**. I. Guyon and A. Elisseeff. Journal of Machine Learning Research, vol. 3, pp. 1157–1182, 2003. [[paper](https://dl.acm.org/doi/10.5555/944919.944968)]

- **On the opportunities and risks of foundation models**. R. Bommasani et al. arXiv preprint arXiv:2108.07258, 2021. [[paper](https://arxiv.org/abs/2108.07258)]

- **Accelerators and specialized hardware for deep learning**. T. Ben-Nun and T. Hoefler. Communications of the ACM, vol. 62, no. 12, pp. 34–44, 2019. [[paper](https://htor.inf.ethz.ch/publications/img/distdl-preprint.pdf)]

- **Language models are unsupervised multitask learners**. A. Radford et al. OpenAI Blog, vol. 1, p. 9, 2019. [[paper](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)] [[code](https://paperswithcode.com/paper/language-models-are-unsupervised-multitask)]

- **Language models are few-shot learners**. T. B. Brown. arXiv preprint arXiv:2005.14165, 2020. [[paper](https://arxiv.org/abs/2005.14165)]

- **Exploring the limits of transfer learning with a unified text-to-text transformer**. C. Raffel et al. Journal of Machine Learning Research, vol. 21, pp. 1–67, 2020. [[paper](https://arxiv.org/abs/1910.10683)]

- **PaLM: Scaling language modeling with pathways**. A. Chowdhery et al., 2022. [[paper](https://arxiv.org/abs/2204.02311)]

- **LLama: Open and Efficient Foundation Language Models**. H. Touvron et al., 2023. [[paper](https://arxiv.org/abs/2302.13971)]

- **Will we run out of data? Limits of LLM scaling based on human-generated data**. L. Villalobos et al., 2022. [[paper](https://arxiv.org/abs/2211.04325)]

- **Blockchain versus federated learning: A comparative analysis for privacy-preserving applications**. M. J. M. Chowdhury et al. 2022. [[paper](https://ieeexplore.ieee.org/document/9734494)]

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

- **The backpropagation algorithm**. R. Rojas. Neural Networks: A Systematic Introduction, pp. 149–182, 1996. [[chapter](https://link.springer.com/chapter/10.1007/978-3-642-61068-4_7)]

- **In-datacenter performance analysis of a tensor processing unit**. N. P. Jouppi et al. Proceedings of the 44th Annual International Symposium on Computer Architecture, 2017. [[paper](https://ieeexplore.ieee.org/document/8192463)]

- **AI and compute**. D. Amodei and D. Hernandez. 2018. Available at: [[OpenAI blog](https://openai.com/blog/ai-and-compute/)]

- **AI is outpacing Moore’s law**. Z. Science. 2019. [[article](https://www.zmescience.com/science/ai-is-outpacing-moores-law/)]

- **Denoising diffusion probabilistic models**. J. Ho et al. Advances in Neural Information Processing Systems, vol. 33, pp. 6840–6851, 2020. [[paper](https://arxiv.org/abs/2006.11239)]

- **The EU General Data Protection Regulation (GDPR)**. P. Voigt and A. Von dem Bussche. A Practical Guide, 1st Ed., Cham: Springer International Publishing, vol. 10, no. 3152676, pp. 10–5555, 2017. [[book](https://dl.acm.org/doi/10.5555/3152676)]

- **Truebit: A scalable verification solution for blockchains**. J. Teutsch and C. Reitwießner. 2018. [[paper](https://arxiv.org/abs/1908.04756)]

- **Language models are few-shot learners**. T. B. Brown et al., 2020. [[paper](https://arxiv.org/abs/2005.14165)]

### 3. On-training
#### 3.1. Industry
- **Bittensor** [[whitepaper](https://bittensor.org/wp-content/uploads/2024/02/bittensor.org-whitepaper.pdf)] [[docs](https://docs.bittensor.com/)] [[code](https://github.com/opentensor/BitTensor)]
- **Numeraire** [[whitepaper](https://numer.ai/whitepaper.pdf)] [[docs](https://docs.numer.ai/)] [[code](https://github.com/erasureprotocol/NMR)]
- **Commune AI** [[whitepaper](https://ai-secure.github.io/DMLW2022/assets/papers/7.pdf)] [[docs](https://commune-t.pages.dev/docs/next/Introduction)] [[code](https://github.com/commune-ai)]
- **FLock** [[whitepaper](https://www.flock.io/whitepaper)] [[docs](https://docs.flock.io/)] [[code](https://github.com/FLock-io)]

#### 3.2. Academic Work

- **The malicious use of artificial intelligence: Forecasting, prevention, and mitigation**. M. Brundage et al. arXiv preprint arXiv:1802.07228, 2018. [[paper](https://arxiv.org/abs/1802.07228)]

- **Large scale distributed deep networks**. J. Dean et al. In Advances in Neural Information Processing Systems, vol. 25, 2012, pp. 1223–1231. [[paper](https://dl.acm.org/doi/10.5555/2999134.2999271)]

- **Imagenet: A large-scale hierarchical image database**. J. Deng et al. In 2009 IEEE Conference on Computer Vision and Pattern Recognition. IEEE, 2009, pp. 248–255. [[paper](https://ieeexplore.ieee.org/document/5206848)]

- **Health insurance portability and accountability act of 1996**. U.S. Congress. Public Law 104–191, 1996. [[article](https://aspe.hhs.gov/reports/health-insurance-portability-accountability-act-1996)]

- **Language models are few-shot learners**. T. B. Brown et al. In Advances in Neural Information Processing Systems, vol. 33, 2020, pp. 1877–1901. [[paper](https://arxiv.org/abs/2005.14165)]

#### 4. Post-training

##### 4.1. Model Inference

###### 4.1.1. Industry

- **Allora** [[whitepaper](https://whitepaper.assets.allora.network/whitepaper.pdf)] [[docs](https://docs.allora.network/home/explore)] [[code](https://github.com/allora-network)]

- **Sertn** [[whitepaper](https://public.inferencelabs.com/sertn-whitepaper.pdf)] [[docs](https://docs.inferencelabs.com/)] [[code](https://github.com/inference-labs-inc)]

- **ORA** [[whitepaper](https://arxiv.org/abs/2401.17555)] [[docs](https://docs.ora.io/doc)] [[code](https://github.com/ora-io)]

###### 4.1.2. Academic Work

- **Machine Learning**. T. M. Mitchell. McGraw Hill, 1997. [[book](https://www.cs.cmu.edu/~tom/mlbook.html)]

- **Efficient processing of deep neural networks: A tutorial and survey**. V. Sze et al. Proceedings of the IEEE, vol. 105, no. 12, pp. 2295–2329, 2017. [[paper](https://arxiv.org/pdf/1703.09039)]

- **Blockchain for IoT security and privacy: The case study of a smart home**. A. Dorri et al. In 2017 IEEE International Conference on Pervasive Computing and Communications Workshops (PerCom Workshops). IEEE, 2017, pp. 618–623. [[paper](https://ieeexplore.ieee.org/document/7917634)]

##### 4.2. Application

###### 4.2.1. Industry

- **Fetch** [[whitepaper](https://media.abnnewswire.net/media/en/whitepaper/rpt/96506-Fetch_WP.pdf)] [[docs](https://fetch.ai/docs/guides)] [[code](https://github.com/fetchai)]
- **Morpheus** [[whitepaper](https://mor.org/whitepaper)] [[docs](https://github.com/MorpheusAIs/Docs)] [[code](https://github.com/MorpheusAIs/Docs)]
- **Delysium** [[whitepaper](https://delysium.gitbook.io/whitepaper)] 
- **Theoriq** [[whitepaper](https://www.theoriq.ai/litepaper)] [[code](https://github.com/chain-ml/theoriq-agent-sdk)] 

###### 4.2.2. Academic Work

- **Artificial Intelligence: A Modern Approach**. S. Russell and P. Norvig. 3rd ed. Upper Saddle River, NJ: Prentice Hall, 2010. [[book](https://aima.cs.berkeley.edu/)]

- **Multiagent systems: A survey from a machine learning perspective**. P. Stone and M. Veloso. Autonomous Robots, vol. 8, no. 3, pp. 345–383, 2000. [[paper](https://www.cs.cmu.edu/~mmv/papers/MASsurvey.pdf)]

- **Grand challenges in AI: Representation learning, reasoning, and common sense**. O. Vinyals et al. DeepMind Research, 2019. [[blog](https://deepmind.com/blog/article/grand-challenges-ai-representation-learning-reasoning-common-sense)]

##### 4.3. Marketplace

###### 4.3.1. Industry

- **Balance AI** [[docs](https://docs.balanceai.network/)] [[code](https://github.com/balanceainetwork/task-oriented-agents-poc)]
- **SingularityNET** [[whitepaper](https://public.singularitynet.io/whitepaper.pdf)] [[docs](https://dev.singularitynet.io/docs/concepts/)] [[code](https://github.com/singnet/)]
- **Immutable** [[whitepaper](https://uploads-ssl.webflow.com/646557ee455c3e16e4a9bcb3/6499367de527dd82ab7475a3_Immutable%20Whitepaper%20Update%202023%20(3).pdf)] [[docs](https://docs.immutable.com/)] [[code](https://github.com/ImmutableLabs)]
- **Sahara** [[whitepaper](https://saharalabs.ai/learn/litepaper)] [[docs](https://docs.saharalabs.ai/)]
