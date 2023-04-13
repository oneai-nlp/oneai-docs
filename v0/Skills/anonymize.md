---
title: "Anonymize"
slug: "anonymize"
excerpt: "Removes Personally Identifiable Information (PII) from the input text.\nGenerates a new output."
hidden: false
createdAt: "2022-08-17T11:10:52.629Z"
updatedAt: "2023-04-02T15:17:36.559Z"
---
[block:html]
{
  "html": "<div style=\"max-width: 40rem; margin: 0 auto; background-color: rgb(17, 140, 243, 0.1); padding: 18px; line-height: 28px;\">\nThe names of the suspects are <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none; text-decoration: line-through;\">JOHN SMITH</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> ***</span> and <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none; text-decoration: line-through;\">Terra McDonald</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> ***</span>. You can reach their lawyer at <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none; text-decoration: line-through;\">MIKE@LAWYERS.COM</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> ***</span>.   \n</div>"
}
[/block]



> 📘 Use Anonymize Skill to anonymize:
> 
> - [articles](https://studio.oneai.com/?pipeline=DXewDG)
> - [conversations](https://studio.oneai.com/?pipeline=5c9bCp)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type       | Value               |
| :--------- | :------------------ |
| anonymized | The anonymized text |

## Parameters

None.

## Example

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR_API_KEY_HERE>' \
-d '{
    "input": "The name of the suspects are John Smith and Terra McDonald. You can reach their lawyer at mike@lawyers.com",
    "steps": [
      {
        "skill": "anonymize"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");
const oneai = new OneAI("<YOUR-API-KEY-HERE>")

const text =
  "The name of the suspects are John Smith and Terra McDonald. You can reach their lawyer at mike@lawyers.com";
const pipeline = new oneai.Pipeline(oneai.skills.anonymize());

pipeline
  .run(text)
  .then((o) => console.log(o))
  .catch(console.error);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "The name of the suspects are John Smith and Terra McDonald. You can reach their lawyer at mike@lawyers.com"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Anonymize(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "The name of the suspects are John Smith and Terra McDonald. You can reach their lawyer at mike@lawyers.com",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "anonymize",
      "text_generated_by_step_id": 1,
      "text": "The name of the suspects are *** and ***. You can reach their lawyer at ***",
      "labels": [
        {
          "type": "anonymized",
          "skill": "anonymize",
          "value": "John Smith",
          "span_text": "John Smith",
          "span": [
            29,
            32
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 29,
              "end": 32
            }
          ]
        },
        {
          "type": "anonymized",
          "skill": "anonymize",
          "value": "Terra McDonald",
          "span_text": "Terra McDonald",
          "span": [
            37,
            40
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 37,
              "end": 40
            }
          ]
        },
        {
          "type": "anonymized",
          "skill": "anonymize",
          "value": "mike@lawyers.com",
          "span_text": "mike@lawyers.com",
          "span": [
            72,
            75
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 72,
              "end": 75
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
  text: 'The name of the suspects are John Smith and Terra McDonald. You can reach their lawyer at mike@lawyers.com',
  anonymizations: {
    text: 'The name of the suspects are *** and ***. You can reach their lawyer at ***'
  }
}
```