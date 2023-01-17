# Themelio bridge covenant
The Themelio bridge covenant keeps track of Ethereum headers using Ethereum's native cryptographic primitives, trustlessly inheriting its security and allowing it to verify the contents of a particular storage mapping in the FancyName smart contracts, allowing it to act as a specialized Ethereum light-client.

A bridging event is initiated by the locking up of any coin to the Themelio bridge covenant. This covenant locks coins until they are proven to have been burned on the Ethereum network, at which point the coins are released. The covenant is written in Themelio's high-level language, Melodeon, learn more [here](https://melodeonlang.org).

## Covenant API
### Locking coins
To lock coins up on the Themelio network, all that needs to be done is send a transaction to the covenant's address where:
the first output of the transaction contains the coin that will be bridged
the recipient's Ethereum address is encoded in the first outputs's additional data field.

### Unlocking coins
To unlock coins, a transaction must be sent which attempts to spend the locked coin and has, in the additional data field of its first output, an encoded Merkle proof which proves the equivalent token amount was burned on Ethereum. This proof can be obtained by any Ethereum client.