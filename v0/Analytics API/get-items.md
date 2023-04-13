---
title: "Get Items"
slug: "get-items"
hidden: false
createdAt: "2023-03-29T13:25:10.475Z"
updatedAt: "2023-04-09T11:59:33.198Z"
---
You can use an API call to get all the items included in any of your **clusters or phrases**.

## Get Items in Cluster

To see all of the items inside a **cluster**, send the following API call, providing it with the needed details:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/<collection-name>/clusters/<cluster_id>/items' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```python Python
import requests

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/phrases/<PHRASE ID>/items"

payload={}
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```
```javascript Node
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/phrases/<PHRASE ID>/items',
  'headers': {
    'api-key': '<YOUR API KEY>'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



### Response

And we get a detailed output of the entire cluster:

```json
{
    "items": [
        {
            "id": 8051931,
            "create_date": "2023-03-21T07:55:47 UTC+00:00",
            "item_timestamp": "2023-02-20T11:00:00 UTC+00:00",
            "original_text": "This is a good day.",
            "item_original_text": "This is a good day.",
            "item_summarized_text": "This is a good day.",
            "item_translated_text": null,
            "distance_to_phrase": 0.0,
            "metadata": {
                "key": [
                    {
                        "value": "value",
                        "count": 1
                    }
                ]
            },
            "phrase": {
                "id": 8051935,
                "text": "This is a good day."
            },
            "cluster": {
                "id": 8071302,
                "text": "Tommorrow is the next day."
            }
        }
    ],
    "total_items": 1,
    "total_pages": 1
}
```



## Get Items in Phrase

To see all of the items inside a **phrase**, send the following API call, providing it with the needed details:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/<collection-name>/phrases/<phrase_id>/items' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```python Python
import requests

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/phrases/<PHRASE ID>/items"

payload={}
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```
```javascript Node
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/phrases/<PHRASE ID>/items',
  'headers': {
    'api-key': '<YOUR API KEY>'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



### Response

And we get a detailed output of the entire phrase:

```json
{
    "items": [
        {
            "id": 8141472,
            "create_date": "2023-03-22 08:34:41.0",
            "item_timestamp": "2023-03-22 08:34:41.0",
            "original_text": "Need help cancelling order",
            "item_original_text": "Need help cancelling order",
            "item_translated_text": null,
            "distance_to_phrase": 0.0,
            "metadata": {
                "key": [
                    {
                        "value": "value",
                        "count": 1
                    }
                ]
            },
            "phrase": {
                "id": 8141474,
                "text": "I want to cancel my order"
            },
            "cluster": {
                "id": 8071302,
                "text": "I want to cancel my order"
            }
        }
    ],
    "total_items": 1,
    "total_pages": 1
}
```