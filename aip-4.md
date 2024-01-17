---
title: 4
description: Add ARweave Protocol support to URN and implement compatibility with DMint
author: okayama.shatoshi@gmail.com
discussions-to: <URL>
status: Draft
type: Standards 
category: Core, Interface
created: 2024-1-18
---

## Abstract

This proposal introduces support for Atomicals URN on the Arweave Protocol and the implementation of compatibility with the Atomicals.js Dmint CLI interface and API.

The main implementation involves the decoupling of Atomicals Meta information (on Bitcoin) from the storage of large NFT image/video data (on Arweave), which alleviates the application restrictions caused by the high Gas fees on Bitcoin, and expands the applicability of the Atomicals protocol.

This protocol can serve as a generic implementation for Atomicals supporting multiple storage protocols (such as IPFS, DA/ETH, or even AWS), where these storage protocol URNs can be listed in an array to implement a simple backup mechanism.

## Motivation

Atomicals is an overlay protocol on Bitcoin, operating on the theory of colored coins and sharing Bitcoin addresses and UTXOs, with all its data stored on the Bitcoin blockchain. This presents a significant advantage as all application data benefit from the high security and data distribution capabilities of the Bitcoin network. However, it also imposes a significant burden. Since Bitcoin was designed for P2P electronic cash transactions, its storage costs are prohibitively high, making it impractical to store high-definition images. This cost is unaffordable for both creators and users, which is why current applications are limited to pixel-art style NFTs.

By decoupling Atomicals' application metadata from instance data and anchoring and verifying it through a Merkle tree and hashes, we can eliminate the current storage restrictions of the Atomicals protocol. This will significantly broaden the innovation and application scope of the Atomicals protocol.

## Specification

- **Arweave URN Plugin**
Currnetly the convention is to use the prefix "atom:btc" to indicate the Atomicals Protocol on the Bitcoin (BTC) network. It is possible to reference digital objects by atomical_id, container name, or (sub)realms and immutable file data by the data_id.
The basic form of the  Atomicals Universal Resource Name (URN)  is:
atom:<chain>:<ref_type>:<identifier>[$ or /[<file>]]

The Arweave protocol extended  form of Atomicals Universal Resource Name (URN)  is：
atom:<chain>:<ref_type>:<identifier>[$ or /[<file>]]

Where:
Chain: The referenced blockchain, When we extend it to support arweave, we set it to "AR" 

ref_type: The type of reference, When Chain seted to "AR" , supported Options : "url", "urls"

identifier: The identifier corresponding to the ref_type. Such as a url string "ar://abc.com",  or the urls array include 豆号分隔的多条url.

$ or /: Whether to refer to the mint (original) data (using dollar sign $) or the dynamic (latest) data (using slash /) of a file for an Atomical, . 

When Chain is “AR”，You will notice that for the dat ref_type either $ or / is acceptable and will return the same data regardless.

file: The name of the file is optional, if omitted then general information about the resource is returned

- **Arweave Cli Support**

Regarding the compatibility of the Atomicals.js command line, we introduce a parameter --chain="ar" to implement specific support for the Arweave protocol，like bellow：

  $ yarn cli validate-container-item "#container-name" "test-item-3" "path/to/item-3.json" --chain="ar"


## Backwards Compatibility

No backward compatibility issues found.


## Reference Implementation

To know about the implementation, head over to
[atomicals-ar](https://github.com/okayama-shatoshi/atomcials-ar)
for use cases and the source.

TBD


## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).
