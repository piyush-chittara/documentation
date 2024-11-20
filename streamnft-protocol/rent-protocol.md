---
description: Owner can transfer NFT to a borrower with zero collateral
---

# 🔓 Rent Protocol

The protocol secures tokens by a set of contracts deployed that are managed by the smart contract. NFT Owner puts their NFT on rent, sets the rules of the contract, and deposits their NFT to the protocol. Borrowers, or customers, can claim the token, and get conditional ownership as parameters set by the issuer.&#x20;

The protocol works permissionless without needing any collateral and aims to solve the following :&#x20;

* The capability to share idle digital assets ( In-game assets, tokenized real estate, digital content, etc. ) for their utility and generate interest\

* Lowering the entry barrier for new consumers by providing a medium to experience at low cost and then make the buying decision\

* Simplifying asset management for institutional holders such as gaming guilds, and DAOs by enabling private rentals. They can simply whitelist the beneficiary's address ( Scholars, etc. ).&#x20;

**🌟 Supported Chains -** Solana, Ethereum, Polygon, Hedera, Mantle, Telos, & more coming soon ( Pipeline - Avalanche, Arbitrum, Scroll, etc. )\


{% tabs %}
{% tab title="Rentals on EVM" %}


NFTs on EVM are not inherently lockable, therefore StreamNFT has proposed [ERC7066](https://eips.ethereum.org/EIPS/eip-7066) to enable escrowless financialization tools on EVM. StreamNFT currently supports ERC721, ERC1155 and ERC7066 NFTs. Integration steps for these can be found [here](../for-developers/rental-integration/rental-quick/).

### Features:

Projects can customize own rental solutions using provided features:

1. **Asset Receipt**
   * Smart Registry: Low cost solution where smart contract stores the token states
   * Wrapped Token: Mint an [ERC7066](https://eips.ethereum.org/EIPS/eip-7066) wrapped token as receipt (an extension of ERC721 and supports all ERC721 functions). [ERC7066](https://eips.ethereum.org/EIPS/eip-7066) copy of token is transferred and locked to user wallet. Only one token is minted for each NFT and all subsequent rentals lock/unlock and transfer the wrapped token using [ERC7066](https://eips.ethereum.org/EIPS/eip-7066) capabilities, thus making the solution gas optimal.&#x20;
2. **Private Rental**\
   Configure rental within a specific guild or targeted user base
3. **Custom Payment Token**\
   Configure rental payment in chain native token or your own ERC20 token
4. **Partner Fee**\
   Project/Collection can configure their fee, which shall be processed to partner treasury on each successful rental
5. **Reward sharing**\
   Reward NFT holders in native tokens or any ERC20 token, which gets distributed to NFT owner and NFT rentee as per configurable reward share
6. **Trials**\
   Project can choose to list NFTs on trial for no cost. Incentivising users to experience projects and NFT utilities for free.
{% endtab %}

{% tab title="Rentals on Solana" %}


StreamNFT brings truly decentralized and no-collateralization rental protocol, enabling digital asset owners and projects to make their NFTs rentable. Borrowers can own digital assets for their utility for a specified duration without locking up capital or exposing themselves to volatility by just paying small fees.&#x20;

**Supported Standard :** Metaplex Editions, pNFT

### Features:

1. **Decentralized and Escrowless**\
   NFT never leaves your wallet. While renting out or on loan, NFT stays within your wallet. Enabling users to exercise utility of NFT. NFT successful rental transfers NFT to rentee and locks the NFT in the wallet.
2. **Integration require 0 line of code**\
   StreamNFT moves NFTs to user wallets and enabling rental for your project require 0 development efforts
3. **Time Based and Use Based Rentals**\
   NFT rental expiry can be configured based on time. Optionally with 2 lines of code on-chain / off-chain use based expiry can be configured.
4. **Private Rental**\
   Configure rental within a specific guild or targeted user base
5. **Custom Payment Token**\
   Configure rental payment in chain native token or your own SPL token
6. **Partner Fee**\
   Project/Collection can configure their fee, which shall be processed to partner treasury on each successful rental
7. **Reward sharing**\
   Reward NFT holders in native tokens or any SPL token, which gets distributed to NFT owner and NFT rentee as per configurable reward share
8. **Trials**\
   Project can choose to list NFTs on trial for no cost. Incentivising users to experience projects and NFT utilities for free.
{% endtab %}
{% endtabs %}

<figure><img src="../.gitbook/assets/Post 4.png" alt=""><figcaption><p>Rental Protocol Flow</p></figcaption></figure>



##
