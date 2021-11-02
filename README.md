# wNano Concept

Links:

1. https://github.com/PlasmaPower/musig-nano
2. https://nanojson.medium.com/how-to-use-nano-multisig-33c8865ef8b1

1. Any implementation will be multisig. This will prevent one person holding any nano that is wrapped and will require multiple people (Monitors) to work together to mint / redeem wNano.
2. Monitors will hold part of the multisig key as detailed in the above links for nano and will hold part of a multisig key for BSC. Actors will run a monitor that monitors two addresses. One on the Nano side and one on the BSC side.
4. A BSC user will sign a transaction similar to the wBan implementation to claim their nano address. Example signed wBan message below.
5. When a transaction arrives into the monitored Nano wallet. The Monitors will sign a transaction on the BSC chain to mint and transfer to the corresponding BSC address from the Nano sender address.
6. When a transaction arrives into the monitored BSC wallet. The Monitors will sign a transaction on the BSC chain to redeem(remove) the wNano and the the Monitors will sign a transaction on Nano to transfer to the corresponding Nano address from the BSC sender address.




Example Signed wBan message:

'I hereby claim that the BAN address "ban_1bananobh5rat99qfgt1ptpieie5swmoth87thi74qgbfrij7dcgjiij94xr" is mine'. This in proxy links a Nano address and a BSC address.
