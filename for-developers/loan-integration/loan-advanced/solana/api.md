---
description: API Integration for Loan Application with StreamNFT
---

# API

#### 1. Create a Bid Pool

This operation creates a bid pool for a specific collection.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/createLoanPool" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/initPool", "POST", new
{
  interestrate = "1",
  graceperiod = "10",
  collection = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  loanduration = "10",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/initPool");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  interestrate = "1",
  graceperiod = "10",
  collection = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  loanduration = "10",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

#### 2. Get Bid Pool

This operation retrieves the bid pool.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/getLoanPool" method="get" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/getBidPool", "GET", null));// Some code
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/getBidPool");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var response = await client.GetAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

#### 3. Add Liquidity

This operation adds liquidity to a created Bid Pool.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/addLoanOffer" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/initManager", "POST", new
{
  biddingool = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  bidamount = "100", // amount in lamports,
  totalbids = "10", // total bids
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/initManager");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  biddingool = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  bidamount = "100", 
  totalbids = "10", 
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56",
  raw = false 
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

#### 4. Get Bid Manager

This operation retrieves the bid manager.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/getLoanOffers" method="get" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/getBidManager", "GET", null));// Some code
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/getBidPool");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var response = await client.GetAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

#### 5. Get User Assets

This operation retrieves the assets of a specific user.

{% tabs %}
{% tab title="Unity" %}
```csharp
string userAddress = "userAddressHere"; // Replace with the actual user address
StartCoroutine(SendRequest($"http://api.streamnft.tech/getUserAssets/{userAddress}", "GET", null));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var userAddress = "2FPSmq9njjsyr4Axb1LDzdooUaVJThXdgHE4Z6Gpaa3h";
var options = new RestClientOptions($"http://api.streamnft.tech/getUserAssets/{userAddress});
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var response = await client.GetAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

6\. **Get Asset Manager**

This operation retrieves the asset manager.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/getAssetInfo/{mint}" method="get" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp

string mint = "NFTmint"; // Replace with the NFT mint
StartCoroutine(SendRequest($"http://api.streamnft.tech/getAssetInfo/{mint}", "GET", null));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/getAssetManager");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var response = await client.GetAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

#### 7. Take Loan

Collection holders can claim loan on their NFTs.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/processLoan" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/processLoan", "POST", new
{
  biddingpool = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  biddingmanager = "2YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56",
  raw = false 
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/processLoan");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  biddingpool = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  biddingmanager = "2YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56",
  raw = false
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}



#### 8. Repay Loan

Repay loan already taken by the user.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/repayLoan" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/repayLoan", "POST", new
{
  biddingpoolaccount = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  biddingmanager = "2YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  nftmint = "3YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa33",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/repayLoan");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  biddingpoolaccount = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  biddingmanager = "2YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  nftmint = "3YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa33",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56",
  raw = false 
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

#### 9. Remove Liquidity

Liquidity providers can remove provided liquidity.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/removeLoanOffer" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/cancelmanager", "POST", new
{
  biddingpool = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  biddingmanager = "2YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
    secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/cancelmanager");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  biddingpool = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  biddingmanager = "2YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56",
  raw = false
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}

