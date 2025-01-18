# AITU_SE2324_KV Token Contract  

## Overview  
This project implements an ERC-20 token named `AITU_SE2324_KV` as part of the 3rd assignment. The project demonstrates the implementation of the ERC-20 token standard alongside custom functionalities for transaction tracking, metadata retrieval, and human-readable timestamps.  

The token was first deployed and tested locally on a simple testnet environment to ensure correctness, followed by deployment on the Sepolia Testnet as part of the bonus task.  

---

## Token Specifications  
- **Token Name**: AITU_SE2324_KV  
- **Token Symbol**: AITU  
- **Decimals**: 18  
- **Initial Supply**: 2000 tokens (scaled by `10^18` for decimal precision). p.s. Actually can be any desired amount  

The contract uses OpenZeppelin’s secure and tested `ERC20` implementation for all standard token operations.  

---

## Main Features  

### ERC-20 Standard Compliance  
The contract inherits from OpenZeppelin’s `ERC20` library, which ensures compatibility with the ERC-20 standard. It provides:  
- Token transfers via `transfer` and `transferFrom`.  
- Allowance mechanisms for third-party transfers.  
- Accurate handling of decimal precision with 18 decimal places.  

### Custom Functionalities  

1. **Transaction Tracking**  
   - The contract overrides `transfer` and `transferFrom` to track the most recent transaction.  
   - A `TransactionInfo` struct stores:  
     - Sender address.  
     - Receiver address.  
     - Amount transferred.  
     - Timestamp of the transaction.  

2. **Human-Readable Timestamp**  
   - Converts the block timestamp of the latest transaction into a readable format (e.g., "2 days, 4 hours, 20 minutes ago").  
   - The function `getLatestTransactionTimestamp` leverages a utility function `timestampToString` to perform this conversion.  

3. **Sender and Receiver Retrieval**  
   - `getTransactionSender`: Retrieves the sender's address for the latest transaction.  
   - `getTransactionReceiver`: Retrieves the receiver's address for the latest transaction.  

4. **Utility Functions**  
   - `uint2str`: Converts integers (e.g., time intervals) to strings for readable output.  

---

## Deployment Process  

### 1. Local Testnet Deployment and Testing  
The contract was initially deployed and tested on a local testnet to verify its functionality. The process included:  

1. **Contract Deployment**  
   - The contract was deployed with an initial supply of 2000 tokens.  
   - Tokens were minted to the deployer’s wallet.  

2. **Token Transfers**  
   - Tokens were transferred from the deployer’s wallet to another wallet using `transfer`.

3. **Function Testing**  
   After performing transactions, the following functions were tested to ensure they returned accurate results:  
   - `balanceOf`: Verified the token balance of wallets.  
   - `decimals`: Retrieved the token’s decimal places (18).  
   - `getLatestTransactionTimestamp`: Displayed the timestamp of the most recent transaction in a human-readable format.  
   - `getTransactionSender` and `getTransactionReceiver`: Returned the sender and receiver addresses of the last transaction.  
   - `latestTransaction`: Provided detailed information about the most recent transaction (sender, receiver, amount, timestamp).  
   - `name`: Displayed the token’s name.  
   - `symbol`: Displayed the token’s symbol.  
   - `totalSupply`: Verified the total supply of tokens (2000 tokens, scaled by decimals).  

4. **Screenshots**  
Screenshots of the deployment and testing process on the local testnet are available by `deploylocal.pdf` and showcase the following:  
   - Contract deployment and initial supply allocation.  
   - Token transfers between wallets.  
   - Outputs of the custom functions (`getLatestTransactionTimestamp`, `getTransactionSender`, `getTransactionReceiver`, etc.).  

---

### 2. Sepolia Testnet Deployment (Bonus Task)  
After validating the contract functionality locally, it was deployed on the Sepolia Testnet using the Metamask wallet.  

#### Deployment Details:  
- **Network**: Sepolia Testnet  
- **Wallet**: Metamask  
- **Initial Supply**: 2000 tokens  
- **Contract Address**: `0x5CCd34AADA8D03584a3d94C438Eff058B50cE81A`

#### Testing on Sepolia  
The same tests conducted on the local testnet were repeated on Sepolia, including:  
- Token transfers between wallets.  
- Verification of custom functions.  
- Balance checks and metadata retrieval.  

#### Screenshots  
The file `sepoliascreens.pdf` contains evidence of the contract deployment and interactions on Sepolia. This includes:  
- Confirmation of contract deployment.  
- Successful token transfers.  
- Outputs of custom and standard ERC-20 functions.  

---

## Tools and Libraries  

1. **Development Tools**  
   - **Solidity Compiler**: ^0.8.0  
   - **Remix IDE**: For contract development and initial testing.  
   - **Metamask Wallet**: For deployment and testing on Sepolia.  

2. **Libraries**  
   - **OpenZeppelin**: Used for ERC-20 standard implementation.  (Heavily)

3. **Blockchain Networks**  
   - **Local Testnet**: For initial deployment and testing.  (Ganache, Remix VM)
   - **Sepolia Testnet**: For the bonus task.  

---

## How to Use  

### Deployment  
1. Deploy the contract using Remix or another Solidity IDE, specifying an initial supply (e.g., 2000 tokens).  
2. Interact with the deployed contract using tools like Metamask, Remix, or blockchain libraries (e.g., Web3.js, Ethers.js).  

### Interactions  
- **Token Transfers**: Use `transfer` to send tokens.  We have `allowance` and `transferFrom` for use by 3rd party dApps. 
- **Retrieve Metadata**: Call the custom functions to get details about the latest transaction, token name, symbol, decimals, and total supply.  Mostly utilized by the metamask itself.

---





