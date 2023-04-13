---
title: "Quick Start"
slug: "quick-start-analytics"
excerpt: "We will have you running your first One AI query in less than a minute."
hidden: false
createdAt: "2022-08-28T11:55:34.439Z"
updatedAt: "2023-04-03T12:34:11.552Z"
---
## Grab an API key

Grab your API key from [your One AI account](https://studio.oneai.com/settings/api-keys). If you haven't yet, sign up to generate an API Key.

## Creating a collection

> 👍 Pro-tip: You can skip this step for now, inserting items will implicitly create a collection with default configuration params.

Send the following API call in order to create a collection. See more information on [Creating a Collection page](https://docs.oneai.com/docs/create-collection) .

```curl
curl -X 'POST' \
  'https://api.oneai.com/clustering/v1/collections/my-first-analytics-collection/create' \
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

url = "https://api.oneai.com/clustering/v1/collections/my-first-analytics-collection/create"

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
  'url': 'https://api.oneai.com/clustering/v1/collections/my-first-analytics-collection/create',
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



## Inserting items into a collection

Clustering is an analytics tool. You push data consistently and then you can analyze it at any point in time. So let's start by pushing some data

1. Copy this code (select between `curl`, `Node.js` or `Python`).

```curl
curl -X 'POST' \
  'https://api.oneai.com/clustering/v1/collections/my-first-analytics-collection/items' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>' \
  -H 'Content-Type: application/json' \
  -d '[
  {
    "text": "Can not access account"
  },
  {
    "text": "I cannot access my account"
  },
  {
    "text": "Can not enter my account"
  },
  {
    "text": "Cancel order"
  },
  {
    "text": "I want to cancel my order"
  },
  {
    "text": "How do I cancel my order?"
  },
  {
    "text": "Need help cancelling order"
  }
]'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const collection = new oneai.clustering.Collection('support-email-subjects');

const items = [
  {
    "text": "Can not access account"
  },
  {
    "text": "I cannot access my account"
  },
  {
    "text": "Can not enter my account"
  },
  {
    "text": "Cancel order"
  },
  {
    "text": "I want to cancel my order"
  },
  {
    "text": "How do I cancel my order?"
  },
  {
    "text": "Need help cancelling order"
  }
];

collection.addItems(items).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"

collection = oneai.clustering.Collection('support-email-subjects')

items = [
  "Can not access account",
  "I cannot access my account",
	"Can not enter my account",
  "Cancel order",
	"I want to cancel my order",
  "How do I cancel my order?",
  "Need help cancelling order"
]

collection.add_items(items)
```



2. Paste your API Key instead of the `<YOUR-API-KEY-HERE>` placeholder.
3. `pip3 install oneai` or `npm install oneai` if you selected to use the `Python` or `Node.js` examples respectively.

## Run the sample

You should be getting an output similar to

```json JSON Response
{"status":"queued"}
```



## List collections

Your job has been queued - not to worry, it will run moments later.

An excellent way to poll for results in the future is to list all your available collections. Since you provided a name for a collection that didn't yet exist, the collection `my-first-analytics-collection` was supposed to be created for you. Let's see if it was.

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

(async () => {
  for await (const collection of oneai.clustering.getCollections()) {
    console.log(collection.toJSON());
  }
})();
```
```Text Python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"

for collection in oneai.clustering.get_collections():
		print(collection)
```



The response should look something like

```json JSON Response
{
	"collections": [
		"my-first-analytics-collection"
	]
}
```
```json Node.js Response
[
  { id: 'support-email-subjects' },
  ...
]
```
```Text Python Response
[
	Collection(name="my-first-analytics-collection"),
  ...
]
```



## Fetch all collection clusters

Now we can fetch all collection clusters. Clusters are automatically created for us, so this is where we start to see the magic.

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/my-first-analytics-collection/clusters?sort=ASC&include-phrases=false' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node.js
const OneAI = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const collection = new oneai.clustering.Collection('support-email-subjects');
(async () => {
	for await (const item of collection.getClusters()) {
  	console.log(item);
  }
})();
```
```Text Python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"

collection = oneai.clustering.Collection('support-email-subjects')
for cluster in collection.get_clusters():
		print(cluster)
```



You should be getting something similar to this as a response:

```json
{
  "clusters": [
    {
      "cluster_id": 51411,
      "collection": "my-first-analytics-collection",
      "cluster_phrase": "Need help cancelling order",
      "phrases_count": 2,
      "metadata": null,
      "items_count": 8
    },
    {
      "cluster_id": 51412,
      "collection": "my-first-analytics-collection",
      "cluster_phrase": "Can not access account",
      "phrases_count": 1,
      "metadata": null,
      "items_count": 6
    }
	],
  "total_clusters": 10,
  "total_pages" 5
}
```



You can see that the collection was clustered into two, one cluster about `Need help cancelling order` and the other about `Can not access account`

## Fetch all cluster phrases

Let's drill down into the `Need help cancelling order` cluster phrases:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/my-first-analytics-collection/clusters/51411/items' \
  -H 'accept: application/json' \
  -H 'api-key: 5475fb4a-e4b0-4c11-b9d5-6d98d2434593'
```
```javascript Node.js
const OneAI = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const collection = new oneai.clustering.Collection('support-email-subjects');
const cluster = new oneai.clustering.Cluster({id: 51411, collection});
(async () => {
	for await (const item of cluster.getPhrases()) {
  	console.log(item);
  }
})();
```
```Text Python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"

collection = oneai.clustering.Collection('support-email-subjects')
cluster = collection.get_clusters()[0]
for phrase in cluster.get_phrases():
		print(phrase)
```



And we get a detailed output of the entire cluster:

```json
{  
	"phrases": [
    {
      "id": 51419,
      "create_date": "2022-08-28 13:10:23.181493",
      "original_text": "I want to cancel my order",
      "distance_to_phrase": -0.000001000000000139778,
      "phrase": {
        "id": 51409,
        "text": "I want to cancel my order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    },
    {
      "id": 51417,
      "create_date": "2022-08-28 13:10:22.147757",
      "original_text": "Need help cancelling order",
      "distance_to_phrase": 0,
      "phrase": {
        "id": 51402,
        "text": "Need help cancelling order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    },
    {
      "id": 51416,
      "create_date": "2022-08-28 13:10:21.648177",
      "original_text": "Cancel order",
      "distance_to_phrase": 0.14747310000000002,
      "phrase": {
        "id": 51402,
        "text": "Need help cancelling order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    },
    {
      "id": 51415,
      "create_date": "2022-08-28 13:10:21.139048",
      "original_text": "How do I cancel my order?",
      "distance_to_phrase": 0.12254450000000006,
      "phrase": {
        "id": 51409,
        "text": "I want to cancel my order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    },
    {
      "id": 51408,
      "create_date": "2022-08-28 12:04:46.860096",
      "original_text": "I want to cancel my order",
      "distance_to_phrase": 0,
      "phrase": {
        "id": 51409,
        "text": "I want to cancel my order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    },
    {
      "id": 51407,
      "create_date": "2022-08-28 12:04:46.375460",
      "original_text": "Cancel order",
      "distance_to_phrase": 0.1474495,
      "phrase": {
        "id": 51402,
        "text": "Need help cancelling order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    },
    {
      "id": 51405,
      "create_date": "2022-08-28 12:04:44.518022",
      "original_text": "How do I cancel my order?",
      "distance_to_phrase": 0.1381425999999999,
      "phrase": {
        "id": 51402,
        "text": "Need help cancelling order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    },
    {
      "id": 51401,
      "create_date": "2022-08-28 12:04:43.396130",
      "original_text": "Need help cancelling order",
      "distance_to_phrase": 0,
      "phrase": {
        "id": 51402,
        "text": "Need help cancelling order"
      },
      "cluster": {
        "id": 51411,
        "text": "Need help cancelling order"
      }
    }
  ],
	"total_phrases": 10,
	"total_pages": 1
}
```



## Analyze the data

Now you already have enough data to start analyzing. You may want to use our [UI tool](doc:ui-component) for easy text analytics.