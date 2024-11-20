# API

#### 1. Lend NFT for rental

This operation will list the NFT on DApp for rentals.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/lendToken" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/lendToken", "POST", new
{
  nftmint = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h", 
  rate = "10", // rate per minute
  offerduration = "1",
  isfixed = true,
  fixedminutes = "10",
  ownershare = "10",
  whitelist = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h", // whitelist for private rental (undefined for public)
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/lendToken");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  nftmint = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h", 
  rate = "10",
  offerduration = "1",
  isfixed = true,
  fixedminutes = "10",
  ownershare = "10",
  whitelist = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h", 
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot2cj5Cz56",
  raw = false
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}
{% endtabs %}



#### 2. Take Rent for any NFT

User can take any NFT on rent for provided time duration.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/processRent" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/processRent", "POST", new
{
  durationminutes = "60",
  nftmint = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/processRent");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  durationminutes = "60",
  nftmint = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot2cj5Cz56", 
  raw = false
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}

{% tab title="Bash" %}

{% endtab %}
{% endtabs %}



#### 3. Cancel Rent

Cancel the rental offer and retrieve back the NFT.

{% swagger src="../../../../.gitbook/assets/apidoc.json" path="/removeLendToken" method="post" %}
[apidoc.json](../../../../.gitbook/assets/apidoc.json)
{% endswagger %}

{% tabs %}
{% tab title="Unity" %}
```csharp
StartCoroutine(SendRequest("http://api.streamnft.tech/cancelRent", "POST", new
{
  nftmint = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot2cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}));
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var options = new RestClientOptions("http://api.streamnft.tech/cancelRent");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var body= {
  nftmint = "1YeSmq9njjsyr4AYb1LDzdooUaVJThXdgH34Z6Gpaa3h",
  secret = "4uzLYRhX2dnsgUZVNNY82TNFCZbDFt5D9KLJuTFM8X2mc83ACEybEAi8aurEEZJTkSBwp8xg65KKP2ot1cj5Cz56", //Optional (providing secret send on-chain transaction)
  raw = false //Optional (return raw transaction)
}
request.AddBody(body);
var response = await client.PostAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}

{% tab title="Bash" %}

{% endtab %}
{% endtabs %}

#### 4. Get User Assets

This operation retrieves the assets of a specific user.

{% tabs %}
{% tab title="Unity" %}
```csharp
string userAddress = "userAddressHere"; // Replace with the actual user address
StartCoroutine(SendRequest($"http://api.streamnft.tech/getUserAssets/{userAddress}", "GET", null));// Some code
```
{% endtab %}

{% tab title="C#" %}
```csharp
using RestSharp;

var userAddress = "2FPSmq9njjsyr4Axb1LDzdooUaVJThXdgHE4Z6Gpaa3h";
var options = new RestClientOptions($"http://api.streamnft.tech/getUserAssets/{userAddress}");
var client = new RestClient(options);
var request = new RestRequest("");
request.AddHeader("accept", "application/json");
var response = await client.GetAsync(request);

Console.WriteLine("{0}", response.Content);
```
{% endtab %}

{% tab title="Bash" %}

{% endtab %}
{% endtabs %}



#### 5. Get Asset Manager

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

{% tab title="Bash" %}

{% endtab %}
{% endtabs %}

