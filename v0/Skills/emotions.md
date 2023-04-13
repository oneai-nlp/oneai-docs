---
title: "Emotions"
slug: "emotions"
excerpt: "Finds **spans** in the text with Emotions, and **identifies** the emotion (Happiness, Anger, etc.)."
hidden: false
createdAt: "2022-08-16T11:09:14.539Z"
updatedAt: "2023-04-02T15:17:47.549Z"
---
[block:html]
{
  "html": "  <div style=\"max-width: 40rem; margin: 0 auto; background-color: rgb(17, 140, 243, 0.1); padding: 18px; line-height: 28px;\">\n    \n    John: <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">SADNESS</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> Yesterday was very bad for me</span> <br/>\n    Jane: That's too bad how are you feeling today?<br/>\n    John: <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">HAPPINESS</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> I am having a great time with my kids</span> <br/>\n    Jane: keep it up!\n</div>"
}
[/block]



> 📘 Use Emotions Skill to extract:
> 
> - [Emotions from chat bot conversations](https://studio.oneai.com/?pipeline=us4m6c)
> - [Emotions from sales calls](https://studio.oneai.com/?pipeline=AXAnBX)
> - [Emotions from user comments](https://studio.oneai.com/?pipeline=tMnZmQ)

> 🚦 [Benchmarks](https://docs.oneai.com/docs/emotions-benchmarks)
> 
> | Grade | Accuracy | Precision | Recall |                                                                   |
> | :---- | :------- | :-------- | :----- | :---------------------------------------------------------------- |
> | 🟡B   | 75%      | 75%       | 75%    | [read benchmark](https://docs.oneai.com/docs/emotions-benchmarks) |

## Output labels

- [HAPPINESS](doc:happiness-label) 
- [SADNESS](doc:sadness-label) 
- [ANGER](doc:anger-label) 
- [SURPRISE](doc:surprise-label) 

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
        "skill": "emotions"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "I feel very bad about hurting Michelle the other day.";
const pipeline = new oneai.Pipeline(
	oneai.skills.emotions(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "I feel very bad about hurting Michelle the other day."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Emotions(),
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
          "type": "emotion",
          "skill": "emotions",
          "name": "sadness",
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
  emotions: [
    {
      type: 'emotion',
      skill: 'emotions',
      name: 'sadness',
      span_text: 'I feel very bad about hurting Michelle the other day.',
      span: [ 0, 53 ],
      output_spans: [ { section: 0, start: 0, end: 53 } ]
    }
  ]
}
```