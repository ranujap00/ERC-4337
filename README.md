# ERC-4337

## Difference between POW and POS (Consensus layers)
  - POW - Miners have to validate the transaction. Who ever solves it first can add it to the blockchain. Consumes a lot of power.
  - POS - No miners. Validators can stake their tokens. One who has staked a large no of tokens has a high chance of getting selected as a validator.

## Account Abstraction
  - Account abstraction is a feature of ERC-4337 that allows users to interact with smart contracts as if they were interacting with externally owned accounts.
      - EOA: metamask, trust wallet etc
      - contract accs: not owned by a user and user has no control. No private key
  - This is achieved by account abstraction contract.
  - Account abstraction contracts can implement security features such as multi-signature and social recovery.
  - Downsides of EOA
      - If you loose the private key / seed phrase to the wallet, you will not be able to recover the funds in the wallet.
  - contract accounts over EOA
      - You can code your own function and have it as a feature in your wallet. (eg: permission controls)

## High level overview on how a transaction works
  1. A user wants to send a transaction.
  2. The user's wallet constructs a UserOperation data structure that represents the transaction.
  3. The user signs the UserOperation data structure with their private key.
  4. The wallet sends the signed UserOperation data structure to the Account Abstraction Contract.
  5. The Account Abstraction Contract verifies the signature on the UserOperation data structure.
  6. The Account Abstraction Contract executes the transaction.
  7. The Account Abstraction Contract updates the user's account state.
  8. The wallet notifies the user that the transaction has been successfully executed.
