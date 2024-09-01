# Cross-Chain Interoperability with Chainlink CCIP

This project demonstrates how to use Chainlink's Cross-Chain Interoperability Protocol (CCIP) to send a message from a smart contract deployed on the Metis Sepolia testnet to another smart contract on the Ethereum Sepolia testnet. 

___
The code is fully based on the getting started section : https://docs.chain.link/ccip/getting-started

But adapted for Metis chain.
___

## Prerequisites

Before you begin, make sure you have the following:

- Basic knowledge of Solidity and smart contract development.
- A MetaMask wallet configured with the Metis Sepolia and Ethereum Sepolia networks.
- Testnet funds:
  - **Metis Sepolia**: LINK, METIS.
  - **Ethereum Sepolia**: Testnet ETH.
- Access to the [Remix IDE](https://remix.ethereum.org/) for contract deployment.
- Testnet tokens from [Chainlink faucets](https://faucets.chain.link/).

## Setup

### Metis Sepolia Testnet

- **Router address:** `0xaCdaBa07ECad81dc634458b98673931DD9d3Bc14`
- **Chain selector:** `3777822886988675105`
- **Chain ID:** `59902`
- **LINK token address:** `0x9870D6a0e05F867EAAe696e106741843F7fD116D`
- **WMETIS token address:** `0x5c48e07062aC4E2Cf4b9A768a711Aef18e8fbdA0`
- **Native gas token:** METIS

### Ethereum Sepolia Testnet

- **Router address:** `0x0BF3dE8c5D3e8A2B34D2BEeB17ABfCeBaf363A59`

## Deployment Guide

### 1. Deploy the Sender Contract on Metis Sepolia

1. Open the `Sender.sol` contract in [Remix](https://remix.ethereum.org/).
2. Compile the contract.
3. Switch MetaMask to the Metis Sepolia testnet.
4. In Remix, set the environment to "Injected Provider - MetaMask".
5. Enter the following details under the deploy section:
   - **Router address:** `0xaCdaBa07ECad81dc634458b98673931DD9d3Bc14`
   - **LINK token address:** `0x9870D6a0e05F867EAAe696e106741843F7fD116D`
6. Deploy the contract on the Metis Sepolia testnet.
7. After deployment, copy the contract address.
8. Fund the deployed contract with at least 0.1 LINK to cover CCIP fees.

### 2. Deploy the Receiver Contract on Ethereum Sepolia

1. Open the `Receiver.sol` contract in [Remix](https://remix.ethereum.org/).
2. Compile the contract.
3. Switch MetaMask to the Ethereum Sepolia testnet.
4. In Remix, set the environment to "Injected Provider - MetaMask".
5. Enter the following details under the deploy section:
   - **Router address:** `0x0BF3dE8c5D3e8A2B34D2BEeB17ABfCeBaf363A59`
6. Deploy the contract on the Ethereum Sepolia testnet.
7. After deployment, copy the contract address.

### 3. Send Data from Metis Sepolia to Ethereum Sepolia

1. Switch MetaMask back to the Metis Sepolia testnet.
2. In Remix, expand the deployed sender contract.
3. Find the `sendMessage` function and fill in the following:
   - **destinationChainSelector:** `16015286601757825753` (for Ethereum Sepolia).
   - **receiver:** The address of the receiver contract deployed on Ethereum Sepolia.
   - **text:** The message you want to send, e.g., "Hello World!".
4. Click `transact` to send the message.
5. Confirm the transaction in MetaMask.

### 4. Verify the Message on Ethereum Sepolia

1. Use the transaction hash from the Metis Sepolia testnet to track the cross-chain message in the [CCIP Explorer](https://ccip.chain.link/).
2. Once the status is marked as "Success," the message should have been delivered.
3. In Remix, switch MetaMask to the Ethereum Sepolia testnet.
4. Expand the deployed receiver contract.
5. Click the `getLastReceivedMessageDetails` function to view the received message.

That's it!
