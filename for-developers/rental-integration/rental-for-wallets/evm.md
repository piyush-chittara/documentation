# EVM

To integrate the SDK with your repository, follow the steps below. The following code snippets provide examples of how to use the SDK functions to interact with the smart contract.

```
Testnet SDK: streamnft-evm-test
Mainnet SDK: streamnft-evm
```

**1. Get Rented NFTs By Wallet:**

To retrieve the details of a specific user asset, you can use the following function:

* Specify the user's public address and the index of the user asset.
* Provide the chainId&#x20;

```javascript
const stream = require('streamnft-evm-test');

stream.getRentedNFTs(wallet.address, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

Example Response:

<pre class="language-json"><code class="lang-json"><strong>{ success: true, data:
</strong>  [
    {
      "rentee": "0x000000000000000000000000000000000020e8fe",
      "rent_expiry": "1710344564",
      "initializer": "0x00000000000000000000000000000000003621e2",
      "state": "RENT",
      "token_address": "0x000000000000000000000000000000000030b248",
      "token_id": "46"
    },
    {
      "rentee": "0x000000000000000000000000000000000020e8fe",
      "rent_expiry": "1709029643",
      "initializer": "0x000000000000000000000000000000000020e8fe",
      "state": "RENT",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "6"
    }
  ]
}
</code></pre>

\
Executing this code will fetch the details of the user asset associated with the provided user address. The result will contain information such as the asset's token address, token ID, and other relevant details pertaining to the asset rental.

**2. Get Rented NFTs By Wallet And Collection:**

To retrieve the details of a specific user asset, you can use the following function:

* Specify the user's public address and the index of the user asset.
* Provide the chainId&#x20;

```javascript
const stream = require('streamnft-evm-test');

