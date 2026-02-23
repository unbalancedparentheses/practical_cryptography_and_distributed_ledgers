# Practical Cryptography and Distributed Ledgers

- Pablo Deymonnaz
- Diego Kingston
- Federico Carrone

The ZK proving systems landscape has exploded. Circle STARKs (Starkware/Stwo) operate over the Mersenne31 field, enabling dramatically faster proof generation by exploiting the structure of circles over finite fields. Binius (Irreducible) works over binary tower fields, achieving the smallest proofs for binary circuits. Jolt/Lasso (a16z) use lookup arguments to verify RISC-V execution without custom circuits -- this is the "lookup singularity" approach where the prover just commits to a trace and proves lookups into predefined tables. Folding schemes (Nova, HyperNova, SuperNova from Microsoft Research) are the other major paradigm shift: instead of proving a computation all at once, you incrementally fold instances together, enabling IVC (Incremental Verifiable Computation) for long-running computations like blockchain state transitions.

Post-quantum cryptography has moved from research to deployment: NIST finalized FIPS 203 (ML-KEM, lattice-based key encapsulation), FIPS 204 (ML-DSA, lattice-based signatures), and FIPS 205 (SLH-DSA, hash-based signatures). Chrome and Signal already ship post-quantum key exchange. The FHE entries (Zama's fhEVM, Concrete ML) show fully homomorphic encryption becoming practical for specific use cases -- encrypted on-chain computation and private ML inference -- though it remains orders of magnitude slower than plaintext for general computation.

## Table of Contents
- [1. Foundations of Cryptography](#1-foundations-of-cryptography)
- [2. Symmetric encryption](#2-symmetric-encryption)
- [3. Asymmetric encryption](#3-asymmetric-encryption)
- [4. Hash Functions, MAC and Signatures](#4-hash-functions-mac-and-signatures)
- [5. What is Money?](#5-what-is-money)
- [6. Introduction to blockchains and cryptocurrencies](#6-introduction-to-blockchains-and-cryptocurrencies)
- [7. Bitcoin](#7-bitcoin)
- [8. Ethereum](#8-ethereum)
- [9. Wallets, Dapps and DeFi](#9-wallets-dapps-and-defi)
- [10. Oracles, Bridges and Rollups](#10-oracles-bridges-and-rollups)
- [11. EVM](#11-evm)
- [12. Security](#12-security)
- [13. MEV](#13-mev)
- [14. Zcash, SNARKs and Privacy in blockchains](#14-zcash-snarks-and-privacy-in-blockchains)
- [15. Scaling blockchains](#15-scaling-blockchains)
- [16. Tendermint, HotStuff and Narwhal](#16-tendermint-hotstuff-and-narwhal)
- [17. Bitcoin: SegWit, Taproot, Lightning Network and Covenants](#17-bitcoin-segwit-taproot-lightning-network-and-covenants)
- [Books](#books)
- [Courses](#courses)
- [Missing topics](#missing-topics)

# 1. Foundations of Cryptography
- Groups, Rings and Fields
- Finite Fields
- Modular Arithmetic
- Polynomials over a Field
- P versus NP problem
- Computationally Hard Problems: Factorization and the Discrete Logarithm
- Elliptic Curves
- Elliptic Curves Pairings and Field Extensions

## Readings
- [Chapter entitled Cryptography: Sections on Symmetric Crypto Primitives - Anderson Security Engineering](https://www.cl.cam.ac.uk/~rja14/Papers/SEv2-c05.pdf) - Overview of symmetric primitives including block ciphers, stream ciphers, and their real-world failure modes
- [A (Relatively Easy To Understand) Primer on Elliptic Curve Cryptography - Nick Sullivan](https://blog.cloudflare.com/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/) - Gentle introduction to why elliptic curves are used in crypto and how ECDH and ECDSA work
- [Exploring Elliptic Curve Pairings - Vitalik Buterin](https://vitalik.ca/general/2017/01/14/exploring_ecp.html) - Explains bilinear pairings on elliptic curves, the mathematical foundation behind BLS signatures and zk-SNARKs
- [Pairing](https://www.zeroknowledgeblog.com/index.php/the-pinocchio-protocol/pairing) - Short walkthrough of how pairing-based cryptography enables the Pinocchio zk-SNARK protocol
- [Ben Lynn's notes on cryptography, abstract algebra and number theory](https://crypto.stanford.edu/pbc/notes/) - Concise Stanford lecture notes covering groups, fields, pairings, and their applications in cryptographic protocols
- [Reed Solomon](https://mazzo.li/posts/reed-solomon.html) - Hands-on explanation of Reed-Solomon error-correcting codes with code examples
- [Reed-Solomon codes for coders](https://en.wikiversity.org/wiki/Reed%E2%80%93Solomon_codes_for_coders) - Step-by-step tutorial on implementing Reed-Solomon encoding and decoding from scratch
- [Moonmath](https://leastauthority.com/community-matters/moonmath-manual/) - Comprehensive manual covering the mathematics behind zk-SNARKs, from finite fields through polynomial commitments

## Exercises
- [Programming Bitcoin: Learn How to Program Bitcoin from Scratch - Jimmy Song](https://github.com/jimmysong/programmingbitcoin) - Hands-on exercises building a Bitcoin library in Python, covering elliptic curves, transactions, and script

# 2 Symmetric encryption
- Stream ciphers and block ciphers
- AES
- AES operation modes
- ChaCha20
- Security definitions.
- Attacks on block and stream ciphers.

# 3. Asymmetric encryption
- Diffie-Hellman Key Exchange
- ECDH
- ElGamal
- RSA
- PKCS

## Readings
- [Twenty Years of Attacks on the RSA Cryptosystem - Dan Boneh](https://crypto.stanford.edu/~dabo/papers/RSA-survey.pdf) - Survey of two decades of RSA attacks including timing attacks, padding oracles, and small-exponent vulnerabilities

# 4. Hash Functions, MAC and Signatures
- Properties of cryptographic hash functions
- Merkle-Damgard construction
- MD5
- SHA1
- Sponge constructions
- Keccak - SHA3
- Message Authentication Codes
- ECDSA signature
- Schnor signature
- BLS signature

## Readings
- [What is a Cryptographic Hash Function? - Alin Tomescu](https://decentralizedthoughts.github.io/2020-08-28-what-is-a-cryptographic-hash-function/) - Explains collision resistance, preimage resistance, and why hash functions are fundamental to blockchains
- [What is the BLS signature scheme? - David Wong](https://www.cryptologie.net/article/472/what-is-the-bls-signature-scheme/) - Introduction to BLS signatures and why their aggregation property makes them ideal for consensus protocols
- [BLS Signatures - Remco Bloemen](https://xn--2-umb.com/22/bls-signatures/) - Technical deep dive into BLS signature math, aggregation, and their use in Ethereum 2.0 validator attestations

# 5. What is Money?
- [A Brief History of Money](https://nakamoto.com/a-brief-history-of-money/) - Traces the evolution of money from barter through gold, fiat, and digital currencies
- [Shelling Out: The Origins of Money - Nick Szabo](https://nakamotoinstitute.org/shelling-out/) - Argues that collectibles and proto-money emerged from evolutionary pressures to solve cooperation problems
- [What is Money anyway - Lyn Alden](https://www.lynalden.com/what-is-money/) - Comprehensive analysis of money as a ledger technology, comparing hard money, credit money, and digital alternatives
- [Money in the modern economy: an introduction](https://www.bankofengland.co.uk/-/media/boe/files/quarterly-bulletin/2014/money-in-the-modern-economy-an-introduction.pdf?la=en&hash=E43CDFDBB5A23D672F4D09B13DF135E6715EEDAC) - Bank of England primer on what money is and the different types of money in a modern economy
- [Money creation in the modern economy](https://www.bankofengland.co.uk/-/media/boe/files/quarterly-bulletin/2014/money-creation-in-the-modern-economy.pdf?la=en&hash=9A8788FD44A62D8BB927123544205CE476E01654) - Bank of England explains how commercial banks create money through lending, debunking the money multiplier myth
- [The Cypherpunks](https://nakamoto.com/the-cypherpunks) - History of the cypherpunk movement and how their ideas about privacy and digital cash led to Bitcoin

# 6. Introduction to blockchains and cryptocurrencies
- What is a blockchain?
- State Machines
- Consensus
- Merkle Trees

## Readings
- [Why cryptocurrencies are interesting?](https://mirror.xyz/0xaFaBa30769374EA0F971300dE79c62Bf94B464d5/us0MyyUNYwSXazM0YCrGscbRWr18s0aIIZqyHBbTWfM) - Motivates why permissionless digital money and programmable contracts matter beyond speculation
- [Cancelled Nickel Trades on the LME](https://youtu.be/tHXF5LyLI4M) - Video showing how the London Metal Exchange reversed trades to bail out insiders, illustrating why immutable ledgers matter
- [What is a Blockchain - Ittai Abraham](https://decentralizedthoughts.github.io/2022-09-05-what-is-a-blockchain/) - Formal definition of a blockchain as a replicated state machine with safety and liveness properties
- [How does everything tie together?](https://mirror.xyz/0xaFaBa30769374EA0F971300dE79c62Bf94B464d5/nsEwS5WZjLeydpX2x9XybTpu7dA5LpLNyayj93HnovA) - Connects the building blocks of blockchains: cryptography, consensus, state machines, and incentives
- [Blockchains as Cryptographic Data Structures - Pramod Viswanath](https://courses.grainger.illinois.edu/ece598pv/sp2021/lectureslides2021/ECE_598_PV_course_notes2.pdf) - Lecture notes formalizing blockchains as authenticated data structures using hash chains and Merkle trees
- [Hash functions](https://nakamoto.com/hash-functions/) - Explains how cryptographic hash functions provide data integrity and proof-of-work in blockchains
- [Merkle Tree](https://nakamoto.com/merkle-trees/) - Introduces Merkle trees and how they enable efficient verification of data in blocks
- [What is a Merkle Tree](https://decentralizedthoughts.github.io/2020-12-22-what-is-a-merkle-tree/) - Formal treatment of Merkle trees covering proofs of inclusion, exclusion, and their role in light clients
- [What is Consensus? - Kartik Nayak, Ittai Abraham](https://decentralizedthoughts.github.io/2019-06-27-defining-consensus/) - Rigorous definition of consensus covering agreement, validity, and termination properties
- [Flavours of State Machine Replication - Ittai Abraham](https://decentralizedthoughts.github.io/2019-10-25-flavours-of-state-machine-replication/) - Taxonomy of SMR variants: crash vs Byzantine failures, synchronous vs asynchronous, and their trade-offs
- [Consensus for State Machine Replication - Kartik Nayak, Ittai Abraham](https://decentralizedthoughts.github.io/2019-10-15-consensus-for-state-machine-replication/) - Shows how single-shot consensus is extended to replicate a full state machine across nodes
- [From Single-Shot Agreement to State Machine Replication](https://decentralizedthoughts.github.io/2022-11-19-from-single-shot-to-smr/) - Walks through the reduction from state machine replication to repeated instances of consensus
- [On settlement finality - Ethereum Blog](https://blog.ethereum.org/2016/05/09/on-settlement-finality/) - Distinguishes probabilistic finality (Bitcoin) from economic finality (PoS) and their practical implications
- [Finality in Blockchain Consensus - Mechanism Labs](https://medium.com/mechanism-labs/finality-in-blockchain-consensus-d1f83c120a9a#:~:text=In%20the%20blockchain%20setting%2C%20finality,be%20arbitrarily%20changed%20or%20reversed) - Compares different finality models across blockchain protocols and their security guarantees
- [The mystery behind block time](https://medium.facilelogin.com/the-mystery-behind-block-time-63351e35603a) - Explains how block time is determined by difficulty adjustment and its relationship to security and throughput
- [What everyone gets wrong about 51% attacks - Dankrad Feist](https://dankradfeist.de/ethereum/2021/05/20/what-everyone-gets-wrong-about-51percent-attacks.html) - Clarifies that 51% attacks cannot steal funds or change rules, only double-spend and censor transactions
- [Blockchain papers - decrypto-org](https://github.com/decrypto-org/blockchain-papers) - Curated collection of academic blockchain research papers organized by topic
- [An Empirical Analysis of Chain Reorganizations and Double-Spend Attacks on Proof-of-Work Cryptocurrencies - MIT](https://dspace.mit.edu/handle/1721.1/127476) - Measures how often chain reorgs actually happen in practice and quantifies real-world double-spend risk

## Videos
- [E48: The role of decentralization, China/US break down & more with Bestie Guestie Balaji Srinivasan](https://youtu.be/B2iNXMiGEms) - Discussion on why decentralization matters geopolitically and how crypto fits into US-China dynamics

# 7. Bitcoin
- Two general's Problem
- What Is the Byzantine Generals Problem?

## Readings
- [The Byzantine Generals Problem](https://dl.acm.org/doi/10.1145/357172.357176) - The original Lamport, Shostak, and Pease paper proving consensus requires more than two-thirds honest participants
- [Blockchain Basics & Consensus - MIT 15.S12 Blockchain and Money - Gary Gensler](https://www.youtube.com/watch?v=w7HDA8gUbpQ&list=PLUl4u3cNGP63UUkfL0onkxF6MYgVa04Fn) - MIT lecture series covering blockchain fundamentals, proof-of-work, and how Bitcoin achieves consensus
- [Paxos(etcd) vs. Nakamoto(Bitcoin): consensus](https://gyuho.dev/paxos-etcd-vs-nakamoto-bitcoin-consensus.html) - Side-by-side comparison of classical BFT consensus (Paxos) and Nakamoto consensus trade-offs
- [Nakamoto's Longest-Chain Wins Protocol](https://decentralizedthoughts.github.io/2021-10-15-Nakamoto-Consensus/) - Formal analysis of why following the longest chain achieves consensus under honest majority assumptions
- [Learning-Bitcoin-from-the-Command-Line](https://github.com/BlockchainCommons/Learning-Bitcoin-from-the-Command-Line) - Hands-on tutorial for interacting with Bitcoin Core via CLI, covering wallets, transactions, and scripting
- [Bitcoin: A Peer-to-Peer Electronic Cash System](https://bitcoin.org/bitcoin.pdf) - The original Satoshi Nakamoto whitepaper describing proof-of-work, the UTXO model, and the incentive structure
- [But how does bitcoin actually work?](https://youtu.be/bBC-nXj3Ng4) - Visual explanation by 3Blue1Brown of how digital signatures, hashing, and proof-of-work combine to form Bitcoin
- [Cryptoeconomics In 30 Minutes by Vitalik Buterin](https://youtu.be/GQR1xjQn5Pg) - Vitalik explains how economic incentives and cryptography work together to secure decentralized protocols
- [The differences between a hard fork, a soft fork, and a chain split](https://medium.com/@lightcoin/the-differences-between-a-hard-fork-a-soft-fork-and-a-chain-split-and-what-they-mean-for-the-769273f358c9) - Clarifies how protocol upgrades work and when they cause chain splits versus backward-compatible changes

# 8. Ethereum
- Solidity
- ERC20
- ERC721
- ERC-1155
- Merkle Patricia Trie Tree

## Readings
- [DEVCON1: Understanding the Ethereum Blockchain Protocol - Vitalik Buterin](https://youtu.be/gjwr-7PgpN8) - Vitalik walks through Ethereum's architecture including accounts, gas, the EVM, and state transitions
- [Ethereum Whitepaper](https://ethereum.org/en/whitepaper/) - The founding document describing Ethereum as a general-purpose programmable blockchain with smart contracts
- [Learn Solidity in Y Minutes](https://learnxinyminutes.com/docs/solidity/) - Quick-reference syntax tour of Solidity covering types, functions, modifiers, and common patterns
- [Getting Started with Solidity](https://cryptomarketpool.com/getting-started-with-solidity/) - Beginner tutorial covering Solidity basics, contract structure, and deploying your first smart contract
- [OpenZeppelin](https://docs.openzeppelin.com/contracts/4.x/) - Battle-tested library of reusable smart contracts for ERC20, ERC721, access control, and upgradeable proxies
- [Go Ethereum](https://geth.ethereum.org/docs) - Official documentation for Geth, the most widely used Ethereum execution client written in Go
- [Trie, Merkle, Patricia: A Blockchain Story](https://kronosapiens.github.io/blog/2018/07/04/patricia-trees.html) - Explains how Ethereum combines tries, Merkle trees, and Patricia trees to store world state efficiently
- [Ethereum development made easy with Foundry](https://www.notamonadtutorial.com/ethereum-development-made-easy-with-foundry/) - Getting started guide for Foundry, a fast Rust-based toolchain for compiling, testing, and deploying Solidity
- [scaffold-eth: forkable Ethereum dev stack focused on fast product iterations](https://github.com/scaffold-eth/scaffold-eth) - Full-stack Ethereum starter kit with React frontend, Hardhat backend, and one-command local deployment
- [Scaffold-Eth Challenges](https://github.com/scaffold-eth/scaffold-eth-challenges) - Progressive coding challenges to learn Ethereum development by building real DeFi and NFT projects
- [solmate - Modern, opinionated, and gas optimized building blocks - Rari Capital](https://github.com/Rari-Capital/solmate) - Gas-optimized Solidity library providing minimal, audited implementations of common token and auth patterns
- [CNBC: People are paying millions of dollars for digital pictures of rocks (NFTs)](https://www.cnbc.com/2021/08/23/people-are-paying-millions-of-dollars-for-digital-pictures-of-rocks.html) - News piece illustrating the NFT mania of 2021 and how ERC-721 tokens created a digital collectibles market

# 9. Wallets, Dapps and DeFi
- DEX: Uniswap
- Lending: Aave
- Stablecoin: Maker/DAI
- dYdX
- [Metamask and other wallets](https://metamask.io/) - Browser extension wallet for interacting with Ethereum dApps, managing keys, and signing transactions
- DEMO: Uniswap, Curve, OpenSea NFTs, Maker/Oasis, Multisig
- [lil web3: Small, focused, utility-based smart contracts](https://github.com/m1guelpf/lil-web3) - Minimalist implementations of common web3 protocols like ENS, Uniswap, and NFT marketplaces for learning
- [Programming DeFi: Uniswap V2. Part 1](https://jeiwan.net/posts/programming-defi-uniswapv2-1/) - Build Uniswap V2 from scratch: core pair contract, constant product formula, and liquidity provision
- [The Problems with DeFi & Crypto](https://www.lynalden.com/defi-problems/) - Critical analysis of DeFi risks including smart contract bugs, oracle manipulation, and systemic leverage
- [Programming DeFi: Uniswap V2. Part 1](https://ethereum.org/en/developers/tutorials/uniswap-v2-annotated-code/) - Line-by-line annotated walkthrough of the official Uniswap V2 Solidity source code
- [Programming DeFi: Uniswap V2. Part 2](https://jeiwan.net/posts/programming-defi-uniswapv2-2/) - Implements the Uniswap V2 router, multi-hop swaps, and slippage protection
- [Programming DeFi: Uniswap V2. Part 3](https://jeiwan.net/posts/programming-defi-uniswapv2-3/) - Adds flash swaps, price oracles via TWAP, and protocol fee mechanisms to the Uniswap V2 implementation
- [Uniswap V3 Development Book](https://uniswapv3book.com/) - Full book on building Uniswap V3 with concentrated liquidity, tick-based accounting, and multiple fee tiers
- [Hayden Adams Explains Uniswap and the Rise of DeFi](https://open.spotify.com/episode/3TT6aFeMWnFPZTlfy5fxvv?si=KCw3uWvJQAaeBCZoH1RwNw&dl_branch=1) - Uniswap creator tells the origin story and explains how automated market makers replaced order books
- [What's the simplest possible decentralized stablecoin? - Jacob Eliosoff](https://jacob-eliosoff.medium.com/whats-the-simplest-possible-decentralized-stablecoin-4a25262cf5e8) - Thought experiment exploring the minimal mechanism needed to peg a token to a dollar without centralization
- [Awesome Foundations of DeFi - Mikerah](https://github.com/Mikerah/awesome-foundations-of-DeFi) - Curated list of academic papers on AMMs, lending protocols, liquidations, and other DeFi primitives

# 10. Oracles, Bridges and Rollups
- Oracles
- Bridges
- [An Incomplete Guide to Rollups](https://vitalik.ca/general/2021/01/05/rollup.html) - Vitalik explains how optimistic and ZK rollups scale Ethereum by executing off-chain while posting data on-chain

# 11. EVM
- [EVM codes](https://www.evm.codes/?fork=merge) - Interactive reference for every EVM opcode with gas costs, stack inputs/outputs, and execution behavior
- [EVM: From Solidity to byte code, memory and storage](https://youtu.be/RxL_1AfV7N4) - Video walkthrough of how Solidity compiles to bytecode and how the EVM manages memory, storage, and the stack
- [Ethereum Virtual Machine](https://www.youtube.com/watch?v=BsDq2mzC5tk) - Visual introduction to EVM architecture including the call stack, gas metering, and contract execution flow
- [EVM Deep Dives: The Path to Shadowy Super Coder - Part 1](https://noxx.substack.com/p/evm-deep-dives-the-path-to-shadowy) - Deep dive into EVM internals: how function selectors, memory layout, and storage slots work at the bytecode level
- [Contract ABI Specification - Solidity Docs](https://docs.soliditylang.org/en/latest/abi-spec.html) - Official spec for how Solidity encodes function calls and return values for inter-contract communication

# 12. Security
- [Capture the Ether](https://capturetheether.com/challenges/) - CTF-style challenges teaching Ethereum security by exploiting vulnerable smart contracts
- [Ethernaut](https://ethernaut.openzeppelin.com/) - Progressive wargame where you hack intentionally vulnerable Solidity contracts to learn common attack patterns
- [Damn Vulnerable DeFi](https://www.damnvulnerabledefi.xyz/) - Advanced CTF focused on DeFi-specific attacks including flash loans, price manipulation, and governance exploits
- [Solidity Security: Comprehensive list of known attack vectors and common anti-patterns](https://blog.sigmaprime.io/solidity-security.html) - Reference catalog of Solidity vulnerabilities including reentrancy, integer overflow, and delegatecall pitfalls
- [MISO War Room - Mudit Gupta](https://mudit.blog/miso-war-room/) - Post-mortem of the SushiSwap MISO exploit detailing how the team discovered, analyzed, and mitigated the attack
- [Critical privacy vulnerability getting exposed by MetaMask](https://medium.com/@alxlpsc/critical-privacy-vulnerability-getting-exposed-by-metamask-693c63c2ce94) - Disclosure of how MetaMask leaked user IP addresses to Infura, compromising wallet privacy

## Tools
- [echidna - Ethereum smart contract fuzzer](https://github.com/crytic/echidna) - Property-based fuzzer that tests Solidity contracts by generating random transactions to find invariant violations
- [manticore - Symbolic execution tool](https://github.com/trailofbits/manticore) - Explores all reachable program paths in EVM bytecode to find bugs like reentrancy and integer overflows
- [mythril - Security analysis tool for EVM bytecode](https://github.com/ConsenSys/mythril) - Automated vulnerability scanner using symbolic execution and taint analysis to detect common Solidity flaws
- [surya - A Solidity inspection tool - ConsenSys](https://github.com/ConsenSys/surya) - Generates call graphs, inheritance trees, and function visibility reports to audit Solidity contract structure

# 13. MEV
- [MEV101 - Introduction to Maximal Extractable Value](./MEV101.pdf) - Introductory slide deck explaining what MEV is, how searchers extract it, and why it matters for users
- [MEV](https://research.paradigm.xyz/MEV) - Paradigm research overview of MEV taxonomy including frontrunning, backrunning, sandwiching, and liquidations
- [How To Get Front-Run on Ethereum mainnet](https://www.youtube.com/watch?v=UZ-NNd6yjFM) - Live demo showing how a mempool transaction gets detected and front-run by a bot in real time
- [Video: Honeypots in Ethereum And How To Avoid Them With Tenderly.co Transaction Simulation](https://youtu.be/DDn5mksOUCc) - Shows how MEV honeypot contracts lure bots and how to use transaction simulation to detect them
- [The Anatomy of an Inspector - Flashbots](https://writings.flashbots.net/writings/the-anatomy-of-an-inspector/) - Explains how Flashbots built mev-inspect to classify and measure MEV extraction across Ethereum blocks
- [The Hidden World of Ethereum Snipers - Samneet Chepal](https://www.samchepal.com/the-hidden-world-of/) - Investigation of token sniping bots that buy new tokens at launch by monitoring contract deployments

# 14. Zcash, SNARKs and Privacy in blockchains
- [Zcash](https://electriccoin.co/blog/category/technical/) - Technical blog posts from the Zcash team explaining shielded transactions, the Sapling upgrade, and zk-SNARK circuits
- [Aztec Network](https://aztec.network/) - Privacy-first L2 rollup on Ethereum using zk-SNARKs for confidential transactions and private smart contracts
- [zksnarks](https://zkhack.dev/whiteboard/module-one/) - ZK Hack whiteboard session covering zk-SNARK intuition, the trusted setup, and how proofs are generated and verified
- [Arithmetization I - StarkWare STARK Math](https://medium.com/starkware/arithmetization-i-15c046390862) - Explains how computational claims are converted into polynomial equations, the first step in building STARKs
- [Arithmetization II - StarkWare STARK Math](https://medium.com/starkware/arithmetization-ii-403c3b3f4355) - Continues with constraint composition and how the low-degree testing step verifies polynomial identities
- [Announcing Dark Forest - a zkSNARK game](https://blog.zkga.me/announcing-darkforest) - Introduces a fully on-chain strategy game using zk-SNARKs so players can prove moves without revealing positions
- [Umbra: How does Umbra compare to Tornado Cash and Aztec?](https://app.umbra.cash/faq#how-does-umbra-compare-to-tornado-cash-and-aztec) - Comparison of stealth address privacy (Umbra) versus mixing (Tornado Cash) and rollup privacy (Aztec)
- [STARKs, Part I: Proofs with Polynomials - Vitalik Buterin](https://vitalik.ca/general/2017/11/09/starks_part_1.html) - Builds intuition for STARKs by showing how polynomial evaluations can prove computational statements without trusted setup
- [An approximate introduction to how zk-SNARKs are possible - Vitalik Buterin](https://vitalik.eth.limo/general/2021/01/26/snarks.html) - Accessible walkthrough of zk-SNARK construction from polynomial commitments through quadratic arithmetic programs

# 15. Scaling blockchains
- Data Availability
- Optimistic versus Zero Knoweledge Rollups
- Circom, Cairo, Noir

## Readings
- [Data, Consensus, Execution: Three Scalability Bottlenecks for State Machine Replication - Ittai Abraham](https://decentralizedthoughts.github.io/2019-12-06-dce-the-three-scalability-bottlenecks-of-state-machine-replication) - Framework decomposing blockchain scalability into three independent bottlenecks that must each be solved
- [Understanding Blockchain Latency and Throughput - Lefteris Kokoris-Kogias](https://www.paradigm.xyz/2022/07/consensus-throughput) - Rigorous analysis of what actually limits blockchain throughput and why naive metrics are misleading
- [(Almost) Everything you need to know about Optimistic Rollup - Georgios Konstantopoulos](https://www.paradigm.xyz/2021/01/almost-everything-you-need-to-know-about-optimistic-rollup) - Comprehensive explainer of optimistic rollup mechanics including fraud proofs, challenge periods, and data posting
- [Why rollups + data shards are the only sustainable solution for high scalability - Polynya](https://polynya.medium.com/why-rollups-data-shards-are-the-only-sustainable-solution-for-high-scalability-c9aabd6fbb48) - Argues that L1 execution scaling hits decentralization limits and only rollups with data availability solve the trilemma
- [Volitions: best of all worlds - Polynya](https://polynya.medium.com/volitions-best-of-all-worlds-cfd313aec9a8) - Introduces volitions as hybrid rollups where users choose between on-chain and off-chain data availability per transaction
- [Volition and the Emerging Data Availability Spectrum - StarkWare](https://medium.com/starkware/volition-and-the-emerging-data-availability-spectrum-87e8bfa09bb) - StarkWare's design for letting applications pick their data availability trade-off between cost and security

# 16. Tendermint, HotStuff and Narwhal
- [What is the difference between PBFT, Tendermint, SBFT and HotStuff? - Ittai Abraham](https://decentralizedthoughts.github.io/2019-06-23-what-is-the-difference-between/) - Compares four BFT protocols on message complexity, view-change overhead, and leader rotation strategies
- [DAG Meets BFT - The Next Generation of BFT Consensus - Ittai Abraham](https://decentralizedthoughts.github.io/2022-06-28-DAG-meets-BFT/) - Explains how DAG-based mempool protocols like Narwhal decouple data dissemination from consensus ordering
- [MetaAnalysis of Alternative Consensus Protocols - Mechanism Labs](https://github.com/Mechanism-Labs/MetaAnalysis-of-Alternative-Consensus-Protocols) - Structured comparison of consensus protocols including Avalanche, Solana, Algorand, and others
- [FLP and CAP aren't the same thing](https://www.the-paper-trail.org/post/2012-03-25-flp-and-cap-arent-the-same-thing/) - Clarifies the distinct impossibility results of FLP (consensus in async systems) versus CAP (consistency vs availability)
- [FLP and CAP - Dinhtta](https://dinhtta.github.io/flpcap/) - Concise explanation of the FLP impossibility theorem and the CAP theorem with examples of how systems navigate them

# 17. Bitcoin: SegWit, Taproot, Lightning Network and Covenants
- [Segregated Witness](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki) - BIP-141 specification that separates witness data from transactions, fixing malleability and increasing block capacity
- [Taproot: SegWit version 1 spending rules](https://github.com/bitcoin/bips/blob/master/bip-0341.mediawiki) - BIP-341 specification enabling Schnorr signatures and MAST for cheaper, more private complex spending conditions
- [Covenants: CHECKTEMPLATEVERIFY (BIP-119)](https://github.com/bitcoin/bips/blob/master/bip-0119.mediawiki) - BIP-119 proposal for restricting how coins can be spent, enabling vaults, congestion control, and payment pools
- [A Look at the Lightning Network - Lyn Alden](https://www.lynalden.com/lightning-network/) - Balanced assessment of Lightning Network's design, adoption, trade-offs, and viability for scaling Bitcoin payments
- [The Bitcoin Lightning Network: Scalable Off-Chain Instant Payments](https://berkeley-defi.github.io/assets/material/lightning-network-paper.pdf) - The original paper describing bidirectional payment channels and how they compose into a routed payment network

# Books
- [Bitcoin and Cryptocurrency Technologies: A Comprehensive Introduction - Arvind Narayanan, Joseph Bonneau, Edward Felten, Andrew Miller, and Steven Goldfeder](https://press.princeton.edu/books/hardcover/9780691171692/bitcoin-and-cryptocurrency-technologies) - Textbook covering Bitcoin mechanics, mining, anonymity, and altcoins; suitable for students and developers new to crypto
- [Security Engineering - Ross Anderson](https://www.cl.cam.ac.uk/~rja14/book.html) - Encyclopedic reference on building secure systems, covering cryptography, protocols, and real-world failure case studies

## Blockchain
- [Foundations of Distributed: Consensus and Blockchains - Elaine Shi](http://elaineshi.com/docs/blockchain-book.pdf) - Graduate-level textbook formalizing consensus, Byzantine fault tolerance, and blockchain protocols with mathematical rigor

## Cryptography
- [Handbook of Applied Cryptography - Menezes, van Oorschot and Vanstone](https://cacr.uwaterloo.ca/hac/) - Comprehensive reference covering algorithms and protocols for symmetric crypto, public-key crypto, and key management
- [Crypto 101 - lvh](https://www.crypto101.io/) - Free introductory cryptography book aimed at programmers who want practical understanding without heavy math

## Abstract Algebra and Number Theory
- [An Introduction to Mathematical Cryptography - Jeffrey Hoffstein, Jill Pipher, Joseph H. Silverman](https://link.springer.com/book/10.1007/978-1-4939-1711-2) - Undergraduate textbook connecting number theory and algebra to RSA, Diffie-Hellman, lattices, and elliptic curves
- [A Course in Number Theory and Cryptography - Neal Koblitz](https://link.springer.com/book/10.1007/978-1-4419-8592-7) - Classic graduate text covering number theory foundations with direct applications to RSA and elliptic curve cryptography
- [Algebra for Applications - Arkadii Slinko](https://link.springer.com/book/10.1007/978-3-030-44074-9) - Introduces groups, rings, and fields through cryptographic and coding theory applications rather than pure abstraction
- [A Computational Introduction to Number Theory and Algebra - Victor Shoup](https://shoup.net/ntb/) - Free textbook emphasizing algorithms for number theory and algebra, ideal for those who want to implement cryptographic primitives
- [Elliptic Curves Number Theory and Cryptography - Lawrence C. Washington](https://www.routledge.com/Elliptic-Curves-Number-Theory-and-Cryptography-Second-Edition/Washington/p/book/9781420071467) - Thorough treatment of elliptic curve math and its cryptographic applications, from basics through pairings
- [The Prime Number Conspiracy - Thomas Lin](https://mitpress.mit.edu/9780262536356/the-prime-number-conspiracy/) - Collection of accessible essays from Quanta Magazine exploring deep patterns in prime numbers and modern number theory

# Courses
- [Practical Cryptographic Systems - Matthew Green](https://github.com/matthewdgreen/practicalcrypto/wiki/Spring-2020-Syllabus) - Johns Hopkins course on real-world cryptography covering TLS, secure messaging, cryptocurrencies, and common implementation mistakes
- [Cryptocurrency Class 2022 - Patrick McCorry](https://cryptocurrencyclass.github.io/) - University course covering Bitcoin, Ethereum, payment channels, and layer-2 scaling with practical assignments
- [Principles of Blockchains - Pramod Viswanath](https://courses.grainger.illinois.edu/ece598pv/sp2021/) - Illinois ECE course formalizing blockchain scalability, consensus protocols, and the data-consensus-execution framework
- [Blockchain And Money - Gary Gensler](https://ocw.mit.edu/courses/15-s12-blockchain-and-money-fall-2018/video_galleries/video-lectures/) - MIT Sloan course examining blockchain through the lens of finance, regulation, and use cases beyond cryptocurrency
- [Decentralized Finance MOOC - Dan Boneh, Arthur Gervais, Andrew Miller, Christine Parlour and	Dawn Song](https://defi-learning.org/f22) - Multi-university course covering DeFi mechanics, AMMs, lending, stablecoins, and protocol security
- [Stanford CS 251 Blockchain Technologies - Dan Boneh](https://cs251.stanford.edu/syllabus.html) - Stanford course covering consensus, smart contracts, DeFi, and privacy from a computer science perspective
- [Stanford EE374 Blockchain Foundations - David Tse, Dionysis Zindros](https://web.stanford.edu/class/ee374/) - Stanford course focusing on the theoretical foundations of consensus protocols, longest-chain analysis, and PoS security
- [ECE595 Foundations of Blockchain Systems - Sreeram Kannan](https://ece595uwseattle.github.io/schedule) - UW course on blockchain systems theory covering consensus, sharding, data availability, and restaking
- [CS598CAL Consensus Algorithms - Ling Ren](https://sites.google.com/view/cs598cal?pli=1) - Illinois graduate seminar on consensus algorithms covering Paxos, PBFT, HotStuff, and DAG-based protocols
- [Dan Boneh's Online Cryptography Course - Stanford](https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/) - Stanford's free online course covering symmetric encryption, public-key crypto, and authenticated encryption from first principles

---
# Missing topics
- [ ] Light Clients
- [ ] UTXO vs Account model
- [ ] The Blockchain Trilemma
- [ ] PoS vs PoW
- [ ] Soft Forks vs Hard Forks
- [ ] Onchain vs offchain computation
- [ ] Chinese remainder theorem
- [ ] One Time Pad
- [ ] MAC
- [ ] Account Abstraction (argent x)
- [ ] Finality
- [ ] muun, non custodial wallets

# Not yet reviewed

> These resources were recently found and have not been reviewed yet.

### ZK Proofs: New Proving Systems
- [Binius: Succinct Arguments over Towers of Binary Fields - Diamond & Posen](https://eprint.iacr.org/2023/1784.pdf) - Proofs over binary fields, dramatically cheaper for hash-heavy computations
- [Jolt: SNARKs for Virtual Machines via Lookups (Eurocrypt 2024)](https://eprint.iacr.org/2023/1217) - RISC-V zkVM built almost entirely from lookup arguments, ~10x speedup
- [Lasso: Lookup Arguments (Eurocrypt 2024)](https://people.cs.georgetown.edu/jthaler/Lasso-paper.pdf) - Prover cost scales only with number of lookups, not table size
- [LogUp: Logarithmic Derivatives for Lookups - Haböck (Polygon)](https://eprint.iacr.org/2022/1530) - Standard lookup technique inside Plonky3 and production STARKs

### ZK Proofs: Folding Schemes
- [Nova: Recursive Zero-Knowledge Arguments from Folding Schemes (CRYPTO 2022)](https://eprint.iacr.org/2021/370) - Lightweight alternative to SNARKs for incrementally verifiable computation
- [HyperNova: Recursive Arguments for Customizable Constraint Systems (CRYPTO 2024)](https://eprint.iacr.org/2023/573) - Generalizes Nova to CCS (subsumes R1CS, Plonkish, AIR)
- [SuperNova: Proving Universal Machine Executions without Universal Circuits](https://eprint.iacr.org/2022/1758) - Non-uniform IVC with different circuits per step

### MEV (New)
- [The Future of MEV is SUAVE - Flashbots](https://writings.flashbots.net/the-future-of-mev-is-suave) - Cross-chain MEV network to prevent builder centralization
- [MEV-Share: Programmably Private Orderflow - Flashbots](https://collective.flashbots.net/t/mev-share-programmably-private-orderflow-to-share-mev-with-users/1264) - Users control what searchers see, MEV returned to originators
- [Who Wins Ethereum Block Building Auctions and Why?](https://arxiv.org/pdf/2407.13931) - ~3 builders control 80% of blocks via private order flow feedback loops
- [Based Rollups: Superpowers from L1 Sequencing - Justin Drake](https://ethresear.ch/t/based-rollups-superpowers-from-l1-sequencing/15016) - L1 validators as rollup sequencers

### Scaling & Data Availability
- [EIP-4844: Proto-Danksharding](https://eips.ethereum.org/EIPS/eip-4844) - Blob transactions and KZG commitments, reduced rollup costs 10-100x (Dencun, March 2024)
- [EigenLayer Whitepaper - Sreeram Kannan et al.](https://docs.eigenlayer.xyz/assets/files/EigenLayer_WhitePaper-88c47923ca0319870c611decd6e562ad.pdf) - Restaking to extend ETH security to new protocols including EigenDA

### Consensus (New)
- [Narwhal and Tusk: DAG-based Mempool and BFT Consensus](https://arxiv.org/abs/2105.11827) - 130,000+ tx/sec, foundation for Sui, Aptos, Linera
- [Mysticeti: Low-Latency DAG Consensus (NDSS 2025)](https://arxiv.org/pdf/2310.14821) - First DAG consensus to commit in 3 message delays, <400ms on Sui
- [Shoal++: High Throughput DAG BFT Can Be Fast! (2024)](https://arxiv.org/abs/2405.20488) - Average commit latency of 4.5 message exchanges

### FHE
- [fhEVM: Confidential EVM Smart Contracts Using FHE - Zama](https://github.com/zama-ai/fhevm) - First framework for Solidity contracts operating over encrypted state
- [Concrete ML: Privacy-Preserving ML with FHE - Zama](https://github.com/zama-ai/awesome-zama) - Standard ML models on encrypted data via TFHE

### ZK Proving Systems (New)
- [Circle STARKs - Haboeck, Levit, Papini (2024)](https://eprint.iacr.org/2024/278) - STARKs over Mersenne prime p = 2^31 - 1, achieving ~1.4x speedup over BabyBear-based STARKs
- [Stwo Prover - StarkWare (2024)](https://starkware.co/blog/stwo-prover-the-next-gen-of-stark-scaling-is-here/) - Next-gen open-source STARK prover implementing Circle STARKs; 940x faster than Stone, live on Starknet
- [Polygon Plonky3 (2024)](https://polygon.technology/plonky3) - Modular ZK proving toolkit for custom zkVMs/zkEVMs; 5-10x faster than Plonky2, adopted by SP1 and Valida
- [SP1 Hypercube - Succinct Labs (2025)](https://blog.succinct.xyz/sp1-hypercube-is-now-live-on-mainnet/) - Multilinear-polynomial zkVM proving Ethereum blocks in under 12 seconds on 16 GPUs; first real-time L1 prover
- [Verifying Jolt zkVM Lookup Semantics - Kwan, Dao, Thaler (2024)](https://eprint.iacr.org/2024/1841) - Formal verification of all Jolt RV32I instruction lookups using ACL2 theorem prover

### Ethereum: Pectra & Account Abstraction (New)
- [EIP-7702: Set Code for EOAs - Buterin et al. (2024)](https://eips.ethereum.org/EIPS/eip-7702) - EOAs temporarily delegate to smart contract code; enables batching, gas sponsorship; shipped in Pectra (May 2025)

### MEV / PBS (New)
- [Analysis of Order Flow Auction under PBS - Ma, Tang, Yao (2025)](https://arxiv.org/abs/2502.12026) - Game-theoretic model of OFA + block-building showing builder centralization dynamics
- [Quantifying Price Improvement in Order Flow Auctions - Bachu, Wan / Uniswap Labs (2024)](https://blog.uniswap.org/measuring-price-improvement-with-order-flow-auctions) - Open-source methodology; dutch-auction OFAs yield 4-5 bps average price improvement
- [SoK: Ethereum's Enshrined Proposer Builder Separation - Koegler (2025)](https://arxiv.org/abs/2506.18189) - Systematization of ePBS mechanisms and gaps in current PBS designs

### Bitcoin: BitVM & OP_CAT (New)
- [BitVM: Quasi-Turing Complete Computation on Bitcoin - Aumayr et al. (2024)](https://eprint.iacr.org/2024/1995) - Formal analysis proving arbitrary computation encodable in Bitcoin Script via fraud proofs without consensus changes
- [BIP-347: OP_CAT in Tapscript - Heilman, Sabouri (2024)](https://github.com/bitcoin/bips/blob/master/bip-0347.mediawiki) - Reactivating OP_CAT for covenants, vaults, and ZK-proof verification on Bitcoin

### Consensus Protocols (New)
- [SoK: DAG-based Consensus Protocols (2024)](https://arxiv.org/abs/2411.10026) - Classifies DAG-BFT protocols into availability- vs consistency-focused, analyzing security and fairness
- [Beyond the Whitepaper: Where BFT Meets Reality - Wong, Kolegov, Mikushin (2024)](https://eprint.iacr.org/2024/1242) - Lessons from auditing production BFT systems; catalogs logic errors, concurrency bugs, crypto pitfalls

### Post-Quantum (New)
- [Migration to Post-Quantum: From ECDSA to ML-DSA - Dinu (2025)](https://eprint.iacr.org/2025/2025) - Practical comparison for blockchain signatures covering side-channel and fault-injection countermeasures
- [NIST FIPS 203/204/205 Post-Quantum Standards (August 2024)](https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards) - ML-KEM, ML-DSA, SLH-DSA finalized; mandates deprecation of quantum-vulnerable algorithms by 2035

### Formal Verification (New)
- [PropertyGPT: LLM-driven Formal Verification of Smart Contracts - Liu et al. (NDSS 2025)](https://arxiv.org/abs/2405.02580) - GPT-4 with RAG to auto-generate formal properties; detected 26 CVEs and 12 zero-days

### Cross-Chain (New)
- [Blockchain Cross-Chain Bridge Security: Challenges, Solutions, and Future Outlook (ACM DLT, 2024)](https://dl.acm.org/doi/10.1145/3696429) - Survey of bridge architectures with security analysis and taxonomy of bridge exploits
