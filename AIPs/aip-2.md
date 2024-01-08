---
aip: 2
title: Address Standardization Proposal for Asset Identification (atom32)
status: Draft
type: Standards Track
category: Application
author: neeboo <@neeboo>.
created: 2024-1-8
---

## Abstract

This proposal introduces a standardized address format based on *bech32* encoding
to resolve asset identification challenges within the Bitcoin system,
particularly concerning the Atomicals Protocol.
The new address format aims to differentiate Atomicals Protocol assets from Bitcoin assets,
enabling node services to accurately identify and handle distinct asset types,
thus preventing unintended asset burning during transactions.

## Motivation

In the Bitcoin ecosystem, the Atomicals Protocol operates based on colored coin theory, sharing Bitcoin addresses and UTXOs.
This overlap leads to a critical issue: traditional node services cannot distinguish between assets from different protocols.
Consequently, during user transactions, assets might inadvertently be merged or burned due to insufficient UTXO differentiation.
This poses a significant risk to asset security and user confidence.

## Specification

### Problem Statement

- **Shared Address and UTXO**: Atomicals Protocol assets share addresses and UTXOs with Bitcoin, causing confusion and potential loss.
- **Lack of Asset Differentiation**: Traditional node services fail to differentiate between Bitcoin and Atomicals Protocol assets, leading to accidental asset burning.

### Proposed Solution

1. ***bech32* Address Format**: Implement a bech32-based address format specifically for Atomicals Protocol assets.
   This format will be distinct yet compatible with existing Bitcoin addresses.
2. **Asset Differentiation**: Indexing nodes will recognize and differentiate assets based on the new address format.
   This recognition extends to wallets, block explorers, and trading platforms, ensuring end-to-end asset distinction.

### Benefits

- **Enhanced Security**: Prevents accidental merging and burning of Atomicals Protocol assets.
- **Clear Asset Identification**: Enables node services, wallets, and other platforms to accurately identify and handle distinct asset types.
- **Ecosystem Support**: Encourages widespread adoption and support across wallets, block explorers, and trading platforms.

## Reference Implementation

To know about the implementation, head over to
[atom32](https://github.com/AstroxNetwork/atom32)
for use cases and the source.

## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).
