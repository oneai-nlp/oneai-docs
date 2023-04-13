---
title: "Split by Topic"
slug: "split-by-topic"
excerpt: "Splits input content by topics."
hidden: false
createdAt: "2022-08-17T12:12:01.091Z"
updatedAt: "2023-04-02T16:00:47.541Z"
---
[block:html]
{
  "html": "<div  class=\"example_box\">\nJosh: <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">DIALOGUE-SEGMENTATION</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> Do you like math?<br/>\nMellisa: I like it but I'm not so good at it<br/>\nJosh: what was your last grade?<br/>\n  Mellisa: I got a C last year.</span><br/>\nJosh: <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">DIALOGUE-SEGMENTATION</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> Did you hear about Donald Trump last issue?<br/>\n  Mellisa: No. What did he do this time?</span><br/>\n</div>"
}
[/block]



> 📘 Use Split by Topic Skill to:
> 
> - [Split conversation by topics](https://studio.oneai.com/?pipeline=P8zkMh)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type             |
| :--------------- |
| dialogue-segment |

## Optional Parameters

| Name     | Type   | Description                                                                                    | Default  |
| :------- | :----- | :--------------------------------------------------------------------------------------------- | :------- |
| `amount` | number | The amount of topics the text will be split by. Any value of `less`,`normal`, `more` is valid. | `normal` |

## Example

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": [{ "speaker": "Josh", "utterance": "Do you like math?", "timestamp": "0:00" }, { "speaker": "Mellisa", "utterance": "I like it but I'\''m not so good at it", "timestamp": "0:00" }, { "speaker": "Josh", "utterance": "...", "timestamp": "..." }],
    "input_type": "conversation",
		"content_type": "application/json",
    "steps": [
      {
        "skill": "dialogue-segmentation"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const conversation = new oneai.Conversation(
  [{ "speaker": "Josh", "utterance": "Do you like math?", "timestamp": "0:00" }, { "speaker": "Mellisa", "utterance": "I like it but I'm not so good at it", "timestamp": "0:00" }, { "speaker": "Josh", "utterance": "...", "timestamp": "..." }]
);

const pipeline = new oneai.Pipeline(
	oneai.skills.splitByTopic(),
);

pipeline.run(conversation).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.SplitByTopic(),
  ]
)

conversation = oneai.Conversation(
  [{ "speaker": "Josh", "utterance": "Do you like math?", "timestamp": "0:00" }, { "speaker": "Mellisa", "utterance": "I like it but I'm not so good at it", "timestamp": "0:00" }, { "speaker": "Josh", "utterance": "...", "timestamp": "..." }]
)

output = pipeline.run(conversation)
```



#### Response

```json API Response
{
  "input_text": "Josh:\nDo you like math?\n\nMellisa:\nI like it but I'm not so good at it\n\nJosh:\nwhat was your last grade?\n\nMellisa:\nI got a C last year.\n\nJosh:\nDid you hear about Donald Trump last issue?\n\nMellisa:\nNo. What did he do this time?\n\n",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "Josh:\nDo you like math?\n\nMellisa:\nI like it but I'm not so good at it\n\nJosh:\nwhat was your last grade?\n\nMellisa:\nI got a C last year.\n\nJosh:\nDid you hear about Donald Trump last issue?\n\nMellisa:\nNo. What did he do this time?\n\n",
      "labels": [
        {
          "type": "dialogue-segment",
          "skill": "dialogue-segmentation",
          "speaker": "Mellisa,Josh",
          "data": {
            "subheading": "Do you like math?"
          },
          "span_text": "Do you like math?\n\nMellisa:\nI like it but I'm not so good at it\n\nJosh:\nwhat was your last grade?\n\nMellisa:\nI got a C last year.",
          "span": [
            6,
            133
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 0,
              "end": 17
            },
            {
              "section": 1,
              "start": 0,
              "end": 35
            },
            {
              "section": 2,
              "start": 0,
              "end": 25
            },
            {
              "section": 3,
              "start": 0,
              "end": 20
            }
          ]
        },
        {
          "type": "dialogue-segment",
          "skill": "dialogue-segmentation",
          "speaker": "Mellisa,Josh",
          "data": {
            "subheading": "Did you hear about Donald Trump?"
          },
          "span_text": "Did you hear about Donald Trump last issue?\n\nMellisa:\nNo. What did he do this time?",
          "span": [
            141,
            224
          ],
          "output_spans": [
            {
              "section": 4,
              "start": 0,
              "end": 43
            },
            {
              "section": 5,
              "start": 0,
              "end": 29
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
  text: '[0:00] Josh:\n' +
    'Do you like math?\n' +
    '\n' +
    '[0:00] Mellisa:\n' +
    "I like it but I'm not so good at it\n" +
    '\n' +
    '[...] Josh:\n' +
    '...\n' +
    '\n',
  segments: [
    {
      type: 'dialogue-segment',
      skill: 'dialogue-segmentation',
      speaker: 'Mellisa,Josh',
      span_text: 'Do you like math?\n' +
        '\n' +
        '[0:00] Mellisa:\n' +
        "I like it but I'm not so good at it\n" +
        '\n' +
        '[...] Josh:\n' +
        '...',
      span: [ 13, 100 ],
      output_spans: [
        { section: 0, start: 0, end: 17 },
        { section: 1, start: 0, end: 35 },
        { section: 2, start: 0, end: 3 }
      ],
      data: { 
        subheading: 'Do you like math?' 
      }
    }
  ]
}
```



#### Additional Data

Each segment will contain a `subheading`, generated by the [Subheading](doc:subheading) skill in the `data` field