stream.getRentedNFTs(wallet.address, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

Example Response:

```json
{ success: true, data:
  [
    {
        "rentee": "0x000000000000000000000000000000000020e8fe",
        "rent_expiry": "1710344564",
        "initializer": "0x00000000000000000000000000000000003621e2",
        "state": "RENT",
        "token_address": "0x000000000000000000000000000000000020e948",
        "token_id": "46"
      },
      {
        "rentee": "0x000000000000000000000000000000000020e8fe",
        "rent_expiry": "1709029643",
        "initializer": "0x000000000000000000000000000000000020e8fe",
        "state": "RENT",
        "token_address": "0x000000000000000000000000000000000020e948",
        "token_id": "6"
      }
  ]
}
```

```json
{ success: false, data: <error>}
```

Executing this code will fetch the details of the user asset associated with the provided user address and collection. The result will contain information such as the asset's token address, token ID, and other relevant details pertaining to the asset rental.\


**3. Initialize Rent for a Specific Asset:**

To initiate a rent for a specific asset, you can use the following function:

* Provide the token address of the asset, the token ID, and other required parameters such as the rate per minute, validity duration, fixed/variable rent, owner share, and whitelist.
* Specify the chainId and signer information.

```javascript
const stream = require('streamnft-evm-test');

const tokenAddress = "TOKEN_ADDRESS";
const tokenId = "TOKEN_ID";
const ratePerMinute = 10;
const validityMinutes = 60;
const isFixed = false;
const fixedMinutes = 0;
const doMint=false; // receipt type: smart registry, true=> mint wrapped token
const ownerShare = 80; // in percentage
const whitelist = []; // Array of whitelisted addresses

stream.lendToken(
  tokenAddress,
  tokenId,
  ratePerMinute,
  validityMinutes,
  isFixed,
  fixedMinutes,
  doMint,
  ownerShare,
  whitelist,
  chainId,
  signer
)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

**Example Response:**

```json
{ success: true, data: <index>}
```

```json
{ success: false, data: <error>}
```

\
\
**4. Get Asset Manager Details:**

To retrieve the asset manager details for a specific token, you can use the following function:

* Provide the token address and token ID of the asset.
* Specify the chainId&#x20;

<pre class="language-javascript"><code class="lang-javascript">const stream = require('streamnft-evm-test');

const tokenAddress = "TOKEN_ADDRESS";
const tokenId = "TOKEN_ID";
<strong>stream.getAssetManager(tokenAddress, tokenId, chainId)
</strong>  .then((result) => {
    // Handle the result (asset manager details)
  })
  .catch((error) => {
    // Handle the error
  });
</code></pre>

Executing this code will fetch the asset manager details for the specified token. Ensure that you provide the correct token address and token ID corresponding to the asset you want to retrieve information for. The result will contain relevant details about the asset manager, which can be further processed or displayed as needed in your application.

**Example Response:**

```json
{ success: true, data: 
    {
      "id": 240,
      "initializer": "0x000000000000000000000000000000000009be43",
      "loan_pool_index": "4",
      "loan_offer_index": "9",
      "state": "PRE_LOAN",
      "loan_expiry": "1708598493",
      "provider": "0x000000000000000000000000000000000009be43",
      "rate": null,
      "validity_expiry": null,
      "is_fixed": null,
      "fixed_minutes": null,
      "rent_expiry": null,
      "rentee": null,
      "private_rental": null,
      "owner_share": null,
      "whitelist": null,
      "chain_id": "296",
      "contract_address": "0xeB90f41DeAAe8D3Af051196E280ECfD2fedC293e",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "1",
      "metadata_uri": "QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "metadata_link": "https://hashpack.b-cdn.net/ipfs/QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "name": "SIWAS by Kabila",
      "image": "https://hashpack.b-cdn.net/ipfs/QmXJqZH6NMaJh9LfLTn2SPkPVnf4LBs2RaHfrUqBnpnSrc",
      "profit": null,
      "rental_type": null,
      "domint": null,
      "loan_expiry_utc": null,
      "rent_expiry_utc": null,
      "validity_expiry_utc": null,
      "loan_amount": "1200000000",
      "tx_hash": null,
      "version": null,
      "ERC1155_index": null,
      "index": null
    }
}
```

```json
{ success: false, data: <error>}
```

**5. Process a Rent for a Specific Asset:**

To initiate a rental process for a specific asset, you can utilize the following function:

* Provide the token address and token ID of the asset.
* Specify the duration of the rent in minutes.
* Specify the chainId and signer information.

```javascript
const stream = require('streamnft-evm-test');

const tokenAddress = "TOKEN_ADDRESS";
const tokenId = "TOKEN_ID";
const durationMinutes = 120;

stream.stream.processRent(tokenAddress, tokenId, durationMinutes, chainId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

Executing this code will trigger the rental process for the specified asset. Ensure that you provide the correct token address and token ID corresponding to the asset you want to initiate the rent for. Set the desired duration of the rent in minutes. The result will indicate the success of the rental process, and you can handle it accordingly in your application.



**6. Expire a Rent for a Specific Asset:**

To expire a rent for a specific asset, you can use the following function:

* Provide the token address and token ID of the asset for which you want to expire the rent.
* Specify the chainId and signer information.

```javascript
const stream = require('streamnft-evm-test');

const tokenAddress = "TOKEN_ADDRESS";
const tokenId = "TOKEN_ID";

stream.expireRent(tokenAddress, tokenId, chainId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

By executing this code, you initiate the process to expire the rent for the specified asset. Make sure to provide the correct token address and token ID corresponding to the asset you want to expire the rent for. The result will indicate the successful expiration of the rent, and you can handle it accordingly in your application logic.

**Example Response:**

```json
{ success: true, data: }
```

```json
{ success: false, data: <error>}
```



**7. Cancel a Rent for a Specific Asset:**

To cancel a rent for a specific asset, you can use the following function:

* Provide the token address and token ID of the asset for which you want to cancel the rent.
* Specify the chainId and signer information.

<pre class="language-javascript"><code class="lang-javascript">const stream = require('streamnft-evm-test');

<strong>const tokenAddress = "TOKEN_ADDRESS";
</strong>const tokenId = "TOKEN_ID";

stream.cancelRent(tokenAddress, tokenId, chainId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
</code></pre>

By executing this code, you initiate the process to cancel the rent for the specified asset. Make sure to provide the correct token address and token ID corresponding to the asset you want to cancel the rent for. The result will indicate the successful cancellation of the rent, and you can handle it accordingly in your application logic.

**Example Response:**

```json
{ success: true, data: }
```

```json
{ success: false, data: <error>}
```

8. **Get Assets by collection**

```javascript
const stream = require('streamnft-evm-test');

const tokenAddress = "TOKEN_ADDRESS";

stream.getAssetsByCollection(tokenAddress, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

By executing this code, you get all all assets for provided collection

**Example Response:**

```json
{ success: true, data: [
    {
      "id": 240,
      "initializer": "0x000000000000000000000000000000000009be43",
      "loan_pool_index": "4",
      "loan_offer_index": "9",
      "state": "PRE_LOAN",
      "loan_expiry": "1708598493",
      "provider": "0x000000000000000000000000000000000009be43",
      "rate": null,
      "validity_expiry": null,
      "is_fixed": null,
      "fixed_minutes": null,
      "rent_expiry": null,
      "rentee": null,
      "private_rental": null,
      "owner_share": null,
      "whitelist": null,
      "chain_id": "296",
      "contract_address": "0xeB90f41DeAAe8D3Af051196E280ECfD2fedC293e",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "1",
      "metadata_uri": "QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "metadata_link": "https://hashpack.b-cdn.net/ipfs/QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "name": "SIWAS by Kabila",
      "image": "https://hashpack.b-cdn.net/ipfs/QmXJqZH6NMaJh9LfLTn2SPkPVnf4LBs2RaHfrUqBnpnSrc",
      "profit": null,
      "rental_type": null,
      "domint": null,
      "loan_expiry_utc": null,
      "rent_expiry_utc": null,
      "validity_expiry_utc": null,
      "loan_amount": "1200000000",
      "tx_hash": null,
      "version": null,
      "ERC1155_index": null,
      "index": null
    },
    {
      "id": 267,
      "initializer": "0x000000000000000000000000000000000037d1f6",
      "loan_pool_index": "1",
      "loan_offer_index": "1",
      "state": "LOAN",
      "loan_expiry": "1709828808",
      "provider": "0x000000000000000000000000000000000020e8fe",
      "rate": "0",
      "validity_expiry": null,
      "is_fixed": false,
      "fixed_minutes": "0",
      "rent_expiry": "0",
      "rentee": "0x0000000000000000000000000000000000000000",
      "private_rental": null,
      "owner_share": "0",
      "whitelist": "",
      "chain_id": "296",
      "contract_address": "0xeB90f41DeAAe8D3Af051196E280ECfD2fedC293e",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "51",
      "metadata_uri": "QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "metadata_link": "https://hashpack.b-cdn.net/ipfs/QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "name": "SIWAS by Kabila",
      "image": "https://hashpack.b-cdn.net/ipfs/QmXJqZH6NMaJh9LfLTn2SPkPVnf4LBs2RaHfrUqBnpnSrc",
      "profit": "0",
      "rental_type": null,
      "domint": null,
      "loan_expiry_utc": null,
      "rent_expiry_utc": null,
      "validity_expiry_utc": null,
      "loan_amount": "10000000000",
      "tx_hash": null,
      "version": null,
      "ERC1155_index": null,
      "index": null
    }
]}
```

```json
{ success: false, data: <error>}
```

8. **Get Assets by collection and wallet**

```javascript
const stream = require('streamnft-evm-test');

const tokenAddress = "TOKEN_ADDRESS";
const wallet = "USER_WALLET_ADDRESS";
stream.getAssetsByUserAndCollection(wallet, tokenAddress, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

By executing this code, you get all all assets for provided collection and user\


**Example Response:**

```json
{ success: true, data: [
    {
      "id": 240,
      "initializer": "0x000000000000000000000000000000000009be43",
      "loan_pool_index": "4",
      "loan_offer_index": "9",
      "state": "PRE_LOAN",
      "loan_expiry": "1708598493",
      "provider": "0x000000000000000000000000000000000009be43",
      "rate": null,
      "validity_expiry": null,
      "is_fixed": null,
      "fixed_minutes": null,
      "rent_expiry": null,
      "rentee": null,
      "private_rental": null,
      "owner_share": null,
      "whitelist": null,
      "chain_id": "296",
      "contract_address": "0xeB90f41DeAAe8D3Af051196E280ECfD2fedC293e",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "1",
      "metadata_uri": "QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "metadata_link": "https://hashpack.b-cdn.net/ipfs/QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "name": "SIWAS by Kabila",
      "image": "https://hashpack.b-cdn.net/ipfs/QmXJqZH6NMaJh9LfLTn2SPkPVnf4LBs2RaHfrUqBnpnSrc",
      "profit": null,
      "rental_type": null,
      "domint": null,
      "loan_expiry_utc": null,
      "rent_expiry_utc": null,
      "validity_expiry_utc": null,
      "loan_amount": "1200000000",
      "tx_hash": null,
      "version": null,
      "ERC1155_index": null,
      "index": null
    },
    {
      "id": 267,
      "initializer": "0x000000000000000000000000000000000009be43",
      "loan_pool_index": "1",
      "loan_offer_index": "1",
      "state": "LOAN",
      "loan_expiry": "1709828808",
      "provider": "0x000000000000000000000000000000000020e8fe",
      "rate": "0",
      "validity_expiry": null,
      "is_fixed": false,
      "fixed_minutes": "0",
      "rent_expiry": "0",
      "rentee": "0x0000000000000000000000000000000000000000",
      "private_rental": null,
      "owner_share": "0",
      "whitelist": "",
      "chain_id": "296",
      "contract_address": "0xeB90f41DeAAe8D3Af051196E280ECfD2fedC293e",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "51",
      "metadata_uri": "QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "metadata_link": "https://hashpack.b-cdn.net/ipfs/QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "name": "SIWAS by Kabila",
      "image": "https://hashpack.b-cdn.net/ipfs/QmXJqZH6NMaJh9LfLTn2SPkPVnf4LBs2RaHfrUqBnpnSrc",
      "profit": "0",
      "rental_type": null,
      "domint": null,
      "loan_expiry_utc": null,
      "rent_expiry_utc": null,
      "validity_expiry_utc": null,
      "loan_amount": "10000000000",
      "tx_hash": null,
      "version": null,
      "ERC1155_index": null,
      "index": null
    }
]}
```

```json
{ success: false, data: <error>}
```

9. **Get User Asset Details:**

To retrieve the details of a specific user asset, you can use the following function:

* Specify the user's public address and the index of the user asset.
* Provide the chainId&#x20;

```javascript
const stream = require('streamnft-evm-test');

const userAddress = "USER_PUBLIC_KEY";

stream.getAssestsByUser(userAddress, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```

**Example Response:**

```json
{ success: false, data: <error>}
```

```json
{ success: true, data: [
    {
      "id": 240,
      "initializer": "0x000000000000000000000000000000000009be43",
      "loan_pool_index": "4",
      "loan_offer_index": "9",
      "state": "PRE_LOAN",
      "loan_expiry": "1708598493",
      "provider": "0x000000000000000000000000000000000009be43",
      "rate": null,
      "validity_expiry": null,
      "is_fixed": null,
      "fixed_minutes": null,
      "rent_expiry": null,
      "rentee": null,
      "private_rental": null,
      "owner_share": null,
      "whitelist": null,
      "chain_id": "296",
      "contract_address": "0xeB90f41DeAAe8D3Af051196E280ECfD2fedC293e",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "1",
      "metadata_uri": "QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "metadata_link": "https://hashpack.b-cdn.net/ipfs/QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "name": "SIWAS by Kabila",
      "image": "https://hashpack.b-cdn.net/ipfs/QmXJqZH6NMaJh9LfLTn2SPkPVnf4LBs2RaHfrUqBnpnSrc",
      "profit": null,
      "rental_type": null,
      "domint": null,
      "loan_expiry_utc": null,
      "rent_expiry_utc": null,
      "validity_expiry_utc": null,
      "loan_amount": "1200000000",
      "tx_hash": null,
      "version": null,
      "ERC1155_index": null,
      "index": null
    },
    {
      "id": 267,
      "initializer": "0x000000000000000000000000000000000009be43",
      "loan_pool_index": "1",
      "loan_offer_index": "1",
      "state": "LOAN",
      "loan_expiry": "1709828808",
      "provider": "0x000000000000000000000000000000000020e8fe",
      "rate": "0",
      "validity_expiry": null,
      "is_fixed": false,
      "fixed_minutes": "0",
      "rent_expiry": "0",
      "rentee": "0x0000000000000000000000000000000000000000",
      "private_rental": null,
      "owner_share": "0",
      "whitelist": "",
      "chain_id": "296",
      "contract_address": "0xeB90f41DeAAe8D3Af051196E280ECfD2fedC293e",
      "token_address": "0x000000000000000000000000000000000020e948",
      "token_id": "51",
      "metadata_uri": "QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "metadata_link": "https://hashpack.b-cdn.net/ipfs/QmfDDKu2VhN9GMiYDdoQVZx7wkAp9gRdvJkxBMeJgHehpS",
      "name": "SIWAS by Kabila",
      "image": "https://hashpack.b-cdn.net/ipfs/QmXJqZH6NMaJh9LfLTn2SPkPVnf4LBs2RaHfrUqBnpnSrc",
      "profit": "0",
      "rental_type": null,
      "domint": null,
      "loan_expiry_utc": null,
      "rent_expiry_utc": null,
      "validity_expiry_utc": null,
      "loan_amount": "10000000000",
      "tx_hash": null,
      "version": null,
      "ERC1155_index": null,
      "index": null
    }
]}
```

\
Executing this code will fetch the details of the user asset associated with the provided user address. The result will contain information such as the asset's token address, token ID, and other relevant details pertaining to the user asset.

{% hint style="info" %}
Make sure to replace the placeholders (TOKEN\_ADDRESS, TOKEN\_ID, USER\_PUBLIC\_KEY, etc.) with the actual values specific to your use case.
{% endhint %}

These examples demonstrate how to use the SDK functions to interact with the smart contract. You can integrate them into your application logic and handle the results and errors accordingly.
