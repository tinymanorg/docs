---
description: A basic overview of the Tinyman AMM
---

# Tinyman AMM Basics

## Overview

Tinyman is a decentralised exchange (DEX) on Algorand. More specifically it is an Automated Market Maker (AMM) exchange employing the Constant Product Market Maker algorithm. This is the same concept pioneered by Uniswap V2.

The web based app (`app.tinyman.org`) is a visual interface for interacting with a set of smart contracts deployed to the Algorand blockchain.&#x20;

The exchange is fully **decentralized** and **non custodian**. Funds are held in permissionless smart contract accounts. This means the only methods to withdraw funds from the pool accounts are those encoded in the smart contract. At a high level this code only allows withdrawals in exchange for an appropriate amount of another asset or by the liquidity owners in exchange for their Pool Tokens.&#x20;

Furthermore the contracts are fully **permissionless**. This means that any account can create a pool by issuing the correct set of transactions. It means that no account has authority over the pool's assets or functionality. This also means there is _no mechanism to revert or adjust transactions even if they are made in error._

The contracts are also fully **immutable**. This means no account has the authority to update or delete the contracts that control the pools. This means that funds cannot be stolen by an update to the contracts.
