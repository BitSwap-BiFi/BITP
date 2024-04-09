# BITP-11: MEVs Attacks

`author: 22388o` `author: Rsync25` `mandatory` `final`

MEV (Miner Extractable Value) refers to the potential profit miners can make by reordering or censoring transactions in a block. While most discussions around MEV center on Ethereum due to its flexibility in executing smart contracts, MEV can also impact Bitcoin, albeit in a different manner.

In the context of AMM (Automated Market Maker) protocols on Bitcoin, such as those facilitating decentralized exchanges (DEXs) or liquidity pools, MEV can manifest in various ways:

1. **Front-running**: Miners can reorder transactions to place their own trades ahead of others, taking advantage of price changes in the market.

2. **Arbitrage opportunities**: Miners can exploit price differences between decentralized and centralized exchanges by prioritizing transactions that benefit them.

3. **Transaction censorship**: Miners could censor transactions that compete with their own or benefit from including certain transactions and excluding others.

Possible solutions to MEV in AMM protocols on Bitcoin include:

1. **Layer 2 solutions**: Moving transactions off-chain, such as using the Lightning Network for faster and more private transactions, reduces the exposure to MEV.

2. **Smart contract execution order randomness**: Introducing randomness in the execution order of smart contracts can make it harder for miners to predict profitable trades with RGB protocol

3. **Transaction batching**: Batching transactions can make it more expensive for miners to selectively include or exclude transactions with Replace by Fee (RBF)
   
4. **Market-based solutions**: Develop economic mechanisms that disincentivize or neutralize MEV, such as fee markets that make it unprofitable for miners to engage in MEV.

It's worth noting that MEV is a complex and evolving issue, and any solution must consider the trade-offs involved, including impact on decentralization, security, and usability.
