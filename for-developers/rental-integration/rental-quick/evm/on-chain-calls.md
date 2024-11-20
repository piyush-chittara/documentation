# On-Chain calls

If your project uses on-chain calls for `token owner`, replace them with streamNFT contract calls using the streamNFT ABI

<details>

<summary>StreamNFT ABI for NFT State calls</summary>

```json
[
  {
    "inputs": [
      {
        "internalType": "uint256",
        "name": "tokenId",
        "type": "uint256"
      }
    ],
    "name": "ownerOf",
    "outputs": [
      {
        "internalType": "address",
        "name": "",
        "type": "address"
      }
    ],
    "stateMutability": "view",
    "type": "function"
  },
  {
    "inputs": [
      {
        "internalType": "address",
        "name": "tokenAddress",
        "type": "address"
      },
      {
        "internalType": "uint256",
        "name": "tokenId",
        "type": "uint256"
      },
      {
        "internalType": "address",
        "name": "user",
        "type": "address"
      }
    ],
    "name": "balanceOf",
    "outputs": [
      {
        "internalType": "uint256",
        "name": "",
        "type": "uint256"
      }
    ],
    "stateMutability": "view",
    "type": "function"
  },
  {
    "inputs": [
      {
        "internalType": "address",
        "name": "tokenAddress",
        "type": "address"
      },
      {
        "internalType": "address",
        "name": "user",
        "type": "address"
      }
    ],
    "name": "balanceOf",
    "outputs": [
      {
        "internalType": "uint256",
        "name": "",
        "type": "uint256"
      }
    ],
    "stateMutability": "view",
    "type": "function"
  }
]
```

</details>

1.  For ERC721 token, you need to update on-chain call with \


    ```javascript
    (ERC721) ownerOf(tokenId) -> (streamNFT) ownerOf(tokenAddress,tokenId)
    (ERC721) balanceOf(user) -> (streamNFT) balanceOf(tokenAddress,user)
    ```
2.  For ERC1155 token, you need to update on-chain call with&#x20;



    ```javascript
    (ERC1155) balanceOf(tokenId,user) -> (streamNFT) balanceOf(tokenAddress,tokenId,user)
    ```
