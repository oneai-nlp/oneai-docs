---
title: "Merge/Split Clusters"
slug: "merge-split-clusters"
hidden: false
metadata: 
createdAt: "2023-03-29T12:25:16.707Z"
updatedAt: "2023-04-03T10:01:36.227Z"
---
In case you are interested in changing the clusters created automatically by the AI engine, you can split or merge them. For both actions you need to know the `cluster_id` - see [Get Clusters in Collection](https://docs.oneai.com/docs/list-clusters). 

### Merge Clusters

In order to merge clusters, be it two or more, use the following API, providing it with the relevant details:

```curl
curl -X POST \
'https://api.oneai.com/clustering/v1/collections/<collection-name>/merge' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
--d '{"source_clusters":["<CLUSTER ID>","<CLUSTER ID>"],
    "destination_cluster":"<CLUSTER ID>"}'
```
```python
import requests
import json

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/merge"

payload = json.dumps({
  "source_clusters": [
    "<CLUSTER ID>",
    "<CLUSTER ID>"
  ],
  "destination_cluster": "<CLUSTER ID>"
})
headers = {
  'api-key': '<YOUR API KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
```javascript Node
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/merge',
  'headers': {
    'api-key': '<YOUR API KEY>',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    "source_clusters": [
      "<CLUSTER ID>",
      "<CLUSTER ID>"
    ],
    "destination_cluster":"<CLUSTER ID>"
  })

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



Note this function could be used to merge a few clusters into one of them, but also to merge a few clusters into a completely different cluster. 

### Split Clusters

In order to split a cluster, use the following API, providing it with the relevant details:

```curl
curl -X 'POST' \
  'https://api.oneai.com/clustering/v1/collections/<collection-name>/phrases/<phrase_id>/split'\
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/phrases/<PHRASE ID>/split',
  'headers': {
    'api-key': '<YOUR API KEY>'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```
```python
import requests

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/phrases/<PHRASE ID>/split"

payload = ""
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```