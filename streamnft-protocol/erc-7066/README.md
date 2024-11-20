---
description: Interface for enabling locking of ERC-721 using locker and approved
---

# ®️ ERC-7066

### Abstract <a href="#abstract" id="abstract"></a>

An extension of [ERC-721](https://eips.ethereum.org/EIPS/eip-721), this standard incorporates `locking` features into NFTs, allowing for various uses while preventing sale or transfer. The token’s `owner` can `lock` it, setting up locker address (either an EOA or a contract) that exclusively holds the power to unlock the token. Owner can also provide approval for tokenId, enabling ability to lock asset while address holds the token approval. Token can also be locked by `approved`, assigning locker to itself. Upon token transfer, these rights get purged.

### Backwards Compatibility <a href="#backwards-compatibility" id="backwards-compatibility"></a>

This standard is compatible with [ERC-721](https://eips.ethereum.org/EIPS/eip-721) standards.

Existing Upgradedable [ERC-721](https://eips.ethereum.org/EIPS/eip-721) can upgrade to this standard, enabling locking capability inherently and unlock underlying liquidity features.

### Motivation <a href="#motivation" id="motivation"></a>

[ERC-721](https://eips.ethereum.org/EIPS/eip-721) has sparked an unprecedented surge in demand for NFTs. However, despite this tremendous success, NFT economy suffers from secondary liquidity where it remains Illiquid in owner’s wallet. There are projects such as NFTfi, Paraspace which aims to address the liquidity challenge, but they entail below mentioned inconveniences and risks for owners as they necessitate transferring the participating NFTs to the projects’ contracts.

* **Loss of utility**: The utility value of NFTs diminishes when they are transferred to an escrow account, no longer remaining under the direct custody of the owners.
* **Lack of composability**: The market could benefit from increased liquidity if NFT owners had access to multiple financial tools, such as leveraging loans and renting out their assets for maximum returns. Composability serves as the missing piece in creating a more efficient market.
* **Smart contract vulnerabilities**: NFTs are susceptible to loss or theft due to potential bugs or vulnerabilities present in the smart contracts they rely on.

The aforementioned issues contribute to a poor user experience (UX), and we propose enhancing the [ERC-721](https://eips.ethereum.org/EIPS/eip-721) standard by implementing a native locking mechanism: Rather than being transferred to a smart contract, an NFT remains securely stored in self-custody but is locked. During the lock period, the NFT’s transfer is restricted while its other properties remain unchanged. NFT Owner retains the ability to use or distribute it’s utility.

### Use-Cases <a href="#motivation" id="motivation"></a>

NFTs have numerous use cases where the NFT must remain within the owner’s wallet, even when it serves as collateral for a loan. Whether it’s authorizing access to a Discord server, or utilizing NFT within a play-to-earn (P2E) game, owner should have the freedom to do so throughout the lending period. Just as real estate owner can continue living in their mortgaged house, take personal loan or keep tenants to generate passive income, these functionalities should be available to NFT owners to bring more investors in NFT economy.

Lockable NFTs enable the following use cases :

* **NFT-collateralized loans**: Utilize NFT as collateral for a loan without locking it on the lending protocol contract. Instead, lock it within owner’s wallet while still enjoying all the utility of NFT.
* **No collateral rentals of NFTs**: Borrow an NFT for a fee without the need for significant collateral. Renter can use the NFT but not transfer it, ensuring the lender’s safety. The borrowing service contract automatically returns the NFT to the lender once the borrowing period expires.
* **Buy Now Pay Later**: The buyer receives the locked NFT and can immediately begin using it. However, they are unable to sell the NFT until all installments are paid. Failure to complete the full payment results in the NFT returning to the seller, along with a fee.
* **Composability**: Maximize liquidity by having access to multiple financial tools. Imagine taking a loan against NFT and putting it on rentals to generate passive income.
* **Primary sales**: Mint an NFT for a partial payment and settle the remaining amount once owner is satisfied with the collection’s progress.
* **Soulbound**: Organization can mint and self-assign `locker`, send token to user and lock the asset.
* **Safety**: Safely and conveniently use exclusive blue chip NFTs. Lockable extension allows owner to lock NFT and designate secure cold wallet as the unlocker. This way, owner can keep NFT on MetaMask and easily use it, even if a hacker gains access to MetaMask account. Without access to the cold wallet, the hacker cannot transfer NFT, ensuring its safety.
