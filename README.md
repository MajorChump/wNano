# wNano Concept

Links:

1. https://github.com/PlasmaPower/musig-nano
2. https://nanojson.medium.com/how-to-use-nano-multisig-33c8865ef8b1

Concept:

1. Any implementation will be multisig. This will prevent one person holding any nano that is wrapped and will require multiple people (Monitors) to work together to mint / redeem wNano.
2. Monitors will hold part of the multisig key as detailed in the above links for nano and will hold part of a multisig key for BSC. Actors will run a monitor that monitors two addresses. One on the Nano side and one on the BSC side.
4. A BSC user will sign a transaction similar to the wBan implementation to claim their nano address. Example signed wBan message below.
5. When a transaction arrives into the monitored Nano wallet. The Monitors will sign a transaction on the BSC chain to mint and transfer to the corresponding BSC address from the Nano sender address.
6. When a transaction arrives into the monitored BSC wallet. The Monitors will sign a transaction on the BSC chain to redeem(remove) the wNano and the the Monitors will sign a transaction on Nano to transfer to the corresponding Nano address from the BSC sender address.

Nano MultiSig:

Requires 100% agreement which is a risk if a Monitor decides not to monitor anymore. To avoid this we would need to share keys??? AB BC CA?

1. Using the example of 3 monitors. 
2. Each Monitor would have a private key and public address. Each monitor would share its private key with one other monitor in a circle as follows

Monitor A -> Monitor B -> Monitor C -> Monitor A

In this example A would know AC but would need B to complete a transaction. If B was to go offline, C would know CB and so it would be possible to transfer the funds out of the multisig wallet to a new multisig wallet with a new B.

3. https://github.com/PlasmaPower/musig-nano exports a CFFI with functions for the 3 stages of signing. (Blocker: In theory the 3 Monitors should detect the transaction at around the same time. They will all create a block and sign it and send to each other to sign the same block. Will the block they all create be the same hash? if not we will need to work this out to prevent duplication of work).

Example Signed wBan message:

'I hereby claim that the BAN address "ban_1bananobh5rat99qfgt1ptpieie5swmoth87thi74qgbfrij7dcgjiij94xr" is mine'. This in proxy links a Nano address and a BSC address.
