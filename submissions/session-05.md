
# Session 05 - Smart Contract & Digital Assets

- **Student:** Đỗ Duy Hiếu
- **GitHub:** [Your GitHub Username]
- **Date:** 17/11/2026
- **Topic:** Smart Contracts, Tokens and Blockchain Execution

---

## 1. Summary

In Session 05, I learned about Smart Contracts and Digital Assets in Blockchain technology.

The main topics covered include:

- Understanding Smart Contracts and how they work.
- Distinguishing between Native Coins and Tokens.
- Learning about Mint, Transfer, and Burn mechanisms.
- Understanding Stablecoins and NFTs.
- Learning about Gas Fees and Transaction Fees.
- Exploring EVM, SVM, and WASM execution environments.
- Applying Blockchain knowledge to practical projects.

## 2. Topic Notes

### 2.1. Smart Contract

A Smart Contract is a program deployed on a Blockchain that automatically executes predefined instructions when specific conditions are met.

**Key characteristics:**
- Automatic execution.
- Transparency and traceability.
- Decentralized operation.
- Data integrity.

**Practical example:**

A ticket booking system using Blockchain:
1. A user purchases a ticket.
2. The Smart Contract records the transaction.
3. Ticket ownership is updated.
4. Ownership history can be verified on the Blockchain.

**Limitations:**
- Smart Contracts cannot directly access external data without Oracles.
- Programming errors may cause security vulnerabilities.
- Deployed contracts may be difficult to modify.

### 2.2. Native Coin vs Token

| Criteria | Native Coin | Token |
|---|---|---|
| Definition | Blockchain's native asset | Asset created on an existing Blockchain |
| Creation | Built into Blockchain protocol | Usually created through Smart Contracts |
| Main purpose | Network fees and operations | Utility, governance, payments |
| Examples | ETH, SOL | USDT, USDC |

**Example:**
- ETH is the native coin of Ethereum.
- USDT and USDC can exist as tokens on Ethereum.

### 2.3. Token Lifecycle

There are three important operations in Token management:

**1. Mint**
- Creates new tokens.
- Increases the total supply.
- Requires appropriate permissions.

**2. Transfer**
- Moves tokens between wallets.
- Decreases the sender's balance.
- Increases the receiver's balance.
- Does not change the total supply.

**3. Burn**
- Removes tokens from circulation.
- Decreases the total supply.
- Can be used for token supply management.

**Example:**

| Operation | Total Supply |
|---|---:|
| Initial supply | 100 |
| Mint 20 tokens | 120 |
| Transfer 10 tokens | 120 |
| Burn 5 tokens | 115 |

### 2.4. Stablecoins

Stablecoins are cryptocurrencies designed to maintain a relatively stable value against an underlying asset, commonly the US Dollar.

**Examples:**
- USDT
- USDC
- DAI

**Main types:**
1. Fiat-backed Stablecoins.
2. Crypto-collateralized Stablecoins.
3. Algorithmic Stablecoins.

**Depeg:**

Depeg occurs when a Stablecoin loses its intended price peg.

For example, a Stablecoin designed to maintain a value of $1 may fall to $0.97.

### 2.5. NFT (Non-Fungible Token)

NFTs are unique digital tokens that cannot be exchanged on a one-to-one basis like interchangeable tokens.

**Characteristics:**
- Each NFT has a unique identifier.
- Represents digital assets or certain ownership rights.
- Can be transferred between wallets.
- Transactions are recorded on Blockchain.

**Applications:**
- Digital art.
- Gaming assets.
- Event tickets.
- Digital collectibles.
- Certificates.

Owning an NFT does not automatically mean owning the copyright of the associated artwork.

### 2.6. Gas Fee and Transaction Fee

Gas measures the computational resources required to execute transactions on Ethereum.

**Basic formula:**

`Transaction Fee = Gas Used × Gas Price`

Where:
- Gas Used: Amount of gas consumed.
- Gas Price: Cost per unit of gas.
- Transaction Fee: Total transaction cost.

**Example:**

- Gas Used = 21,000.
- Gas Price = 20 Gwei.
- 1 Gwei = 0.000000001 ETH.

Transaction Fee:

`21,000 × 20 × 0.000000001 = 0.00042 ETH`

**Important notes:**
- Complex transactions usually require more gas.
- Network congestion can increase gas prices.
- Reverted transactions may still consume gas.

### 2.7. Blockchain Execution Environments

| Environment | Full Name | Description |
|---|---|---|
| EVM | Ethereum Virtual Machine | Executes Ethereum-compatible Smart Contracts |
| SVM | Solana Virtual Machine | Executes programs in the Solana ecosystem |
| WASM | WebAssembly | Portable execution technology used by some Blockchain platforms |

**EVM:**
- Widely used in Ethereum-compatible networks.
- Supports Solidity Smart Contracts.
- Can be developed using Remix IDE.

**SVM:**
- Used in the Solana ecosystem.
- Designed for executing Solana programs.

**WASM:**
- Supports multiple programming languages.
- Provides portable execution.
- Used by several Blockchain ecosystems.

## 3. Practical Application

### 3.1. Connection with PortablePass

During the development of my PortablePass project, I realized that Smart Contracts could play an important role in document management and ownership verification.

Potential applications include:

- Recording document identifiers on Blockchain.
- Managing document access permissions.
- Tracking document ownership and transfer history.
- Verifying transactions through Smart Contracts.

### 3.2. Smart Contract Development Workflow

The basic development process includes:

1. Writing Smart Contract code using Solidity.
2. Compiling the code with Remix IDE.
3. Selecting an appropriate deployment environment.
4. Connecting MetaMask.
5. Deploying the Smart Contract.
6. Checking the deployed Contract address.
7. Testing Contract functions and transactions.

This workflow helped me understand the relationship between Smart Contracts, Blockchain wallets, and application interfaces.

## 4. Work Completed

- Studied Smart Contract fundamentals.
- Compared Native Coins and Tokens.
- Learned about Mint, Transfer, and Burn.
- Explored Stablecoins and NFTs.
- Studied Gas Fee calculations.
- Compared EVM, SVM, and WASM.
- Connected Blockchain concepts with PortablePass.
- Summarized the knowledge gained in Session 05.

## 5. Evidence

The following evidence can be added:

- Session 05 learning notes.
- Remix IDE interface screenshots.
- Smart Contract compilation screenshots.
- MetaMask connection screenshots.
- Contract deployment or interaction screenshots.

## 6. Blockers

Some challenges I identified during this session:

- I still need more practice reading and understanding Smart Contract code.
- I need to understand Gas Fee calculations more deeply.
- I need to distinguish compilation errors from execution errors.
- I need to improve my understanding of Frontend, MetaMask, and Smart Contract integration.
- I need to pay more attention to Contract addresses and Blockchain network selection.

## 7. Takeaways

Through Session 05, I gained a better understanding of Smart Contracts and their role in Blockchain applications.

I learned how different digital assets work, including Native Coins, Tokens, Stablecoins, and NFTs. I also understood the importance of Gas Fees and Blockchain execution environments.

The most important lesson is that developing a Blockchain application is not only about writing Smart Contracts. It also requires security considerations, transaction management, access control, and frontend integration.

These concepts will provide a foundation for improving my PortablePass project and developing my Blockchain programming skills in future sessions.

---

**End of Session 05**
