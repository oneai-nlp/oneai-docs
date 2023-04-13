---
title: "Pricing"
slug: "pricing"
excerpt: "Detects pricing and quantities in documents and conversations, and extracts them to a consistent structured format.\nGenerates a new output."
hidden: false
createdAt: "2022-08-18T07:36:31.253Z"
updatedAt: "2023-04-02T15:26:51.297Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I'd like to exchange <span class=\"label_box\">PRICING</span><span class=\"label_text\"> $100</span>.\n\n</div>\n"
}
[/block]



> 📘 Use Pricing Skill to detect pricing in:
> 
> - [Articles](https://studio.oneai.com/?pipeline=4a2Sak)
> - [Conversations](https://studio.oneai.com/?pipeline=erWbyN)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type            | Name    |
| :-------------- | :------ |
| business-entity | pricing |

## Parameters

None.

## Example

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "For the second quarter, operating income was $241.8 million and net sales totaled $1.618 billion, a decrease of 5% from a year ago.",
    "input_type": "article",
    "steps": [
      {
        "skill": "business-entities"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "For the second quarter, operating income was $241.8 million and net sales totaled $1.618 billion, a decrease of 5% from a year ago.";
const pipeline = new oneai.Pipeline(
	oneai.skills.pricing(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "For the second quarter, operating income was $241.8 million and net sales totaled $1.618 billion, a decrease of 5% from a year ago."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Pricing(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json
{
  "input_text": "For the second quarter, operating income was $241.8 million and net sales totaled $1.618 billion, a decrease of 5% from a year ago.\n",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "business-entities",
      "text_generated_by_step_id": 1,
      "text": "For the second quarter,operating income was USD 241.8 million and net sales totaled USD 1.618 billion,a decrease of 5% from a year ago.",
      "labels": [
        {
          "type": "business-entity",
          "skill": "business-entities",
          "name": "pricing",
          "value": "USD 241.8",
          "data": {
            "amount": 241.8,
            "currency": "USD",
            "modifier": "",
            "unit": "",
            "is_primary_confidence": 0.5
          },
          "span_text": "USD 241.8",
          "span": [
            44,
            53
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 44,
              "end": 53
            }
          ]
        },
        {
          "type": "business-entity",
          "skill": "business-entities",
          "name": "pricing",
          "value": "net sales totaled USD 1.618",
          "data": {
            "amount": 1.618,
            "currency": "USD",
            "modifier": "net",
            "unit": "",
            "is_primary_confidence": 0.5
          },
          "span_text": "net sales totaled USD 1.618",
          "span": [
            66,
            93
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 66,
              "end": 93
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