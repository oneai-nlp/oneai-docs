---
title: "Proofread"
slug: "proofread"
excerpt: "Fixes typos, duplicate words, etc.\nGenerates a new output."
hidden: false
createdAt: "2022-08-17T11:31:16.744Z"
updatedAt: "2023-04-02T15:35:24.371Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\nThere was a <span class=\"label_box\"> block</span> nearby.\n</div>"
}
[/block]



> 📘 Use Proofread Skill to proofread:
> 
> - [transcriptions](https://studio.oneai.com/?pipeline=UCTKWP)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type        | Value                           |
| :---------- | :------------------------------ |
| replacement | The text to replace the indices |

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
    "input": [{ "speaker": "John", "utterance": "There was a second second accident at the same time in the blok nearby.", "timestamp": "0:00" }, { "speaker": "speaker 2", "utterance": "..." }],
		"content_type": "application/json",
    "steps": [
      {
        "skill": "enhance"
      }   
    ]
}'
```
```javascript Node.js
const OneAI = require("oneai");
const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const conversation = new oneai.Conversation(
  [{ "speaker": "John", "utterance": "There was a second second accident at the same time in the blok nearby.", "timestamp": "0:00" }, { "speaker": "speaker 2", "utterance": "..." }]
);

const pipeline = new oneai.Pipeline(
	oneai.skills.proofread(),
);

pipeline.run(conversation).then(consol.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Proofread(),
  ]
)

conversation = oneai.Conversation(
  [{ "speaker": "John", "utterance": "There was a second second accident at the same time in the blok nearby.", "timestamp": "0:00" }, { "speaker": "speaker 2", "utterance": "..." }]
)

output = pipeline.run(conversation)
```



#### Response

```json API Response
{
  "input_text": "John:\nThere was a second second accident at the same time in the blok nearby.\n\n",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "enhance",
      "text_generated_by_step_id": 1,
      "text": "John:\nThere was a second accident at the same time in the block nearby.\n\n",
      "labels": [
        {
          "type": "replacement",
          "skill": "enhance",
          "value": "second",
          "speaker": "John",
          "span_text": "",
          "span": [
            18,
            18
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 12,
              "end": 12
            }
          ]
        },
        {
          "type": "replacement",
          "skill": "enhance",
          "value": "blok",
          "speaker": "John",
          "span_text": "block",
          "span": [
            58,
            63
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 52,
              "end": 57
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
  text: '[0:00] John:\n' +
    'There was a second second accident at the same time in the blok nearby.\n' +
    '\n' +
    'speaker 2:\n' +
    '...\n' +
    '\n',
  proofread: {
    text: '[0:00] John:\n' +
      'There was a second accident at the same time in the block nearby.\n' +
      '\n' +
      'speaker 2:\n' +
      '\n' +
      '\n',
    replacements: [
      {
        type: 'replacement',
        skill: 'enhance',
        value: 'second',
        speaker: 'John',
        span_text: '',
        span: [ 25, 25 ],
        output_spans: [ { section: 0, start: 12, end: 12 } ]
      },
      {
        type: 'replacement',
        skill: 'enhance',
        value: 'blok',
        speaker: 'John',
        span_text: 'block',
        span: [ 65, 70 ],
        output_spans: [ { section: 0, start: 52, end: 57 } ]
      },
      {
        type: 'replacement',
        skill: 'enhance',
        value: '...',
        speaker: 'speaker 2',
        span_text: '',
        span: [ 91, 91 ],
        output_spans: [ { section: 1, start: 0, end: 0 } ]
      }
    ]
  }
}
```