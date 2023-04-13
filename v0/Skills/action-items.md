---
title: "Action Items"
slug: "action-items"
excerpt: "Finds **spans** in the text with Action Items."
hidden: false
createdAt: "2022-08-17T07:34:21.388Z"
updatedAt: "2023-04-02T15:20:20.093Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">  \n  Alex:<br/>\n  How many participants and what time are you looking at? <span class=\"label_box\">ACTION_ITEM</span><span class=\"label_text\"> Let me know if you'd prefer to hop on a quick videochat tomorrow to go over all the logistics</span>.<br/><br/>\n  Justin:<br/>\n  Hi Alex! <span class=\"label_box\">ACTION-ITEM</span><span class=\"label_text\"> There are 12 of us, and I believe 8 will take part</span>.<br/><br/>\n  Alex:<br/>\n  <span class=\"label_box\">ACTION-ITEM</span><span class=\"label_text\"> I'll send over a call invite with a zoom link and look forward to chatting then!</span><br/><br/>\n  Justin:<br/>\n  Thank you!\n</div>"
}
[/block]



> 📘 Use Action-Items Skill to extract:
> 
> - [Action-Items from conversations](https://studio.oneai.com/?pipeline=npS6Gp)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type        | Value                     |
| :---------- | :------------------------ |
| action-item | The extracted action item |

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
    "input": [{ "speaker": "John", "utterance": "Yeah, I think so. So any d o t? What was that? Sorry? I cut out a little bit. Yeah, sure. Anna, Diane? Oh, God. Yeah, correct. Okay. Do you guys have a white paper or something I can take a look at on the website somewhere.", "timestamp": "0:00" }, { "speaker": "speaker 2", "utterance": "..." }],
    "input_type": "conversation",
		"content_type": "application/json",
    "steps": [
      {
        "skill": "action-items"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");
const oneai = new OneAI("<YOUR_API_KEY>");
const conversation = [
  {
    speaker: "John",
    utterance:
      "Yeah, I think so. So any d o t? What was that? Sorry? I cut out a little bit. Yeah, sure. Anna, Diane? Oh, God. Yeah, correct. Okay. Do you guys have a white paper or something I can take a look at on the website somewhere.",
    timestamp: "0:00",
  },
  { speaker: "speaker 2", utterance: "..." },
];

const pipeline = new oneai.Pipeline(oneai.skills.actionItems());

pipeline.run(conversation).then(console.log);

```
```python
import oneai

oneai.URL = "https://staging.oneai.com"

oneai.api_key = "<YOUR_API_KEY>"
pipeline = oneai.Pipeline(
    steps=[
        oneai.skills.ActionItems(),
    ]
)

conversation = [
    oneai.Utterance("John", "Yeah, I think so. So any d o t? What was that? Sorry? I cut out a little bit. Yeah, sure. Anna, Diane? Oh, God. Yeah, correct. Okay. Do you guys have a white paper or something I can take a look at on the website somewhere."),
    oneai.Utterance("speaker 2", "..."),
]

output = pipeline.run(conversation)
print(output)
```



#### Response

```json API Response
{
   "input_text":"[0:00] John:\nYeah, I think so. So any d o t? What was that? Sorry? I cut out a little bit. Yeah, sure. Anna, Diane? Oh, God. Yeah, correct. Okay. Do you guys have a white paper or something I can take a look at on the website somewhere.\n\nspeaker 2:\n...\n\n",
   "status":"success",
   "output":[
      {
         "text_generated_by_step_name":"input",
         "text_generated_by_step_id":0,
         "text":"[0:00] John:\nYeah, I think so. So any d o t? What was that? Sorry? I cut out a little bit. Yeah, sure. Anna, Diane? Oh, God. Yeah, correct. Okay. Do you guys have a white paper or something I can take a look at on the website somewhere.\n\nspeaker 2:\n...\n\n",
         "labels":[
            {
               "type":"action-item",
               "skill":"action-items",
               "name":"Action item",
               "value":"Do you guys have a white paper or something I can take a look at on the website somewhere.",
               "speaker":"John",
               "span_text":"Do you guys have a white paper or something I can take a look at on the website somewhere.",
               "span":[
                  146,
                  236
               ],
               "output_spans":[
                  {
                     "section":0,
                     "start":133,
                     "end":223
                  }
               ]
            }
         ]
      }
   ],
   "stats":{
      "concurrency_wait_time":0.0,
      "total_running_jobs":1,
      "total_waiting_jobs":0
   }
}
```
```json SDKs Response
{
  text: '[0:00] John:\n' +
    'Yeah, I think so. So any d o t? What was that? Sorry? I cut out a little bit. Yeah, sure. Anna, Diane? Oh, God. Yeah, correct. Okay. Do you guys have a white paper or something I can take a look at on the website somewhere.\n' +
    '\n' +
    'speaker 2:\n' +
    '...\n' +
    '\n',
  actionItems: [
    {
      type: 'action-item',
      skill: 'action-items',
      name: 'Action item',
      value: 'Do you guys have a white paper or something I can take a look at on the website somewhere.',
      speaker: 'John',
      span_text: 'Do you guys have a white paper or something I can take a look at on the website somewhere.',
      span: [ 146, 236 ],
      output_spans: [ { section: 0, start: 133, end: 223 } ]
    }
  ]
}
```