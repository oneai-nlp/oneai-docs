---
title: "Create a Collection"
slug: "create-collection"
hidden: false
createdAt: "2023-03-29T08:45:56.988Z"
updatedAt: "2023-04-03T12:49:34.186Z"
---
## Grab an API Key

Grab your API key from [your One AI account](https://studio.oneai.com/settings/api-keys). If you haven't yet, sign up to generate an API key.

## Create a new collection

You can create multiple collections as needed, each collection is identified by a `collection domain` and is assigned a `domain`. The collection `domain` defines the way content-items are analyzed and grouped within a collection (for example, how similar items should be to be grouped together).

### Collection Name

Collection name can be any alpha-numeric text (no spaces, punctuation or non [a-z, 0-9] characters allowed).

### Collection Domain

Collection Domain defines the behavior and model used to group and analyze items.

> 🚧 Once a collection is created, it is not possible to change it's **'domain'**

Select one of the following domains to defined the collection's behavior:

| domain     | Use-case description                                                                                                                                                                                                                                                            |
| :--------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `curation` | Broad grouping for both Clusters and Phrases (tends to generate larger groups), useful for getting high-level theme and topic insights from large content collections.  Common use-cases: article categorization, themes in conversations, themes in customer service inquiries |
| `survey`   | Medium grouping for Clusters and Phrases, balances grouping and details, good for detailed analysis of free-text answers in surveys                                                                                                                                             |
| `reviews`  | Medium grouping for Clusters and Phrases, balances grouping and details, good for detailed analysis of free-text reviews                                                                                                                                                        |
| `service`  | Narrow grouping for Clusters and Phrases (tends to generate smaller groups), best used for analyzing search-queries, intent-queries, chat-bot messages                                                                                                                          |
| `classify` | Very Narrow grouping for phrases, Medium grouping for Clusters, best used for cases where retrieval of individual text-items by similarity is needed, like intent-classification and search-index                                                                               |

### Create Collection API Call

Insert your API key, `collection-name`  and `domain` into the request.

```curl
curl -X 'POST' \
  'https://api.oneai.com/clustering/v1/collections/<COLLECTION_NAME>/create' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>' \
  -d '[
  {
    "domain": "<DOMAIN>"
  }
]'
```
```python Python
import requests
import json

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/create"

payload = json.dumps({
  "access": {
    "all": {
      "query": True,
      "list_clusters": True,
      "list_items": True,
      "add_items": True,
      "edit_clusters": True,
      "discoverable": True
    }
  },
  "domain":"<DOMAIN>"
})
headers = {
  'api-key': '<YOUR API KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
```javascript node
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION_NAME>/create',
  'headers': {
    'api-key': '<YOUR API KEY>',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    "access": {
      "all": {
        "query": true,
        "list_clusters": true,
        "list_items": true,
        "add_items": true,
        "edit_clusters": true,
        "discoverable": true
      }
    },
    "domain":"<DOMAIN>"
  })

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



### Access-control

By default, every API key in your account can access any collection (both read and write). It is possible to both limit access to collections to specific API keys, and also to allow access to a collection from API keys owned by a different One AI account.

To control which API keys are allowed to access your collection (your account and other accounts), use the following parameter while creating the account - you can also update access to the collection later through the [`collection-setting` API].

If `allowed_api_keys` is set, only the specified API keys will be allowed access to the collection (you can assign both API keys from your organization or from external organizations).

```curl
curl -X 'POST' \
  'https://api.oneai.com/clustering/v1/collections/<COLLECTION_NAME>/create' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>' \
  -d '[
 	{
    "access": {
        "all":{
            "query": true,
            "list_clusters": true,
            "list_items": true,
            "add_items": true,
            "edit_clusters": true,
            "discoverable": true
        }
    },
    "allowed_api_keys": [
        "<allowed-API-key1>",
        "<allowed-API-key2>",
    ]
	}
]'

```