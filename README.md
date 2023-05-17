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

## UserOperation
  - A data structure that represents a user action in JSON format. It contains information such as the sender address, the recipient address, the amount of Ether to be transferred, and the data to be included in the transaction.
  - A UserOperation is signed by the user with their private key and sent to the Account Abstraction Contract. The Account Abstraction Contract verifies the signature and then executes the transaction.
  - Following are some of the attributes that can be passed to a user operation

Field | Type | Description
--- | --- | ---
**sender** | address | The account making the operation
**nonce** | uint256 | Data passed into the account along with the nonce during the verification step
**initCode**	 | bytes | The initCode of the account (needed if and only if the account is not yet on-chain and needs to be created on the fly)
**callData** | bytes |The data to pass to the sender during the main execution call
**callGasLimit** | uint256 | The amount of gas to allocate the main execution call
**verificationGasLimit** | uint256 | The amount of gas to allocate for the verification step
**preVerificationGas** | uint256 | The amount of gas to pay for to compensate the bundler for pre-verification execution and calldata
**maxFeePerGas** | uint256 | Maximum fee per gas (similar to EIP-1559 max_fee_per_gas)
**maxPriorityFeePerGas** | uint256 | Maximum priority fee per gas (similar to EIP-1559 max_priority_fee_per_gas)
**paymasterAndData** | bytes | 	Address of paymaster sponsoring the transaction, followed by extra data to send to the paymaster (empty for self-sponsored transaction)
**signature** | bytes | Data passed into the account along with the nonce during the verification step

  ```
  {
  "type": "object",
  "properties": {
    "sender": {
      "type": "string",
      "description": "The address of the user who is sending the transaction"
    },
    "nonce": {
      "type": "int",
      "description": "Data passed into the account along with the nonce during the verification step"
    }
    {
      .....
    }
  }
}
```
