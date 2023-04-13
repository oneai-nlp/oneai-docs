---
title: "Split by Sentence"
slug: "split-by-sentence"
excerpt: "Splits input content into sentences."
hidden: false
createdAt: "2022-08-17T11:40:05.631Z"
updatedAt: "2023-04-02T15:59:44.688Z"
---
[block:html]
{
  "html": "<div style=\"max-width: 40rem; margin: 0 auto; background-color: rgb(17,140,243,.1); padding: 18px; line-height: 28px;\">\n<span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">SENTENCES</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> Old McDonald had a farm.</span> <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">SENTENCES</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> And in the farm he had a cow.</span>\n</div>"
}
[/block]



> 📘 Use Split by Sentence Skill to:
> 
> - [Split conversation to sentences](https://studio.oneai.com/?pipeline=tiMl8V)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type     | Value             |
| :------- | :---------------- |
| sentence | The sentence text |

## Parameters

This skill takes no parameters as input.

## Example

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "Old McDonald had a farm. And in the farm he had a cow.",
    "steps": [
      {
        "skill": "sentences"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "Old McDonald had a farm. And in the farm he had a cow.";
const pipeline = new oneai.Pipeline(
	oneai.skills.splitBySentence(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "Old McDonald had a farm. And in the farm he had a cow."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.SplitBySentence(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "Old McDonald had a farm. And in the farm he had a cow.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "Old McDonald had a farm. And in the farm he had a cow.",
      "labels": [
        {
          "type": "sentence",
          "skill": "sentences",
          "value": "Old McDonald had a farm.",
          "span_text": "Old McDonald had a farm.",
          "span": [
            0,
            24
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 0,
              "end": 24
            }
          ]
        },
        {
          "type": "sentence",
          "skill": "sentences",
          "value": "And in the farm he had a cow.",
          "span_text": "And in the farm he had a cow.",
          "span": [
            25,
            54
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 25,
              "end": 54
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
  text: 'Old McDonald had a farm. And in the farm he had a cow.',
  sentences: [
    {
      type: 'sentence',
      skill: 'sentences',
      value: 'Old McDonald had a farm.',
      span_text: 'Old McDonald had a farm.',
      span: [ 0, 24 ],
      output_spans: [ { section: 0, start: 0, end: 24 } ]
    },
    {
      type: 'sentence',
      skill: 'sentences',
      value: 'And in the farm he had a cow.',
      span_text: 'And in the farm he had a cow.',
      span: [ 25, 54 ],
      output_spans: [ { section: 0, start: 25, end: 54 } ]
    }
  ]
}
```