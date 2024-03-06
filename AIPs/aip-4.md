---
title: 4
description: Atomicals Container-X Specs (Add AR/IPFS Support For Container)
author:  <iamliqiang@gmail.com>, <okayama.shatoshi@gmail.com>
discussions-to: <URL>
status: Draft
type: Standards Track
category: Interface
created: 2024-1-18
---

## Abstract
**Container-X**, "X" represents expansion and cross-chain.
![Container-X](https://0xspace.oss-cn-beijing.aliyuncs.com/upic/20240306-containerx1.jpg)

The Container-X supports external on-chain storage solutions such as Arweave and IPFS, dramatically reducing Bitcoin (BTC) Dmint costs by 99%. It enables the storage of unlimited size high-definition (HD) images, videos, audio files, AI training data, and other high-value datasets. Additionally, Container-X makes it possible to construct a data exchange marketplace on the Bitcoin network ( powered by Atomicals Protocols.)



## Motivation

Atomicals is an overlay protocol on Bitcoin, operating on the theory of colored coins and sharing Bitcoin addresses and UTXOs, with all its data stored on the Bitcoin blockchain. This presents a significant advantage as all application data benefit from the high security and data distribution capabilities of the Bitcoin network. However, it also imposes a significant burden. Since Bitcoin was designed for P2P electronic cash transactions, its storage costs are prohibitively high, making it impractical to store high-definition images. This cost is unaffordable for both creators and users, which is why current applications are limited to pixel-art style NFTs.

By decoupling Atomicals' application metadata from instance data, and support data  index mapping on AR/IPFS protocol , we can eliminate the current storage restrictions of the Atomicals protocol Containers. This will significantly broaden the innovation and application scope of the Atomicals protocol.

## Specification

**Container-X implementation**

1. The Container-X is designed to store fingerprint thumbnail images at specific resolutions of 16x16, 32x32, and 64x64 pixels (these are all recommended values, you can specify your own).
2. The Dmint metadata JSON file will insert a new segment ”ext“ and include new AR or IPFS elements ( URLs ) that points to the original collection images (or any other data files) using an Ardrive manifest style. This method uses the same (fingerprint thumbnail & orginal files) NFT Token ID to uniquely index all images or files stored in a single directory on Arweave.
3. Marketplaces, wallets, and explorers that adopt the Container-X standard will be capable of displaying the original images or files located on the Arweave or IPFS networks.
4. This standard is a non-intrusive specs extension proposal that requires no modifications to the existing Container codebase. The functionalities and objectives of the proposal are realized exclusively through adherence to the Container-X standard. Additionally, it provides a unified path for compatibility and implementation for third-party atomicals Container-X applications (marketplaces, wallets, explorers, Nfts...etc.).
5. Container-X seamlessly integrates the Arweave and IPFS protocols with Atomicals, marking the first step in cross-chain expansion Atomicals ecosystem.

![Container-X Diagram](https://0xspace.oss-cn-beijing.aliyuncs.com/upic/20240306-containerx2.jpg)

**Container metadata JSON file example**
```json
{
    "name": "DragonCapsule",
    "desc": "Dark Skull DragonCapsule on Bitcoin",
    "image": "atom:btc:dat:f10473077bb06aed1b860356a7afb2a24265acf1f6d71a1037e1eb01a1d70180i0/logo.png",
    "legal": {
        "terms": "https://arweave.net/2om8up8MggA9XZJMgvTeENMJhhV6x5preREexjP-xL4/6",
        "license": "METAIP-COMMUNITY-NO-HATE"
    },
    "links": {
        "x": {
            "v": "https://x.com/atomicalsDragon"
        },
        "web": {
            "v": "https://dragoncapsule.xyz"
        }
    },
    "ext": {
        "ar": {
            "v": "ar://2om8up8MggA9XZJMgvTeENMJhhV6x5preREexjP-xL4"
        },
        "ipfs": {
            "v": "ipfs://QmeSjSinHpPnmXmspMjwiXyN6zS4E9zccariGR3jxcaWtq"
        }
    }
}
```

**Front Dapp Compatibility**

Note: In the JSON file mentioned above, the ar:// and ipfs:// protocols must be converted into specific Arweave or IPFS HTTPS gateway addresses within the front-end application (this specification utilizes the ar:// and ipfs:// protocols to ensure better compatibility with application implementations). For instance, in third-party front-end applications, the conversion would be as follows:

```json
    "ext": {
        "ar": {
            "v": "https://arweave.net/2om8up8MggA9XZJMgvTeENMJhhV6x5preREexjP-xL4"
        },
        "ipfs": {
            "v": "https://ipfs.io/ipfs/QmeSjSinHpPnmXmspMjwiXyN6zS4E9zccariGR3jxcaWtq"
        }
    }
```

## Backwards Compatibility
No backward compatibility issues found, and the Container-X is recommended as a new chapter to be added to the Collection containers section of the atomicals officials docs.

## FAQ and Reference Implementation

1. What is  Arweave Manifest and how to creat it ？
https://ardrive.io/manifest-demo/ 

2. Automating Thumbnail Generation with Tools ？
https://www.npmjs.com/package/@squoosh/cli

3. Container-x Deployment Guide （ Coming soon.....）
[Container-X Deploymnet Guide](https://github.com/okayama-shatoshi/containerx-guide)

TBD
## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).

