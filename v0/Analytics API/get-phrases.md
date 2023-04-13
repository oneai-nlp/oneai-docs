---
title: "Get Phrases"
slug: "get-phrases"
hidden: false
createdAt: "2023-03-29T12:18:09.045Z"
updatedAt: "2023-04-03T12:52:30.714Z"
---
To see all of the phrases inside a cluster, send the following API call, providing it with the needed details:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters/<CLUSTER ID>/phrases' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters/<CLUSTER ID>/phrases',
  'headers': {
    'api-key': '<YOUR API KEY>'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```
```python Python
import requests

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters/<CLUSTER ID>/phrases"

payload={}
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```



And we get a detailed output of the entire cluster:

```json
{  
	"phrases": [
    {
      "id": 51418,
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
    }
  ],
	"total_phrases": 10,
	"total_pages": 1
}
```