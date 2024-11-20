# How does a loan work?

The owner of the NFT can **initialize** a smart contract and Program derived address ( PDA ) is created from the mint key of the NFT to store specific data including **interest, duration, transferability,** and **state** (issued, transferred, or terminated).

* Lender interacts with protocol to offer capital to the collection-specific pool with defined interest & duration.
  * Lender can choose to cancel the offer bid anytime if an order doesn't fill for longer. \

* Owner agrees to the best offer for a specific collection pool and the protocol locks NFT in the owner's wallet. \

* If the loan is repaid with interest within the specified loan duration then NFT is unfreeze.\

* If the loan is not repaid within the specified loan duration then NFT is transferred to the lender.

\
The lifecycle of the offer is completed upon cancellation, or necessary payments are settled, and the token is returned back to the right owner.

## How NFT can be used for its utility while on loan?

StreamNFT locks NFT in your wallet during the loan, despite using it as collateral. We want to bring same benefit with your NFTs as real-world financing. If you take a bank loan against a house, you still get to live inside it and retain conditional ownership unless the loan defaults.&#x20;

You can remain in your DAO, vote in governance, get airdrops, and get in-game utility for gaming NFTs.&#x20;

During the loan period, the lender cannot transfer the NFT as it is locked in the wallet. If the borrower doesn’t pay back, it will be transferred to the lender automatically. If the borrower does, then NFT is unlocked & freed.&#x20;

## Things to consider

* Each collection has multiple sub-pools with variable interest & duration. So, lenders can access their risk appetite and opt for better-suited sub-pool\

* &#x20;NFTs in a collection are regarded as equal at the moment, so you don’t need to pick your super rare NFT as collateral. Rather, you can pick an NFT you’re comfortable parting with. That way, in the unlikely event of a default, you don’t lose a sentimental NFT\

* The main risk Lenders have to consider, is the event of the NFT’s value dropping below the loan offer. If you think the NFT is worth 50 SOL/ETH/HBAR, but tomorrow you think the value is now 45 SOL/ETH/HBAR, then if the Borrower defaults, you lose money. This is why Lenders often choose to over-collateralize, meaning they offer lower than what they think the NFT is worth. It’s up to you and your bullishness on a project. Maybe you think the value would go up, and no chance of it going down.\

* In the case of a default, you get the NFT instead of your loan payment. So you should be comfortable with your loan offer in exchange for the NFT. You want to pay as low of a cost as possible for this consideration.\

* The reason you shouldn’t offer 0.001 SOL/ETH/HBAR, is that it’s a terrible deal for the Borrower, and they may not ever take your offer. If your offer is always lower than what other Lenders offer, then it could be a long time, if ever, before your loan is accepted.
