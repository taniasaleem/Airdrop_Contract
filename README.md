# AirDrop Smart Contract

The `AirDrop` contract enables the efficient distribution of ERC-20 tokens to multiple addresses in a single transaction. This contract can be used for airdrops, distributing rewards, or any scenario requiring token transfers to multiple recipients.

## Features

- **Batch Token Distribution**: Distribute ERC-20 tokens to multiple recipients in a single transaction.
- **Flexible Amounts**: Specify individual token amounts for each recipient.
- **Address Verification**: Ensures that the provided token address is a valid contract.
- **Ownership Control**: Only the contract owner can initiate airdrops.

## Contract Functions

### `constructor()`

- **Description**: Initializes the `AirDropRc31` contract. No parameters are required for deployment.

### `doAirDrop(address[] memory _address, uint[] memory amounts, address tokenInstance)`

- **Description**: Transfers specified amounts of an ERC-20 token to a list of recipient addresses.
- **Parameters**:
    - `_address` - An array of addresses to receive tokens.
    - `amounts` - An array of token amounts corresponding to each recipient.
    - `tokenInstance` - The address of the ERC-20 token contract.
- **Returns**: A boolean value indicating whether the airdrop was successful.
- **Requirements**:
    - The `_address` and `amounts` arrays must have the same length.
    - `tokenInstance` must be a valid ERC-20 token contract.

### Example Usage

1. Deploy the contract.
2. Call the `doAirDrop` function, passing in:
    - A list of recipient addresses (`_address`).
    - The amounts of tokens to send to each recipient (`amounts`).
    - The address of the ERC-20 token contract (`tokenInstance`).

## Access Control

Only the contract owner can initiate the airdrop. This ensures secure and controlled token distribution.

## Prerequisites

- Solidity version ^0.8.1
- An ERC-20 token contract for the token distribution.

### Example

```solidity
address[] memory recipients = [0xRecipientAddress1, 0xRecipientAddress2];
uint[] memory amounts = [100 * 10 ** 18, 50 * 10 ** 18];
airDropInstance.doAirDrop(recipients, amounts, tokenAddress);

```

## Important Notes

1. Ensure that the contract has sufficient allowance to transfer the specified amounts from the sender’s wallet.
2. The function will revert if any transfer fails.
