---
title: "File Uploads"
slug: "file-uploads-1"
hidden: false
createdAt: "2022-08-22T10:01:40.825Z"
updatedAt: "2022-12-28T13:44:38.642Z"
---
Our SDKs currently support sync file uploads. Async support is coming soon.

```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const file = new oneai.File("<PATH-TO-YOUR-FILE>");

const pipeline = new oneai.Pipeline(
	oneai.skills.summarize(),
);

pipeline.run(file).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
file = oneai.File("<PATH-TO-FILE>")

pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Summarize(),
  ]
)

output = pipeline.run(file)
```