# SDK

**1. Initialize a bid pool:**

To create a bid pool for your NFT collection, follow the steps below:

* `tokenAddress`: The address of the ERC721 token representing your NFT collection.
* `loanDurationInMinutes`: The duration of the loan period in minutes.
* `gracePeriodInMinutes`: The grace period in minutes before the loan expires.
* `interestRateLender`: The interest rate for the lender, specified in percentage.



{% tabs %}
{% tab title="JS" %}
```javascript
const tokenAddress = "TOKEN_ADDRESS"; // ERC721 Token address
const loanDurationInMinutes = 60;
const gracePeriodInMinutes = 10;
const interestRateLender = 5; // in percentage

stream.createLoanPool(
  tokenAddress,
  loanDurationInMinutes,
  gracePeriodInMinutes,
  interestRateLender,
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
{% endtab %}
{% endtabs %}

By following these steps, you can create a bid pool for your NFT collection and manage various loan-related operations efficiently using the SDK. Remember to replace the placeholder `TOKEN_ADDRESS` with the actual address of your ERC721 token.



**2. Get bid pool details by bidPoolIndex:**

To retrieve the bidding pool for your NFT collection, you can use the following method:

* `bidPoolIndex`: The index of the bid pool.



{% tabs %}
{% tab title="JS" %}
```javascript
const bidPoolIndex = 0; // Index of the bid pool

