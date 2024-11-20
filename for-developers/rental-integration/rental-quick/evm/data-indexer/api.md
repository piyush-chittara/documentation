---
description: Stream NFT API rental integration
---

# API

The Asset Manager API provides functionalities for managing asset managers in a blockchain-based ecosystem. Asset managers are entities responsible for managing various assets, such as digital tokens, NFTs (Non-Fungible Tokens), and other digital assets, on a blockchain network. These APIs allows users to retrieve information about asset managers based on their chain ID and contract address.

**Endpoint:**

> * Main Net Base URL: [https://indexer.streamnft.tech/](https://indexer.streamnft.tech/)
> * Test Net Base URL: [https://stagingindexer.streamnft.tech/](https://stagingindexer.streamnft.tech/)



1. **Use StreamNFT Indexer (1 API Call to get all User NFTs)**

{% swagger src="../../../../../.gitbook/assets/openapi 3 (1).yml" path="/getNFTs/{chainId}/{wallet}" method="get" %}
[openapi 3 (1).yml](<../../../../../.gitbook/assets/openapi 3 (1).yml>)
{% endswagger %}

2. **Use External Indexer (2 API Call to get all User NFTs)**

_Query Parameters specific for rentals_**:**

* `collection`: Filter for token address of the NFT collection
* `rentee`: Filter for assets rented by a wallet
* `state`: Filter for all assets on Marketplace (STALE) or rented out (RENT)
* `onlyRentData` : Output only rental data (NFT rentee, NFT owner,  rental expiry, state)

{% swagger src="../../../../../.gitbook/assets/openapi.yml" path="/assetManager/{chainId}" method="get" %}
[openapi.yml](../../../../../.gitbook/assets/openapi.yml)
{% endswagger %}

**Response:**

* Successful responses return an array of asset managers for provided token address with detailed information, such as the current rentee and the state of each asset.

### Example: How to Integrate

* Get all rented collection NFTs by user wallet

```javascript
let nfts= indexerCall(wallet.address) // indexer call to get nfts by wallet
nfts.push.apply(nfts, await getNFTs(chainId,wallet.address,tokenAddress));

async function getNFTs(chainId, address,tokenAddress){
    const nfts = await fetch(`https://indexer.streamnft.tech/assetManager/${chainId}?user=${walletAddress}&collection=${collectionAddress}`)
    .then(response => {
        if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
        }
        return response.json();
    })
    .catch(error => {
        // Handle network errors or API response errors here
        console.error('Error:', error.message);
    });
    return nfts;
}
```

* Get all rented NFTs by user wallet

```javascript
let nfts= indexerCall(wallet.address) // indexer call to get nfts by wallet
nfts.push.apply(nfts, await getNFTs(chainId,wallet.address));

async function getNFTs(chainId, address){
    const nfts = await fetch(`https://indexer.streamnft.tech/assetManager/${chainId}?user=${walletAddress}`)
    .then(response => {
        if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
        }
        return response.json();
    })
    .catch(error => {
        // Handle network errors or API response errors here
        console.error('Error:', error.message);
    });
    return nfts;
}
```
