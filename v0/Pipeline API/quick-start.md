---
title: "Quick Start"
slug: "quick-start"
excerpt: "We will have you running your first One AI query in less than a minute."
hidden: false
createdAt: "2022-08-15T12:43:58.022Z"
updatedAt: "2022-12-28T13:27:49.772Z"
---
## Grab an API key

Grab your API key from [your One AI account](https://studio.oneai.com/settings/api-keys). If you haven't yet, sign up to generate an API Key.

## Prepare your first One AI Pipeline API call

Let's summarize a paragraph using One AI's Pipeline API:

1. Copy this code (select between `curl`, `Node.js` or `Python`).

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
    "steps": [
      {
        "skill": "summarize"
      }   
    ]
}'
```
```javascript Node.js
// npm install oneai
const OneAI = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%";
const pipeline = new oneai.Pipeline(
	oneai.skills.summarize(),
);

pipeline.run(text).then(console.log);
```
```python
# pip install oneai
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Summarize(),
  ]
)

output = pipeline.run(text)
print(output)
```



2. Paste your API Key instead of the `<YOUR-API-KEY-HERE>` placeholder.
3. `pip3 install oneai` or `npm install oneai` if you selected to use the `Python` or `Node.js` examples respectively.

## Run the sample

You should be getting an output similar to

```json JSON Response
{
  "input_text": "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "summarize",
      "text_generated_by_step_id": 1,
      "text": "60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020. A third said that spending climbed by more than 30%.",
      "labels": []
    }
  ],
  "stats": {
    "concurrency_wait_time": 0,
    "total_running_jobs": 1,
    "total_waiting_jobs": 0
  }
}
```
```json SDK Response
{
  text: 'Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%',
  summary: {
    text: '60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020. A third said that spending climbed by more than 30%.',
    origins: []
  }
}
```



## Congratulations!

You have run your first One AI Pipeline query. Too many more to come!
