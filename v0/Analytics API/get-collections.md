---
title: "Get Collections"
slug: "get-collections"
hidden: false
metadata: 
createdAt: "2023-03-29T12:16:17.462Z"
updatedAt: "2023-04-03T09:24:38.023Z"
---
To see the collections related to your API key, send the following API call, providing it with the needed details:

```curl
curl -X 'GET' \
  'https://api.oneai.com/clustering/v1/collections' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```
```javascript Node
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.oneai.com/clustering/v1/collections',
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

url = "https://api.oneai.com/clustering/v1/collections"

payload={}
headers = {
  'api-key': '<YOUR API KEY>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```



The response should look something like this:

```json JSON Response
{
	"collections": [
		"my-first-analytics-collection"
	]
}
```