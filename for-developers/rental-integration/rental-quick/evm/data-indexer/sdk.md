---
description: StreamNFT SDK rental integration
---

# SDK

> * Main Net SDK: [https://www.npmjs.com/package/streamnft-evm](https://www.npmjs.com/package/streamnft-evm)
> * Test Net SDK: [https://www.npmjs.com/package/streamnft-evm-test](https://www.npmjs.com/package/streamnft-evm-test)

* Get all rented collection NFTs by user wallet

```javascript
const streamNFT = require('streamnft-evm');

let nfts= indexerCall(wallet.address) // indexer call to get nfts by wallet
nfts.push.apply(nfts, await streamNFT.getNFTs(chainId,wallet.address));
```

* Get all rented NFTs by user wallet

```javascript
const streamNFT = require('streamnft-evm');

let nfts= indexerCall(wallet.address) // indexer call to get nfts by wallet
nfts.push.apply(nfts, await streamNFT.getNFTs(chainId,wallet.address));
```
