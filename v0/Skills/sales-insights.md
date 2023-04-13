---
title: "Sales Insights"
slug: "sales-insights"
excerpt: "Finds **spans** in the text with Sales Insights."
hidden: false
createdAt: "2022-08-17T09:59:40.123Z"
updatedAt: "2023-04-02T15:26:58.648Z"
---
[block:html]
{
  "html": "  <div class=\"example_box\">\n   \n[0:52] Prospect:<br/>\n    Just sad. <span class=\"label_box\">NO INTEREST</span><span class=\"label_text\"> Like I don't like if you're selling me something you just done yourself a huge disservice.</span> Why are you calling me?\n  </div>  \n"
}
[/block]



> 📘 Use Sales Insights Skill to extract:
> 
> - [Sales Insights from sales calls](https://studio.oneai.com/?pipeline=n8cw9i)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

- [Competition](doc:competition-label) 
- [Needs & Features](doc:needs-and-features-label) 
- [Timing & Process](doc:timing-process-label) 
- [No Interest](doc:no-interest-label) 

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
    "input": [{ "speaker": "agent", "utterance": "Alright, hello. Hello. Is this over? Yes. Okay, good morning. This is Shlomi Cucinelli from ena dot, how are you? I'\''m fine. How are you? I'\''m doing well. My apologies for calling out of the blue the I noticed that you recently downloaded a paper of ours regarding AI driven business monitoring or anomaly detection, if you will. I was curious to see what drove your interest. I don'\''t know if that was a good time, perhaps maybe later on is better?", "timestamp": "0:01" }, { "speaker": "customer", "utterance": "Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.", "timestamp": "0:28" }, { "speaker": "agent", "utterance": "...", "timestamp": "..." }],
    "input_type": "conversation",
		"content_type": "application/json",
    "steps": [
      {
        "skill": "sales-insights"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");
const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const conversation = new oneai.Conversation(
  [{ "speaker": "agent", "utterance": "Alright, hello. Hello. Is this over? Yes. Okay, good morning. This is Shlomi Cucinelli from ena dot, how are you? I'm fine. How are you? I'm doing well. My apologies for calling out of the blue the I noticed that you recently downloaded a paper of ours regarding AI driven business monitoring or anomaly detection, if you will. I was curious to see what drove your interest. I don't know if that was a good time, perhaps maybe later on is better?", "timestamp": "0:01" }, { "speaker": "customer", "utterance": "Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.", "timestamp": "0:28" }, { "speaker": "agent", "utterance": "...", "timestamp": "..." }]
);

const pipeline = new oneai.Pipeline(
	oneai.skills.salesInsights(),
);

pipeline.run(conversation).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.SalesInsights(),
  ]
)

conversation = oneai.Conversation(
  [{ "speaker": "agent", "utterance": "Alright, hello. Hello. Is this over? Yes. Okay, good morning. This is Shlomi Cucinelli from ena dot, how are you? I'm fine. How are you? I'm doing well. My apologies for calling out of the blue the I noticed that you recently downloaded a paper of ours regarding AI driven business monitoring or anomaly detection, if you will. I was curious to see what drove your interest. I don't know if that was a good time, perhaps maybe later on is better?", "timestamp": "0:01" }, { "speaker": "customer", "utterance": "Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.", "timestamp": "0:28" }, { "speaker": "agent", "utterance": "...", "timestamp": "..." }]
)

output = pipeline.run(conversation)
```



#### Response

```json API Response
{
  "input_text": "[0:01] agent:\nAlright, hello. Hello. Is this over? Yes. Okay, good morning. This is Shlomi Cucinelli from ena dot, how are you? I'm fine. How are you? I'm doing well. My apologies for calling out of the blue the I noticed that you recently downloaded a paper of ours regarding AI driven business monitoring or anomaly detection, if you will. I was curious to see what drove your interest. I don't know if that was a good time, perhaps maybe later on is better?\n\n[0:28] customer:\nYeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.\n\n",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "[0:01] agent:\nAlright, hello. Hello. Is this over? Yes. Okay, good morning. This is Shlomi Cucinelli from ena dot, how are you? I'm fine. How are you? I'm doing well. My apologies for calling out of the blue the I noticed that you recently downloaded a paper of ours regarding AI driven business monitoring or anomaly detection, if you will. I was curious to see what drove your interest. I don't know if that was a good time, perhaps maybe later on is better?\n\n[0:28] customer:\nYeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.\n\n",
      "labels": [
        {
          "type": "sales-insights",
          "skill": "sales-insights",
          "name": "Timing & Process",
          "value": "Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.",
          "speaker": "customer",
          "span_text": "Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.",
          "span": [
            479,
            684
          ],
          "output_spans": [
            {
              "section": 1,
              "start": 0,
              "end": 205
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
  text: '[0:01] agent:\n' +
    "Alright, hello. Hello. Is this over? Yes. Okay, good morning. This is Shlomi Cucinelli from ena dot, how are you? I'm fine. How are you? I'm doing well. My apologies for calling out of the blue the I noticed that you recently downloaded a paper of ours regarding AI driven business monitoring or anomaly detection, if you will. I was curious to see what drove your interest. I don't know if that was a good time, perhaps maybe later on is better?\n" +
    '\n' +
    '[0:28] customer:\n' +
    'Yeah, I was just curious, because we are like in the beginning of looking at data governance solutions, but we are far away from from anything in the pipeline, or fourth, or just just information purposes.\n' +
    '\n' +
    '[...] agent:\n' +
    '...\n' +
    '\n',
  salesInsights: [
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