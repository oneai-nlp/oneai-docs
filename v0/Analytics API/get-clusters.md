---
title: "Get Clusters"
slug: "get-clusters"
hidden: false
createdAt: "2023-03-29T12:17:25.326Z"
updatedAt: "2023-04-03T12:52:25.813Z"
---
Clusters are automatically created for us by running the "clustering" skill. To see all of the clusters inside a collection, insert the name of the desired collection and send the following API call, providing it with the needed details:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters',
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

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters"

payload={}
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```



## URL Parameters

| Name             | Type    | Description                                                        | Required? |
| :--------------- | :------ | :----------------------------------------------------------------- | :-------- |
| sort             | String  | Sort options                                                       | No        |
| include-phrases  | boolean | Whether the response will list the phrases in each of the clusters | No        |
| limit            | Int     | Set a limit for how many clusters in response                      | No        |
| phrases-limit    | Int     | Set a limit for how many phrases in cluster                        | No        |
| properties-query | String  | Query clusters eg: key1 eq 'val1' and key2 neq 'val'               | No        |
| page             | Int     | Page number                                                        | No        |

Here is an example format of such a URL, including some of the parameters inserted into the URL adjoined by `&`: 

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters?page=0&limit=25&translate=true&include-phrases=true' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```

## Call Response

You should be getting something similar to this as a response, displaying all clusters along with their "cluster_id":

```json
{
  "clusters": [
    {
      "cluster_id": <51411>,
      "collection": "<collection-name>",
      "cluster_phrase": "Need help cancelling order",
      "phrases_count": 2,
      "metadata": null,
      "items_count": 8
    },
    {
      "cluster_id": <51412>,
      "collection": "<collection-name>",
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



You can see that this collection was clustered into two, one cluster about `Need help cancelling order` and the other about `Can not access account`