---
title: "Batch Support"
slug: "batch-support"
excerpt: "The SDKs contain functionality to run Pipeline queries in scale"
hidden: false
createdAt: "2022-08-22T10:00:37.680Z"
updatedAt: "2022-12-28T13:44:19.057Z"
---
Let's say you have a bunch of text that you want to analyze. Instead of using OneAI in a loop, or one by one, the SDKs contain the functionality to help you send all the text in a single command.

```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const texts = [
  "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
  "Some other text to summarize",
  "And another one",
];

const pipeline = new oneai.Pipeline(
	oneai.skills.summarize(),
);

pipeline.runBatch(texts).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
texts = [
  "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
  "Some other text to summarize",
  "And another one",
]

pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Summarize(),
  ]
)

output = pipeline.run_batch(texts)
```