# Token Gated Matchmaking

Ways to enable token gated matchmaking with tokens as NFT rewards:\
\
1\. ERC721: tokens are moved to an escrow account, afterwards a match room is created. Tokens are moved to match winners after match completion.\
\
2\. [ERC7066](https://eips.ethereum.org/EIPS/eip-7066): tokens are locked in user wallets to create a match room and transferred to the match winner.

{% hint style="success" %}
Added advantage of using ERC7066 is project access to integration-less [NFT liquidity solutions](broken-reference) requiring **0 dev efforts**.
{% endhint %}



Steps:\


1. Get signer

```javascript
// function to get user signer from wallet
user.signer=streamSDK.getWalletSigner()
```

```javascript
// function to get user signer from privatekey
user.signer=streamSDK.getSigner(privateKey)
```

2. Join room

```javascript
// function to create/join a room
// @param user.id is userId of player
// @param user.address user wallet address
// @param tokenAddress contract address of NFT
// @param tokenId token Id owned by user
// @param user.signer provides a wallet instance to sign txn
// @param roomSize number of players needed to create a room
// @returns userId of winner
await streamSDK.joinRoom(user.id, user.address, tokenAddress, tokenId, user.signer, roomSize) returns {roomId,userId}
```

3. Claim match reward

```javascript
// function to share winnings to winner
// @param roomId roomId of match
// @param user.address user wallet address
await streamSDK.winnerClaim(roomId, user.address);
```
