# SDK

SDK optional parameters:

|           | true                   | false                        |
| --------- | ---------------------- | ---------------------------- |
| secretKey | sign using secret key  | sign using wallet adapter    |
| raw       | return raw transaction | execute transaction on-chain |

### Initialize

Initializes NFT rental

{% tabs %}
{% tab title="JS" %}
```javascript
stream.initRent(
  rate: BN, // rent price per minute in lamport
  offerDurationInMinutes: BN, // lend offer duration in minutes
  fixedDurationInMinutes: BN, // fixed rent duration in minutes
  rentIsFixed: boolean, // if a lender decides to define fixed rent duration
  ownerRevenue: BN, // owner share for revenue
  trialType: TrialType | null, // not null if not on trial
  trialFee: BN | null, // not null if on trial
  mint: PublicKey, // mint address of NFT
  whiteList?: PublicKey, //optional
  secretKey?: string, //Optional (providing secret send on-chain transaction)
  raw?: boolean //Optional (return raw transaction)
)
```
{% endtab %}
{% endtabs %}

### \[Process]

Processes NFT rental

{% tabs %}
{% tab title="JS" %}
```javascript
processRent(
  timeInMinutes: BN, // rental duration in minutes
  nftMint: PublicKey, // mint address of NFT
  secretKey?: string, //Optional (providing secret send on-chain transaction)
  raw?: boolean //Optional (return raw transaction)
) 
```
{% endtab %}
{% endtabs %}

### \[Cancel]

Cancels the nft rental

{% tabs %}
{% tab title="JS" %}
```javascript
cancelRent(
  nftMint: PublicKey, // mint address of NFT
  secretKey?: string, //Optional (providing secret send on-chain transaction)
  raw?: boolean
)
```
{% endtab %}
{% endtabs %}

### \[Expire]

Expire NFT rental. This gets triggered by our revocation system.

{% tabs %}
{% tab title="JS" %}
```javascript
expireRent(
  nftMint: PublicKey, // mint address of NFT
  secretKey?: string,
  raw?: boolean
)
```
{% endtab %}
{% endtabs %}
