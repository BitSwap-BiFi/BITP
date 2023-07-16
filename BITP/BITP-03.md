# BITP-03: DLCs

`author: 22388o` `mandatory` `final`

DLCs (Discreet Log Contracts) are another type of protocol built on top of the Bitcoin blockchain that enables the creation of smart contracts for financial agreements. DLCs allow parties to enter into contracts without requiring trust in a third party or an oracle. These contracts are "discreet" because the details of the contract are known only to the involved parties.

DLCs can be relevant in the context of decentralized exchanges (DEXs) as they provide a secure and decentralized way to facilitate certain types of trades. Here's how DLCs can be utilized in a DEX scenario:

1. Contract Creation: In a DEX, two parties who wish to trade a particular asset pair can create a DLC contract that specifies the terms of their trade. This could include details such as the assets involved, the exchange rate, and the duration of the contract.

2. Oracle Integration: DLCs typically use oracles to provide external data necessary for contract settlement. In a DEX, the oracle can provide price feeds or other relevant market information required for determining the trade's outcome. The oracle's role is to provide the agreed-upon data to the contract without having control over the contract itself.

3. Funding the Contract: Each party involved in the trade locks a certain amount of Bitcoin into the contract as collateral. This collateral ensures that each participant has a stake in the outcome and discourages malicious behavior. The collateral is usually held in multi-signature addresses, where both parties have control over their funds during the contract lifecycle.

4. Contract Execution: Once the contract is created and funded, it enters a waiting period until the specified end time or a specific outcome occurs. During this period, the contract remains on the Bitcoin blockchain without revealing its terms to external parties. The contract is enforceable by the Bitcoin network without the need for third-party arbitration.

5. Settlement: After the contract reaches its end time or the specified outcome occurs (e.g., a specific price is reached), the contract is settled. The settlement process determines how the collateral is distributed between the parties based on the contract terms and the oracle-provided data. The settlement transaction is executed on the Bitcoin blockchain, and the funds are released accordingly.

By utilizing DLCs in a DEX, traders can engage in trustless and decentralized trades without relying on centralized intermediaries or external oracles. DLCs provide security, privacy, and immutability through their execution on the Bitcoin blockchain.