strean.getBidPoolByIndex(bidPoolIndex, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

```javascript
Response object of bid pool :
    {
      initializerKey: the address of the administrator,
      tokenAddress: the address of the token (e.g., 'xyz'),
      loanDurationInMinutes: the duration of the loan (e.g., 30 days),
      gracePeriodInMinutes: the grace period of the loan,
      apy: the annual percentage yield (e.g., 20%),
      interestRateLender: the interest rate for the lender,
      interestRateProtocol: the interest rate for the protocol,
      totalBidManager: the total bids managed,
      lastBidAmount: the amount of the last bid,
      bidNftFloorPrice: the minimum bid price for the NFT,
    }    
```

This code snippet demonstrates how to use and handle the returned data from the `getBidPools` function, as well as provides descriptions of the properties in the BidPool data structure.



By executing this code snippet, you will receive the details and information associated with the bid pool for your NFT collection. Remember to replace the `bidPoolIndex` with the actual index of the bid pool you want to retrieve.



**3. Get the length of the bid pool:**&#x20;

To retrieve the length of the bidding pool for your NFT collection, you can use the following method: chainId: The identifier of the blockchain where the NFTs reside.

{% tabs %}
{% tab title="JS" %}
```javascript

getBidPoolLength(chainId)
  .then((result) => {
    // Handle the result
    // Result will be the length of the bid pool on the specified chain
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

By executing this code snippet, you will receive the total number of bid pools associated with your NFT collection on the specified blockchain. Remember to replace the `chainId` with the actual identifier of the blockchain where your NFTs are located.



**4. Get all bid pools:**&#x20;

To retrieve all the bidding pools for your NFT collection, you can use the following method: chainId: The identifier of the blockchain where the NFTs reside.

{% tabs %}
{% tab title="JS" %}
```javascript
getBidPools(chainId)
  .then((result) => {
    // Handle the result
    // Result will be an array of all the bid pools on the specified chain
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

```javascript
Response object of bid pool List :
    [{
      initializerKey: the address of the administrator,
      tokenAddress: the address of the token (e.g., 'xyz'),
      loanDurationInMinutes: the duration of the loan (e.g., 30 days),
      gracePeriodInMinutes: the grace period of the loan,
      apy: the annual percentage yield (e.g., 20%),
      interestRateLender: the interest rate for the lender,
      interestRateProtocol: the interest rate for the protocol,
      totalBidManager: the total bids managed,
      lastBidAmount: the amount of the last bid,
      bidNftFloorPrice: the minimum bid price for the NFT,
    }]

    
```

This code snippet demonstrates how to use and handle the returned data from the `getBidPools` function, as well as provides descriptions of the properties in the BidPool data structure.



By executing this code snippet, you will receive a list of all the bid pools associated with your NFT collection on the specified blockchain. Remember to replace the `chainId` with the actual identifier of the blockchain where your NFTs are located.



**5. Creating a Bid Manager:**

To create a bid manager, you can use the following function:

* Provide the index of the bid pool, bid amount, total number of bids, chainId, and signer.

{% tabs %}
{% tab title="JS" %}
<pre class="language-javascript"><code class="lang-javascript">const bidPoolIndex = 0; // Index of the bid pool
const bidAmount = 100; // Amount of the bid
const totalBids = 10; // Total number of bids

stream.addLoanOffer(bidPoolIndex, bidAmount, totalBids, chainId, signer)
  .then((result) => {
<strong>    // Handle the result
</strong>  })
  .catch((error) => {
    // Handle the error
  });
</code></pre>
{% endtab %}
{% endtabs %}

By executing this code, a bid manager will be created within the specified bid pool. Ensure that you provide the appropriate values for the bid pool index, bid amount, and total number of bids to customize the bid manager according to your requirements.



**6. Retrieving Bid Manager Details:**

To retrieve the details of a bid manager, you can use the following function:

* Provide the index of the bid pool and the index of the bid manager, along with the chainId and provider.

{% tabs %}
{% tab title="JS" %}
```javascript
const bidPoolIndex = 0; // Index of the bid pool
const bidManagerIndex = 0; // Index of the bid manager

stream.getLoanOffer(bidPoolIndex, bidManagerIndex, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

Executing this code will fetch the details of the specified bid manager, including relevant information such as bid manager address, bid pool index, bid amount, and other related data. Make sure to provide the correct bid pool index and bid manager index to retrieve the desired bid manager details.



**7. Cancel a Bid Manager:**

To cancel a bid manager and remove it from the bidding pool, you can utilize the following function:

* Specify the bid pool index and bid manager index of the bid manager you want to cancel.
* Provide the chainId and signer information.



{% tabs %}
{% tab title="JS" %}
<pre class="language-javascript"><code class="lang-javascript">const bidPoolIndex = 0; // Index of the bid pool
const bidManagerIndex = 0; // Index of the bid manager

<strong>stream.cancelManager(bidPoolIndex, bidManagerIndex, chainId, signer)
</strong>  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
</code></pre>
{% endtab %}
{% endtabs %}

By executing this code, you will initiate the cancellation process for the specified bid manager within the bidding pool. Ensure that you provide the correct bid pool index and bid manager index to cancel the intended bid manager successfully.



**8. Processing a Loan:**

To initiate the loan processing, you can use the following function:

* Specify the bid pool index, bid manager index, and the token ID for the loan.
* Also, provide the chainId and signer information.

{% tabs %}
{% tab title="JS" %}
```javascript
const bidPoolIndex = 0; // Index of the bid pool
const bidManagerIndex = 0; // Index of the bid manager
const tokenId = "TOKEN_ID";

processLoan(bidPoolIndex, bidManagerIndex, tokenId, chainId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

By executing this code, you will trigger the processing of the loan associated with the specified bid pool and bid manager. The provided token ID is used to identify the specific loan to be processed. Ensure that you provide the correct bid pool index, bid manager index, and token ID to process the desired loan successfully.



**9. Get User Asset Details:**

To retrieve the details of a specific user asset, you can use the following function:

* Specify the user's public address and the index of the user asset.
* Provide the chainId .



{% tabs %}
{% tab title="JS" %}
```javascript
const userAddress = "USER_PUBLIC_KEY";
const userAssetIndex = 0; // Index of the user asset

getUserAssets(userAddress, userAssetIndex, chainId)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

Executing this code will fetch the details of the user asset associated with the provided user address and asset index. Ensure that you supply the correct user address and asset index to retrieve the desired asset details. The result will contain information such as the asset's token address, token ID, and other relevant details pertaining to the user asset.



**10. Repaying a Loan:**

To initiate the repayment of a loan, you can use the following function:

* Specify the user asset index for the loan repayment.
* Also, provide the chainId and signer information.

{% tabs %}
{% tab title="JS" %}
```javascript
const userAssetIndex = 0; // Index of the user asset

repayLoan(userAssetIndex, chainId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

By executing this code, you will trigger the repayment process for the loan associated with the specified user asset index. Ensure that you provide the correct user asset index to repay the intended loan successfully.



**11. Expire a Loan:**

To expire a loan and terminate its active status, you can utilize the following function:

* Specify the user asset index for the loan to be expired.
* Provide the chainId and signer information.

{% tabs %}
{% tab title="JS" %}
```javascript
const userAssetIndex = 0; // Index of the user asset

expireLoan(userAssetIndex, chainId, signer)
  .then((result) => {
    // Handle the result
  })
  .catch((error) => {
    // Handle the error
  });
```
{% endtab %}
{% endtabs %}

By executing this code, you will initiate the expiration process for the loan associated with the provided user asset index. Ensure that you provide the correct user asset index to expire the intended loan successfully.



Make sure to replace the placeholders (TOKEN\_ADDRESS, TOKEN\_ID, USER\_PUBLIC\_KEY, etc.) with the actual values specific to your use case.\


These examples demonstrate how to use the SDK functions to interact with the smart contract. You can integrate them into your application logic and handle the results and errors accordingly.
