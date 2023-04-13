---
title: "Service Insights"
slug: "email-insights"
excerpt: "Finds **spans** in the text with Service Insights."
hidden: false
createdAt: "2022-11-13T13:58:34.434Z"
updatedAt: "2023-04-02T15:21:28.218Z"
---
[block:html]
{
  "html": "  <div class=\"example_box\">\n       <p><span class=\"label_box\">INTRO</span><span class=\"label_text\"> Hi George,</p>\n    <p>Thought you might enjoy a quick video to learn how ACME CORP works.</p>\n    <p>ACME CORP requires no commitments and no minimum spend. <span class=\"label_box\">REQUEST</span><span class=\"label_text\"> Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!</p>\n    <p>Happy to extend up to $10k in labeling credits on us to help get you started.</p>  \n    <p><span class=\"label_box\">QUERY</span><span class=\"label_text\"> Interested in a walk-through from one of our NLP experts?</p>\n    <p><span class=\"label_box\">OUTRO</span><span class=\"label_text\"> Jeff.</p>  \n\n  </div>  \n"
}
[/block]



> 📘 Use Service Insights Skill to extract:
> 
> - [Service Insights from service emails](https://studio.oneai.com/?pipeline=n8cw9i)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

- [Intro](doc:intro-label) 
- [Outro](doc:outro-label) 
- [Request](doc:request-label) 
- [Query](doc:query-label) 
- [Complaint](doc:complaint-label)

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
    "input": "Hi George,\n\nThought you might enjoy a quick video to learn how ACME CORP works.\n\nACME CORP requires no commitments and no minimum spend. Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!\n\nHappy to extend up to $10k in labeling credits on us to help get you started.\n\nInterested in a walk-through from one of our NLP experts?\nJeff",
    "input_type": "article",
		"content_type": "application/json",
    "steps": [
      {
        "skill": "service-email-insights"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");
const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text =  "Hi George,\n\nThought you might enjoy a quick video to learn how ACME CORP works.\n\nACME CORP requires no commitments and no minimum spend. Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!\n\nHappy to extend up to $10k in labeling credits on us to help get you started.\n\nInterested in a walk-through from one of our NLP experts?\nJeff";

const pipeline = new oneai.Pipeline(
	oneai.skills.serviceInsights(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.ServiceInsights(),
  ]
)

text = "Hi George,\n\nThought you might enjoy a quick video to learn how ACME CORP works.\n\nACME CORP requires no commitments and no minimum spend. Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!\n\nHappy to extend up to $10k in labeling credits on us to help get you started.\n\nInterested in a walk-through from one of our NLP experts?\nJeff"

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input": [
    {
      "utterance": "Hi George,\n\nThought you might enjoy a quick video to learn how ACME CORP works.\n\nACME CORP requires no commitments and no minimum spend. Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!\n\nHappy to extend up to $10k in labeling credits on us to help get you started.\n\nInterested in a walk-through from one of our NLP experts?\nJeff"
    }
  ],
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "contents": [
        {
          "utterance": "Hi George,\n\nThought you might enjoy a quick video to learn how ACME CORP works.\n\nACME CORP requires no commitments and no minimum spend. Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!\n\nHappy to extend up to $10k in labeling credits on us to help get you started.\n\nInterested in a walk-through from one of our NLP experts?\nJeff"
        }
      ],
      "labels": [
        {
          "type": "service-email-insights",
          "skill": "service-email-insights",
          "name": "Intro",
          "value": "Hi George,",
          "span_text": "Hi George,",
          "span": [
            0,
            10
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 0,
              "end": 10
            }
          ]
        },
        {
          "type": "service-email-insights",
          "skill": "service-email-insights",
          "name": "Request",
          "value": "Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!",
          "span_text": "Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!",
          "span": [
            137,
            291
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 137,
              "end": 291
            }
          ]
        },
        {
          "type": "service-email-insights",
          "skill": "service-email-insights",
          "name": "Query",
          "value": "Interested in a walk-through from one of our NLP experts?",
          "span_text": "Interested in a walk-through from one of our NLP experts?",
          "span": [
            372,
            429
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 372,
              "end": 429
            }
          ]
        },
        {
          "type": "service-email-insights",
          "skill": "service-email-insights",
          "name": "Outro",
          "value": "Jeff",
          "span_text": "Jeff",
          "span": [
            430,
            434
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 430,
              "end": 434
            }
          ]
        }
      ]
    }
  ],
  "stats": {
    "concurrency_wait_time": 0,
    "total_running_jobs": 2,
    "total_waiting_jobs": 0
  }
}
```
```json SDKs Response
{
  text: '[0:01] agent:\n' +
    "Alright, hello. Hello. Is this over? Yes. Okay, good morning. This is Shlomi Cucinelli from ena dot, how are you? I'm fine. How are you? I'm doing well. My apologies for calling out of the blue the I noticed that you recently downloaded a paper of ours regarding AI driven business monitoring or anomaly detection, if you will. I was curious to see what drove your interest. I don't know if that was a good time, perhaps maybe later on is better?\n" +
    '\n' +
    '[0:28] customer:\n' +
    'Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.\n' +
    '\n' +
    '[...] agent:\n' +
    '...\n' +
    '\n',
  serviceInsights: [
    {
      type: 'sales-insights',
      skill: 'sales-insights',
      name: 'Timing & Process',
      value: 'Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.',
      speaker: 'customer',
      span_text: 'Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.',
      span: [ 479, 684 ],
      output_spans: [ { section: 1, start: 0, end: 205 } ]
    }
  ]
}
```