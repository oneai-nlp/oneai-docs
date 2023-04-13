---
title: "Authentication"
slug: "authentication"
hidden: false
createdAt: "2022-08-15T12:44:16.498Z"
updatedAt: "2022-12-28T13:28:46.413Z"
---
Create a key for your project [here](https://studio.oneai.com/settings/api-keys). Attach your key to API requests via the `api-key` header. Requests must be authenticated, and will fail without an active token.

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
```
```javascript Node.js
const { OneAI } = require("oneai");
const oneai = new OneAI("<YOUR-API-KEY-HERE>");
```
```python
import oneai
oneai.api_key = "<YOUR-API-KEY-HERE>"
```