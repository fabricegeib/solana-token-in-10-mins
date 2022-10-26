# Introduction

## Understanding Solana Network

Solana is a blockchain platform that enables the hosting of decentralized, scalable apps. It was established in 2017 and is an open-source project that is now managed by the Geneva-based Solana Foundation.

The Solana blockchain uses the proof-of-history consensus algorithm. The following block in Solana's chain is determined by this algorithm using timestamps. Solana also uses Delegated proof-of-stake in combination with PoH as its consensus.

Proof of History is based on Proof of Stake but uses a separate clock to measure time. Today, historical occurrences are employed to estimate the passage of time. These occurrences are converted into a hash that can only be produced by earlier occurrences.

## Setting up your environment

Installer Rust : https://rustup.rs/

Vérifier l'installation :

```shell
cargo --version

# cargo 1.64.0 (387270bc7 2022-09-16)
```

Cargo est une sorte d'installateur (NPM ou Yarn) pour Rust.

Installer Solana Tool Suite : https://docs.solana.com/cli/install-solana-cli-tools

Puis ajouter cette ligne dans votre PATH (.zshrc) :

```shell
# Please update your PATH environment variable to include the solana programs:

PATH="/Users/fabricegeib/.local/share/solana/install/active_release/bin:$PATH"
```

Vérifier l'installation :

```shell
solana --version

# solana-cli 1.14.6 (src:cfb2cbe1; feat:2390042548)
```

# Let’s Code

## Using SPL-CLI

```shell
# install the SPL-Token-CLI
cargo install spl-token-cli

# generate a new wallet which we will be using to interact with Solana Devnet

solana-keygen new --no-outfile

# network configuration

solana config get

# Output of solana config get
# Config File: /Users/fabricegeib/.config/solana/cli/config.yml
# RPC URL: https://api.devnet.solana.com
# WebSocket URL: wss://api.devnet.solana.com/ (computed)
# Keypair Path: /Users/fabricegeib/.config/solana/id.json
# Commitment: confirmed

solana airdrop 1

solana balance

# Error: Dynamic program error: No default signer found, run "solana-keygen new -o /Users/fabricegeib/.config/solana/id.json" to create a new one
```

# Deployment

## Deploy your SPL Token and mint it

```shell
spl-token create-token

# Creating token 7rQZEPLkjp5mSDs8t43VmU9hZAqyWXNiPnUnF7BWj24P
# Address:  7rQZEPLkjp5mSDs8t43VmU9hZAqyWXNiPnUnF7BWj24P
# Decimals:  9
# Signature: 4y1WnqEHtj5VqoMomytWYnqQPqsVdPh3mZBLW5CV2THJgSygLLMJvRKinbRD9gi7oc32BQcH7hUhhhAtAa9zvfTu

spl-token create-account <TOKEN_ADDRESS>

# Creating account 52SP9atSREKoEfAxRjXcaAs3zibXURzJJpg6mzttV4qm
# Signature: 4ZeujZZbHv1U2djC6gTXdbPLX57LiZrXvz3muYBtkaDipahWaHCxvfkarJTZ89aNwP6NuSXqJv3ztpJiupY61VRv

spl-token mint <token-address> <token-amount>

# Minting 1000000 tokens
# Token: 7rQZEPLkjp5mSDs8t43VmU9hZAqyWXNiPnUnF7BWj24P
# Recipient: 52SP9atSREKoEfAxRjXcaAs3zibXURzJJpg6mzttV4qm
# Signature: 4VrSQAzW6Y1bAzgBbML1gpwpvngEnm574SKS2kf7BwjpKUyQ4RN4ZbuvQJpn7Zoa6M4bQRELsTBRAR5jKPUUVPxE

solana balance

# 0.99647912 SOL
```

https://explorer.solana.com/supply?cluster=devnet

https://explorer.solana.com/address/7rQZEPLkjp5mSDs8t43VmU9hZAqyWXNiPnUnF7BWj24P?cluster=devnet

## Deploy on mainnet

Il faut changer la configuration :

```shell
solana config set --url <https://api.mainnet-beta.solana.com>
```
