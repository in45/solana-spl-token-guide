# Solana & SPL Token Management Guide

This guide provides step-by-step instructions for setting up and managing Solana CLI, SPL CLI, and SPL tokens. Follow these instructions to configure your environment, create and manage SPL tokens, and perform token transfers.

## Prerequisites

Before proceeding, ensure you have the following installed:

### Solana CLI

Install the Solana CLI by running the following command:

```sh
sh -c "$(curl -sSfL https://release.solana.com/v1.9.5/install)"
```
### SPL CLI

To install the SPL CLI using Cargo, run:

```sh
cargo install spl-token-cli
```
### Solana Wallet
1. Generate a New Solana Wallet
Generate a new Solana wallet and save the private key to a file with:
```sh
solana-keygen new -o alice.json
```
The file alice.json will contain your account's private key.

2. Check Your Solana Cluster Configuration
Verify the current Solana cluster configuration with:

```sh
solana config get
```
3. Set the Solana Cluster to Testnet
Configure your Solana CLI to use the Testnet:
```sh
solana config set --url https://api.devnet.solana.com
solana config set --keypair ./alice.json
```
4. Check Your SOL Balance

To check your SOL balance:
```sh
solana balance
```
To check the balance of a specific account:

```sh
solana balance <Account-pubKey>
```
5. Get Testnet SOL
Obtain testnet SOL from the Solana faucet:

[Solana Faucet](https://solfaucet.com)

6. Airdrop SOL
Request airdrop of SOL to your account:

```sh
solana airdrop 1
```

## Creating SPL Tokens
### Create a new SPL token:
```sh 
spl-token create-token
```
### Create an SPL Token Account
Create an account to store the token balance:
```sh
spl-token create-account <token-identifier>
```
### Mint SPL Tokens
Mint tokens into the created account:

```sh
spl-token mint <token-identifier> <token-amount>
```
### Check the total supply of the token:
```sh
spl-token supply <token-identifier>
```
### Check the balance of the token:

```sh
spl-token balance <token-identifier>
```

## Creating SPL NFTs
### Create the NFT Token
Create a new SPL token for NFTs with 0 decimals:
```sh
spl-token create-token --decimals 0
```
### Create an Account for the NFT
Create an account to store the NFT balance:

```sh
spl-token create-account <token-identifier>
```
### Mint an NFT
Mint a single NFT into the created account:
```sh
spl-token mint <token-identifier> 1 <token-account>
```
### Disable Future Minting
Disable further minting of the NFT:

```sh
spl-token authorize <token-identifier> mint --disable
```
### SPL Token Transfer
Send tokens to another account:
```sh
spl-token transfer --fund-recipient <token-identifier> 10000 <accountA-pubKey>
```
