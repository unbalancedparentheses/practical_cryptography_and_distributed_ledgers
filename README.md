# Practical Cryptography and Distributed Ledgers

- Pablo Deymonnaz
- Diego Kingston
- Federico Carrone

Disclaimer: We're still organizing everything. Some links might be in an incorrect section.

# 1. Foundations of Cryptography
- Groups, Rings and Fields
- Finite Fields
- Modular Arithmetic
- P versus NP problem
- Computationally Hard Problems: Factorization and the Discrete Logarithm 

## Readings
- [Chapter entitled Cryptography: Sections on Symmetric Crypto Primitives - Anderson Security Engineering](https://www.cl.cam.ac.uk/~rja14/Papers/SEv2-c05.pdf)
- [Ben Lynn's notes on cryptography, abstract algebra and number theory](https://crypto.stanford.edu/pbc/notes/)
- [Reed Solomon](https://mazzo.li/posts/reed-solomon.html)
- [Reed–Solomon codes for coders](https://en.wikiversity.org/wiki/Reed%E2%80%93Solomon_codes_for_coders)

## Exercises
- [Programming Bitcoin: Learn How to Program Bitcoin from Scratch - Jimmy Song]()

# 2 Symmetric encryption
- AES
- ChaCha20

# 3. Asymmetric encryption
- Diffie-Hellman Key Exchange
- ECDH
- ElGamal
- RSA

## Readings
- [Twenty Years of Attacks on the RSA Cryptosystem - Dan Boneh](https://crypto.stanford.edu/~dabo/papers/RSA-survey.pdf)

# 4. Signatures, Hash Functions
- MD5
- SHA1
- Keccak - SHA3
- ECDSA signature
- Schnor signature
- BLS signature

## Readings
- [What is a Cryptographic Hash Function? - Alin Tomescu](https://decentralizedthoughts.github.io/2020-08-28-what-is-a-cryptographic-hash-function/)

# 5. What is Money?
- [A Brief History of Money](https://nakamoto.com/a-brief-history-of-money/)
- [Shelling Out: The Origins of Money - Nick Szabo](https://nakamotoinstitute.org/shelling-out/)
- [What is Money anyway - Lyn Alden](https://www.lynalden.com/what-is-money/)
- [Money in the modern economy: an introduction](https://www.bankofengland.co.uk/-/media/boe/files/quarterly-bulletin/2014/money-in-the-modern-economy-an-introduction.pdf?la=en&hash=E43CDFDBB5A23D672F4D09B13DF135E6715EEDAC)
- [Money creation in the modern economy](https://www.bankofengland.co.uk/-/media/boe/files/quarterly-bulletin/2014/money-creation-in-the-modern-economy.pdf?la=en&hash=9A8788FD44A62D8BB927123544205CE476E01654)
- [The Cypherpunks](https://nakamoto.com/the-cypherpunks)

# 6. Introduction to blockchains and cryptocurrencies
- What is a blockchain?
- State Machines
- Consensus
- Merkle Trees

## Readings
- [Why cryptocurrencies are interesting?](https://mirror.xyz/0xaFaBa30769374EA0F971300dE79c62Bf94B464d5/us0MyyUNYwSXazM0YCrGscbRWr18s0aIIZqyHBbTWfM)
- [Cancelled Nickel Trades on the LME](https://youtu.be/tHXF5LyLI4M)
- [What is a Blockchain - Ittai Abraham](https://decentralizedthoughts.github.io/2022-09-05-what-is-a-blockchain/)
- [How does everything tie together?](https://mirror.xyz/0xaFaBa30769374EA0F971300dE79c62Bf94B464d5/nsEwS5WZjLeydpX2x9XybTpu7dA5LpLNyayj93HnovA)
- [Blockchains as Cryptographic Data Structures - Pramod Viswanath](https://courses.grainger.illinois.edu/ece598pv/sp2021/lectureslides2021/ECE_598_PV_course_notes2.pdf)
- [Hash functions](https://nakamoto.com/hash-functions/)
- [Merkle Tree](https://nakamoto.com/merkle-trees/)
- [What is a Merkle Tree](https://decentralizedthoughts.github.io/2020-12-22-what-is-a-merkle-tree/)

- [What is Consensus? - Kartik Nayak, Ittai Abraham](https://decentralizedthoughts.github.io/2019-06-27-defining-consensus/)
- [Flavours of State Machine Replication - Ittai Abraham](https://decentralizedthoughts.github.io/2019-10-25-flavours-of-state-machine-replication/)
- [Consensus for State Machine Replication - Kartik Nayak, Ittai Abraham](https://decentralizedthoughts.github.io/2019-10-15-consensus-for-state-machine-replication/)
- [From Single-Shot Agreement to State Machine Replication](https://decentralizedthoughts.github.io/2022-11-19-from-single-shot-to-smr/)

# 7. Bitcoin
- Two general's Problem
- What Is the Byzantine Generals Problem?

## Readings
- [The Byzantine Generals Problem](https://dl.acm.org/doi/10.1145/357172.357176)
- [Blockchain Basics & Consensus - MIT 15.S12 Blockchain and Money - Gary Gensler](https://www.youtube.com/watch?v=w7HDA8gUbpQ&list=PLUl4u3cNGP63UUkfL0onkxF6MYgVa04Fn)
- [Paxos(etcd) vs. Nakamoto(Bitcoin): consensus](https://gyuho.dev/paxos-etcd-vs-nakamoto-bitcoin-consensus.html)
- [Nakamoto's Longest-Chain Wins Protocol](https://decentralizedthoughts.github.io/2021-10-15-Nakamoto-Consensus/)
- [Learning-Bitcoin-from-the-Command-Line](https://github.com/BlockchainCommons/Learning-Bitcoin-from-the-Command-Line)
- [Bitcoin: A Peer-to-Peer Electronic Cash System](https://bitcoin.org/bitcoin.pdf)
- [But how does bitcoin actually work?](https://youtu.be/bBC-nXj3Ng4) 
- [Cryptoeconomics In 30 Minutes by Vitalik Buterin](https://youtu.be/GQR1xjQn5Pg)

# 8. Ethereum
- Solidity
- ERC20
- ERC721
- ERC-1155

## Readings
- [DEVCON1: Understanding the Ethereum Blockchain Protocol - Vitalik Buterin](https://youtu.be/gjwr-7PgpN8)
- [Ethereum Whitepaper](https://ethereum.org/en/whitepaper/)
- [Learn Solidity in Y Minutes](https://learnxinyminutes.com/docs/solidity/)
- [Getting Started with Solidity](https://cryptomarketpool.com/getting-started-with-solidity/)
- [OpenZeppelin](https://docs.openzeppelin.com/contracts/4.x/)
- [Go Ethereum](https://geth.ethereum.org/docs)
- [Ethereum development made easy with Foundry](https://www.notamonadtutorial.com/ethereum-development-made-easy-with-foundry/)
- [scaffold-eth: 🏗 forkable Ethereum dev stack focused on fast product iterations](https://github.com/scaffold-eth/scaffold-eth)
- [Scaffold-Eth Challenges](https://github.com/scaffold-eth/scaffold-eth-challenges)

# 9. Wallets, ENS, Stablecoins, DeFi
- [Metamask and other wallets]()
- DEMO: Uniswap, Curve, OpenSea NFTs, Maker/Oasis, Multisig
- [lil web3: Small, focused, utility-based smart contracts](https://github.com/m1guelpf/lil-web3)
- [Programming DeFi: Uniswap V2. Part 1](https://jeiwan.net/posts/programming-defi-uniswapv2-1/)
- [The Problems with DeFi & Crypto](https://www.lynalden.com/defi-problems/)
- [Programming DeFi: Uniswap V2. Part 1](https://ethereum.org/en/developers/tutorials/uniswap-v2-annotated-code/)
- [Programming DeFi: Uniswap V2. Part 2](https://jeiwan.net/posts/programming-defi-uniswapv2-2/)
- [Programming DeFi: Uniswap V2. Part 3](https://jeiwan.net/posts/programming-defi-uniswapv2-3/)
- [Uniswap V3 Development Book](https://uniswapv3book.com/)

# 9. Oracles, Bridges and Rollups
- Oracles
- Bridges
- [An Incomplete Guide to Rollups](https://vitalik.ca/general/2021/01/05/rollup.html)

# 10. EVM
- [EVM codes](https://www.evm.codes/?fork=merge)
- [EVM Deep Dives: The Path to Shadowy Super Coder 🥷 💻 - Part 1](https://noxx.substack.com/p/evm-deep-dives-the-path-to-shadowy)
- [ABI]()

# 11. Security
- [Capture the Ether](https://capturetheether.com/challenges/)
- [Ethernaut](https://ethernaut.openzeppelin.com/)
- [Damn Vulnerable DeFi](https://www.damnvulnerabledefi.xyz/)
- [echidna - Ethereum smart contract fuzzer](https://github.com/crytic/echidna)
- [manticore - Symbolic execution tool](https://github.com/trailofbits/manticore)
- [mythril - Security analysis tool for EVM bytecode](https://github.com/ConsenSys/mythril)

# 12. MEV
- [MEV](https://research.paradigm.xyz/MEV)
- https://www.youtube.com/watch?v=UZ-NNd6yjFM

# 13. Zcash, SNARKs and Privacy in blockchains**
- [Zcash]()
- [Aztec]()

# 14. Scaling blockchains
- Data Availability
- Optimistic versus Zero Knoweledge Rollups
- Circom, Cairo, Noir

## Readings
- [Data, Consensus, Execution: Three Scalability Bottlenecks for State Machine Replication - Ittai Abraham](https://decentralizedthoughts.github.io/2019-12-06-dce-the-three-scalability-bottlenecks-of-state-machine-replication)
- [Understanding Blockchain Latency and Throughput - Lefteris Kokoris-Kogias](https://www.paradigm.xyz/2022/07/consensus-throughput)
- [(Almost) Everything you need to know about Optimistic Rollup - Georgios Konstantopoulos](https://www.paradigm.xyz/2021/01/almost-everything-you-need-to-know-about-optimistic-rollup)

# 15. Tendermint, HotStuff and Narwhal
- [What is the difference between PBFT, Tendermint, SBFT and HotStuff? - Ittai Abraham](https://decentralizedthoughts.github.io/2019-06-23-what-is-the-difference-between/)
- [DAG Meets BFT - The Next Generation of BFT Consensus - Ittai Abraham](https://decentralizedthoughts.github.io/2022-06-28-DAG-meets-BFT/)

# 16. Bitcoin: SegWit, Taproot, Lightning Network and Covenants
- [Segregated Witness](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki)
- [Taproot: SegWit version 1 spending rules](https://github.com/bitcoin/bips/blob/master/bip-0341.mediawiki)
- [Covenants: CHECKTEMPLATEVERIFY]()
- [A Look at the Lightning Network - Lyn Alden](https://www.lynalden.com/lightning-network/)

# Books
- [Bitcoin and Cryptocurrency Technologies: A Comprehensive Introduction - Arvind Narayanan, Joseph Bonneau, Edward Felten, Andrew Miller, and Steven Goldfeder](https://press.princeton.edu/books/hardcover/9780691171692/bitcoin-and-cryptocurrency-technologies)
- [Security Engineering — Ross Anderson](https://www.cl.cam.ac.uk/~rja14/book.html)

## Blockchain
- [Foundations of Distributed: Consensus and Blockchains - Elaine Shi](http://elaineshi.com/docs/blockchain-book.pdf)

## Cryptography
- [Handbook of Applied Cryptography -  Menezes, van Oorschot and Vanstone]()
- [Crypto 101 - lvh]()

## Abstract Algebra and Number Theory
- [An Introduction to Mathematical Cryptography - Jeffrey Hoffstein, Jill Pipher, Joseph H. Silverman]()
- [A Course in Number Theory and Cryptography - Neal Koblitz]()
- [Algebra for Applications - Arkadii Slinko]()
- [A Computational Introduction to Number Theory and Algebra - Victor Shoup]()
- [Elliptic Curves Number Theory and Cryptography - Lawrence C. Washington]()
- [The prime number conspiracy - Thomas Lin]()

**Other courses**
- [Practical Cryptographic Systems - Matthew Green](https://github.com/matthewdgreen/practicalcrypto/wiki/Spring-2020-Syllabus)
- [Cryptocurrency Class 2022 - Patrick McCorry](https://cryptocurrencyclass.github.io/)
- [Principles of Blockchains - Pramod Viswanath](https://courses.grainger.illinois.edu/ece598pv/sp2021/)
- [Blockchain And Money - Gary Gensler](https://ocw.mit.edu/courses/15-s12-blockchain-and-money-fall-2018/video_galleries/video-lectures/)
- [Decentralized Finance MOOC - Dan Boneh, Arthur Gervais, Andrew Miller, Christine Parlour and	Dawn Song](https://defi-learning.org/f22)
- [Stanford CS 251 Blockchain Technologies - Dan Boneh](https://cs251.stanford.edu/syllabus.html)
- [Stanford EE374 Blockchain Foundations - David Tse, Dionysis Zindros](https://web.stanford.edu/class/ee374/)
- [ECE595 Foundations of Blockchain Systems - Sreeram Kannan](https://ece595uwseattle.github.io/schedule)
- [CS598CAL Consensus Algorithms - Ling Ren](https://sites.google.com/view/cs598cal?pli=1)

# Missing topics
- Light Clients
- UTXO vs Account model
- The Blockchain Trilemma
- PoS vs PoW
- Tendemint
- Hash Functions
- Digital Signatures
- Soft Forks vs Hard Forks
- Onchain vs offchain computation
- Taproot, Segwit, Covenants
- Chinese remainder theorem
- MAC
- One Time Pad
- MAC
- Stream ciphers and block ciphers
- Signatures
- DeFi Lending (aave vs)
- Account Abstraction (argent x)
- muun, non custodial wallets
- nuestra vida depende de un par de bases de datos https://twitter.com/argentHQ/status/1513488734498525184

**Links to add**

650.445:

- [](https://ethereum.org/en/developers/tutorials/uniswap-v2-annotated-code/)
- https://github.com/matthewdgreen/practicalcrypto/wiki/Spring-2020-Syllabus
- https://www.cl.cam.ac.uk/~rja14/book.html
- https://web.stanford.edu/class/ee374/
- https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/
- https://www.youtube.com/channel/UCqeIoMMTKl9PK9O8BcEpNhQ
- https://youtu.be/-6BtBUbiUIU
- https://github.com/decrypto-org/blockchain-papers
- https://blog.ethereum.org/2016/05/09/on-settlement-finality/
- https://medium.com/mechanism-labs/finality-in-blockchain-consensus-d1f83c120a9a#:~:text=In%20the%20blockchain%20setting%2C%20finality,be%20arbitrarily%20changed%20or%20reversed
- https://github.com/Mechanism-Labs/MetaAnalysis-of-Alternative-Consensus-Protocols
- https://www.youtube.com/watch?v=O1Iq27ItGGg
- https://medium.com/@lightcoin/the-differences-between-a-hard-fork-a-soft-fork-and-a-chain-split-and-what-they-mean-for-the-769273f358c9
- https://dspace.mit.edu/handle/1721.1/127476
- https://medium.facilelogin.com/the-mystery-behind-block-time-63351e35603a
- https://dankradfeist.de/ethereum/2021/05/20/what-everyone-gets-wrong-about-51percent-attacks.html
- https://dinhtta.github.io/flpcap/
- https://www.the-paper-trail.org/post/2012-03-25-flp-and-cap-arent-the-same-thing/
- https://youtu.be/mDyBbGCiBUU
- https://medium.com/@alxlpsc/critical-privacy-vulnerability-getting-exposed-by-metamask-693c63c2ce94
- https://www.cnbc.com/2021/08/23/people-are-paying-millions-of-dollars-for-digital-pictures-of-rocks.html
- https://mudit.blog/miso-war-room/
- https://github.com/ConsenSys/surya
- https://youtu.be/DlNDYMNJ5zQ
- [Hayden Adams Explains Uniswap and the Rise of DeFi](https://open.spotify.com/episode/3TT6aFeMWnFPZTlfy5fxvv?si=KCw3uWvJQAaeBCZoH1RwNw&dl_branch=1)
- https://cryptomarketpool.com/getting-started-with-solidity/
- https://www.youtube.com/watch?v=U6q5gBnxgS0&list=PL9lJNCwSDOhVEf0ajBHkNNICFqNnoGx7r&index=4
- https://twitter.com/guiltygyoza/status/1447641997012082693?s=12
- https://blog.zkga.me/announcing-darkforest
- https://github.com/Rari-Capital/solmate
- https://polynya.medium.com/why-rollups-data-shards-are-the-only-sustainable-solution-for-high-scalability-c9aabd6fbb48
- https://polynya.medium.com/volitions-best-of-all-worlds-cfd313aec9a8
- https://youtu.be/7Kq3YWsysc0
- https://youtu.be/RxL_1AfV7N4
- https://dune.xyz/queries/1161
- https://www.youtube.com/watch?v=B2iNXMiGEms
- https://medium.com/starkware/volition-and-the-emerging-data-availability-spectrum-87e8bfa09bb
- https://jacob-eliosoff.medium.com/whats-the-simplest-possible-decentralized-stablecoin-4a25262cf5e8
- https://github.com/usmfum/USM
- https://writings.flashbots.net/writings/the-anatomy-of-an-inspector/
- https://twitter.com/siegerhino2/status/1445024119112835073?s=21
- https://app.umbra.cash/faq#how-does-umbra-compare-to-tornado-cash-and-aztec
- https://www.vice.com/en/article/dyp7vw/the-cia-is-deep-into-cryptocurrency-director-reveals?utm_source=motherboardtv_facebook&utm_medium=social&fbclid=IwAR2Gxe3I1frUiU344r6bjBImXZz0uRUPvt4I5dBWI1BGZTG2fUV5O6_Q6KE
- https://www.samchepal.com/the-hidden-world-of/
- https://www.youtube.com/watch?v=cizLhxSKrAc&t=215s
- https://www.youtube.com/watch?v=Ehm-OYBmlPM
- https://github.com/Mikerah/awesome-foundations-of-DeFi
