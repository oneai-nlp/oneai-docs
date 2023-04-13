---
title: "Sentiments"
slug: "sentiments"
excerpt: "Finds **spans** in the text with Sentiment, and **identifies** the Sentiment (Positive/Negative)."
hidden: false
createdAt: "2022-08-16T13:24:33.244Z"
updatedAt: "2023-04-02T16:00:14.025Z"
---
[block:html]
{
  "html": "  <div class=\"example_box\">\n    <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">POSITIVE</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> The price is great.</span> \n    (in my opinion)\n    <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">NEGATIVE</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> but the battery life on this camera is not the best I've seen...</span>\n</div>"
}
[/block]



> 📘 Use Sentiment Skill to extract:
> 
> - [Sentiments from chat bot conversations](https://studio.oneai.com/?pipeline=mnqu4U)
> - [Sentiments from e-commerce reviews](https://studio.oneai.com/?pipeline=vWQyml)
> - [Sentiments from user comments](https://studio.oneai.com/?pipeline=tMnZmQ)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

- [POS](doc:pos-label) 
- [NEG](doc:neg-label) 

## Parameters

None.

## Example

#### Request

```curl
curl -X POST \
'https://staging.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "I feel very bad about hurting Michelle the other day.",
    "steps": [
      {
        "skill": "sentiments"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "I feel very bad about hurting Michelle the other day.";
const pipeline = new oneai.Pipeline(
	oneai.skills.sentiments(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "I feel very bad about hurting Michelle the other day."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Sentiments(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "I feel very bad about hurting Michelle the other day.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "I feel very bad about hurting Michelle the other day.",
      "labels": [
        {
          "type": "sentiment",
          "skill": "sentiments",
          "value": "NEG",
          "span_text": "I feel very bad about hurting Michelle the other day.",
          "span": [
            0,
            53
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 0,
              "end": 53
            }
          ]
        }
      ]
    }
  ],
  "stats": {
    "concurrency_wait_time": 0,
    "total_running_jobs": 1,
    "total_waiting_jobs": 0
  }
}
```
```json SDKs Response
{
  text: 'I feel very bad about hurting Michelle the other day.',
  sentiments: [
    {
      type: 'sentiment',
      skill: 'sentiments',
      value: 'NEG',
      span_text: 'I feel very bad about hurting Michelle the other day.',
      span: [ 0, 53 ],
      output_spans: [ { section: 0, start: 0, end: 53 } ]
    }
  ]
}
```