---
description: Integrate Utility protocol within your wallet/project/ecosystem
---

# Advanced Integration

To integrate the SDK with your repository, follow the steps below. The following code snippets provide examples of how to use the SDK functions to interact with the smart contract.

Testnet SDK: [streamnft-utility-test ](https://www.npmjs.com/package/streamnft-utility-test)\
Mainnet SDK: streamnft-evm (TBA)

```javascript
const stream = require('streamnft-utility-test');

//for browser wallets
signer = stream.getWalletSigner();  

//for signer using private key  
signer= stream.getSigner(chainId, privateKey, rpcUrl);    
```

\
1\.  Create Utility\
\
Create Utility on any NFT collection

* create utility schema with UtilitySchema

<details>

<summary>UtilitySchema</summary>

```json
{
  "utilityId": {
    "type": "String",
    "required": true,
    "unique": true
  },
  "utilityIndex": "Number",
  "provider": "String",
  "winners": [
    "String"
  ],
  "participants": [
    "String"
  ],
  "chainId": "Number",
  "utilityType": {
    "type": "String",
    "required": true
  },
  "usage": {
    "expiryOrUsage": "Number",
    "startOnClaim": "Boolean"
  },
  "raffle": {
    "totalEntries": {
      "type": "Number",
      "default": 0
    },
    "participants": [
      "String"
    ],
    "winners": [
      "String"
    ],
    "maxEntries": "Number",
    "winnersMerkle": "String",
    "claimDate": "Date"
  },
  "target": [
    {
      "collection": "String",
      "chainId": "String",
      "name": "String",
      "eligibleType": {
        "type": "String",
        "required": true
      },
      "traits": [
        {
          "key": "String",
          "value": "String"
        }
      ]
    }
  ],
  "eligible": {
    "type": "Map",
    "of": {
      "eligibleType": {
        "type": "String",
        "required": true
      },
      "participants": [
        "String"
      ],
      "externalService": {
        "type": "String"
      },
      "traits": [
        {
          "key": "String",
          "value": "String"
        }
      ],
      "numberOfEntries": "Number",
      "collectionImage": "String",
      "collectionName": "String",
      "chainId": "String",
      "collectionAddress": "String",
      "taskDetails": [
        {
          "taskInfo": "String",
          "serviceTarget": "String",
          "targetURL": "String",
          "numberOfEntries": "Number",
          "mandatory": "Boolean"
        }
      ]
    },
    "default": {}
  },
  "partner": "String",
  "selectionType": {
    "type": "String",
    "required": true
  },
  "title": "String",
  "category": "String",
  "image_url": "String",
  "reward": {
    "value": "String",
    "estimatedValue": "String",
    "mintPrice": "Number",
    "details": [
      "String"
    ],
    "image": "String",
    "type": {
      "type": "String",
      "required": true
    },
    "currency": {
      "type": "String",
      "default": "USD"
    },
    "count": "Number",
    "expiry": "String",
    "chainId": "Number",
    "secret": {
      "value": "String",
      "details": [
        {
          "value": "String",
          "claimed": "Boolean"
        }
      ]
    },
    "congratulationText": "String"
  },
  "createdAt": "Date",
  "description": "String",
  "startDate": "Date",
  "endDate": "Date"
}
```

</details>

```javascript
const stream = require('streamnft-utility-test');

stream.createUtility(utility, chainId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

This shall return index of utility created: utilityId

```javascript
{success:true, data: <index> (int)}
```

2. Get All Utility By Collection&#x20;

Get Utilities present on a collection

```javascript
const stream = require('streamnft-utility-test');

stream.getAllUtilityByCollection(collectionAddress)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

3. Get All Utility By User

Get all Utilities accessible to a wallet

```javascript
const stream = require('streamnft-utility-test');

stream.getAllUtilityByUser(wallet, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

4. Join Raffle

Join Raffle Type Utility

```javascript
const stream = require('streamnft-utility-test');

stream.joinRaffle(chainId, utilityId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

5. Claim Reward

Claim reward for giveaways utilities

```javascript
const stream = require('streamnft-utility-test');

stream.claimReward(chainId, utilityId, user, proof, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

6. Claim Utility On NFT

Claim NFT benefit utility

```javascript
const stream = require('streamnft-utility-test');

stream.claimUtilityOnNFT(user, tokenId, utilityId, proof, chainId,signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

7. Redeem Utility On NFT

Redeem NFT benefit utility

```javascript
const stream = require('streamnft-utility-test');

stream.redeemUtilityOnNFT(tokenId, utilityId, chainId,signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

8. Check  NFT utility

Check if NFT is valid for any utility

```javascript
const stream = require('streamnft-utility-test');

stream.checkNFTUtility(tokenId, utilityId, chainId, provider)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```
