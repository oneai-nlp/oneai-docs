---
title: "Find Text in Clusters"
slug: "find-text"
excerpt: "Find clusters with a similar meaning of a given text"
hidden: false
createdAt: "2023-03-29T12:19:14.562Z"
updatedAt: "2023-04-09T11:32:52.077Z"
---
To look for text inside a cluster, send the following API call, providing it with the needed details:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/<collection_name>/clusters/find?text=<search_text>' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters/find?text=<TEXT>',
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

url = "https://api.oneai.com/clustering/v1/collections/<COLLECTION NAME>/clusters/find?text=<TEXT>"

payload={}
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```



## URL Parameters

| Name                        | Type    | Description                                     | Required? |
| :-------------------------- | :------ | :---------------------------------------------- | :-------- |
| text                        | String  | Search Text                                     | Yes       |
| multilingual                | Boolean | True if text is not in english                  | No        |
| translate                   | Boolean | Translate to English                            | No        |
| similarity_threshold        | String  | Minimum similarity of results (between 0 and 1) | No        |
| expected-language           | String  | Expected language of text                       | No        |
| override-language-detection | Boolean | Whether to override language detection          | No        |

Here is an example of such a complexed URL:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections/<Collection Name>/clusters/find?multilingual=true&translate=true&similarity_threshold=0.5&text=<Search Text>' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.oneai.com/clustering/v1/collections/<Collection Name>/clusters/find?multilingual=true&translate=true&similarity_threshold=0.5&text=<Search Text>',
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

url = "https://api.oneai.com/clustering/v1/collections/<Collection Name>/clusters/find?multilingual=true&translate=true&similarity_threshold=0.5&text=<Search Text>"

payload={}
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```



#### Response

```curl
  [
    {
        "cluster_id": 9283919,
        "cluster_text": "I am very hungry",
        "item_original_text": "I am very hungry",
        "item_translated_text": null,
        "matching_cluster_phrase_id": 9283906,
        "cluster_properties": null,
        "similarity": 0.84834995
    },
    {
        "cluster_id": 9283920,
        "cluster_text": "These pretzles are making me thirsty",
        "item_original_text": "These pretzles are making me thirsty",
        "item_translated_text": null,
        "matching_cluster_phrase_id": 9283917,
        "cluster_properties": null,
        "similarity": 0.61838975
    }
]
```