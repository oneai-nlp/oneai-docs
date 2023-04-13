---
title: "Numbers & Time"
slug: "numbers"
excerpt: "Extracts **values** of numbers, dates and times, along with the corresponding span in the text.\nAlso **identifies** the number type (Money, Quantity, Ordinals, etc.) and the Date/Time type (Date, Duration, Time)"
hidden: false
createdAt: "2022-08-23T07:01:40.547Z"
updatedAt: "2023-04-02T15:25:40.136Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I bought this land <span class=\"label_box\">DATE\n  <div class=\"tooltip\">{<br> \n    &nbsp;&nbsp;&nbsp;\"date_time\": \"2012-08-17T00:00\",<br> \n    &nbsp;&nbsp;&nbsp;\"timezone\": \"US/Eastern\",<br>\n    &nbsp;&nbsp;&nbsp;\"precision\": \"DAY\"<br> \n    }</div>\n  </span><span class=\"label_text\"> ten years ago</span> for <span class=\"label_box\">MONEY</span><span class=\"label_text\"> two thousands bucks</span>. <span class=\"label_box\">DATE</span><span class=\"label_text\"> Now</span> I can sell it for <span class=\"label_box\">MONEY</span><span class=\"label_text\"> a hundred grand</span>.\n  <br>&nbsp;\n  <br>&nbsp;\n  <br>&nbsp;\n</div>\n"
}
[/block]



> 📘 Use Numbers & Time Skill to extract numbers and time from:
> 
> - [Articles](https://studio.oneai.com/?pipeline=CuysJH)
> - [Email threads](https://studio.oneai.com/?pipeline=bFfOWf)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

### Date & Time labels

- [DATE](doc:date-label)  - Specific date & time: _"let's meet next Monday at 3pm"_->'2022-09-02T15:00'
- [TIME](doc:time-label) -  Specific time, with unspecified date: _"let's meet at 3pm"_->'15:00'
- [DURATION](doc:duration-label)  -  A time duration, unspecified date or time: _"let's meet for 3 hours"_->'0.3:00:00'

### Numbers labels

- [MONEY](doc:money-label) 
- [NUMBER](doc:number-label) 
- [ORDINAL](doc:ordinal-label) 
- [QUANTITY](doc:quantity-label)

## Parameters

| Name             | Type                                | Description                                                                                                                                                                                      | Default                              |
| :--------------- | :---------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------- |
| `reference_time` | `yyyy-mm-ddTHH:MM` formatted string | The time & date are used for relative dates calculations. For example,  if `reference_time` is set to January 1st, 1990, then any mention of `tomorrow` will be calculated as January 2nd, 1990. | The current date & time will be used |

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "I bought this land ten years ago for two thousands bucks. Now I can sell it for a hundred grand.",
    "input_type": "article",
    "steps": [
      {
        "skill": "numbers"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "I bought this land ten years ago for two thousands bucks. Now I can sell it for a hundred grand.";
const pipeline = new oneai.Pipeline(
	oneai.skills.numbers(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "I bought this land ten years ago for two thousands bucks. Now I can sell it for a hundred grand."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Numbers(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "I bought this land ten years ago for two thousands bucks. Now I can sell it for a hundred grand.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "I bought this land ten years ago for two thousands bucks. Now I can sell it for a hundred grand.",
      "labels": [
        {
          "type": "number",
          "skill": "numbers",
          "name": "DATE",
          "value": "2012-08-17",
          "data": {
            "date_time": "2012-08-17T00:00",
            "timezone": null,
            "precision": "DAY"
          },
          "span_text": "ten years ago",
          "span": [
            19,
            32
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 19,
              "end": 32
            }
          ]
        },
        {
          "type": "number",
          "skill": "numbers",
          "name": "MONEY",
          "value": "2",
          "data": {
            "numeric_value": 2
          },
          "span_text": "two thousands bucks",
          "span": [
            37,
            56
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 37,
              "end": 56
            }
          ]
        },
        {
          "type": "number",
          "skill": "numbers",
          "name": "DATE",
          "value": "2022-08-17",
          "data": {
            "date_time": "2022-08-17T00:00",
            "timezone": null,
            "precision": "DAY"
          },
          "span_text": "Now",
          "span": [
            58,
            61
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 58,
              "end": 61
            }
          ]
        },
        {
          "type": "number",
          "skill": "numbers",
          "name": "MONEY",
          "value": "1,100",
          "data": {
            "numeric_value": 1100
          },
          "span_text": "a hundred grand",
          "span": [
            80,
            95
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 80,
              "end": 95
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
  text: 'I bought this land ten years ago for two thousands bucks. Now I can sell it for a hundred grand.',
  numbers: [
    {
      type: 'number',
      skill: 'numbers',
      name: 'DATE',
      value: '2012-08-23',
      data: {
        date_time: '2012-08-23T00:00',
        timezone: null,
        precision: 'DAY'
      },
      span_text: 'ten years ago',
      span: [ 19, 32 ],
      output_spans: [ { section: 0, start: 19, end: 32 } ]
    },
    {
      type: 'number',
      skill: 'numbers',
      name: 'MONEY',
      value: '2',
      data: { numeric_value: 2 },
      span_text: 'two thousands bucks',
      span: [ 37, 56 ],
      output_spans: [ { section: 0, start: 37, end: 56 } ]
    },
    {
      type: 'number',
      skill: 'numbers',
      name: 'DATE',
      value: '2022-08-23',
      data: {
        date_time: '2022-08-23T00:00',
        timezone: null,
        precision: 'DAY'
      },
      span_text: 'Now',
      span: [ 58, 61 ],
      output_spans: [ { section: 0, start: 58, end: 61 } ]
    },
    {
      type: 'number',
      skill: 'numbers',
      name: 'MONEY',
      value: '1,100',
      data: { numeric_value: 1100 },
      span_text: 'a hundred grand',
      span: [ 80, 95 ],
      output_spans: [ { section: 0, start: 80, end: 95 } ]
    }
  ]
}
```