---
title: "Update Collection Settings"
slug: "update-collection-settings"
hidden: false
metadata: 
createdAt: "2023-04-03T12:41:46.262Z"
updatedAt: "2023-04-03T12:49:23.957Z"
---
By default, every API key in your account can access any collection (both read and write). It is possible to both limit access to collections to specific API keys, and also to allow access to a collection from API keys owned by a different One AI account.

You can define which API keys are allowed to access your collection (your account and other accounts) when creating a collection, but it could also be done by updating the collection settings using the following API call.

If `allowed_api_keys` is set, only the specified API keys will be allowed access to the collection (you can assign both API keys from your organization or from external organizations).

```curl
curl -X 'POST' \
  'https://api.oneai.com/clustering/v1/collections/<COLLECTION_NAME>/settings' \
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