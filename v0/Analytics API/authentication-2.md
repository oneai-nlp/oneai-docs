---
title: "Authentication"
slug: "authentication-2"
hidden: false
createdAt: "2022-08-18T12:58:50.010Z"
updatedAt: "2022-12-28T13:42:11.406Z"
---
Create a key for your project [here](https://studio.oneai.com/settings/api-keys). Attach your key to API requests via the `api-key` header. Requests must be authenticated and will fail without an active token.

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