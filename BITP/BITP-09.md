# BITP-09: Taproot Channel

`author: 22388o` `author: Rsync25` `mandatory` `final`

Taproot is a Bitcoin protocol upgrade that improves privacy and efficiency, including for Lightning Network channels. Taproot allows multiple parties to collaborate on a single transaction, known as a "collaborative close," which can be particularly useful for Lightning Network channels.

In a Taproot-enabled Lightning channel, when both parties agree to close the channel cooperatively, they can construct a single Taproot output that represents the final state of the channel. This output is cheaper to create and spend on-chain compared to the traditional method, which would require multiple outputs and additional scripts.

Taproot also enhances privacy by making it harder for external observers to distinguish between different types of transactions, including Lightning Network channel closures. This is achieved through a cryptographic technique called "pay-to-contract" (PTC), which allows for the hiding of complex spending conditions until the funds are actually spent.

Overall, Taproot channels on the Lightning Network offer improved efficiency, privacy, and cost savings compared to non-Taproot channels, making them a valuable enhancement for the scalability and usability of the Lightning Network.

## Why is important for Bitswap?

- Enable Bifrost
- Multipeer channels
- Multi Oracle channels
