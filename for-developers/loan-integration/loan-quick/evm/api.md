# API

The Asset Manager API provides functionalities for managing asset managers in a blockchain-based ecosystem. Asset managers are entities responsible for managing various assets, such as digital tokens, NFTs (Non-Fungible Tokens), and other digital assets, on a blockchain network. This API allows users to retrieve information about asset managers based on their chain ID and contract address.

**Endpoint:**

> * Main Net Base URL: [https://indexer.streamnft.tech/](https://indexer.streamnft.tech/)
> * Test Net Base URL: [https://stagingindexer.streamnft.tech/](https://stagingindexer.streamnft.tech/)

* `GET /assetManager/{chainId}`: Retrieves asset managers by their chain ID and contract address.

**Parameters:**

* `chainId`: The ID of the blockchain chain where the asset managers are deployed.

**Query Parameters specific for rentals:**

* `collection`: Filter for token address of the NFT collection
* `rentee`: Filter for assets rented by a wallet
* `state`: Filter for all assets on loan (LOAN)

{% swagger src="../../../../.gitbook/assets/openapi.yml" path="/assetManager/{chainId}" method="get" %}
[openapi.yml](../../../../.gitbook/assets/openapi.yml)
{% endswagger %}

**Response:**

* Successful responses return an array of asset managers for provided token address with detailed information, such as the current rentee and the state of each asset.
