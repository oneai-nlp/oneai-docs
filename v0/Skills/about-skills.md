---
title: "What are 'Skills' ?"
slug: "about-skills"
hidden: false
createdAt: "2022-08-17T06:40:21.725Z"
updatedAt: "2023-01-12T08:38:20.064Z"
---
## Language Skills

A Language Skill is a package of trained NLP models, available via API. Skills accept the text as input in various formats and respond with processed texts and extracted metadata.

Examples:

- Use the `Summarize` Skill to summarize an article or conversation. 
- Use the `Sentiments` Skill to extract sentiments (`positive` or `negative`) from a chatbot session.
- Use the `Sales-Insights` Skill to extract insights (like `needs` and `features`) from sales calls.

## Pipelines

Language Skills are the building stones of the Pipeline API. The pipeline API allows invoking and chaining multiple Skills to process your input text with a single API call. Pipelines can be defined by listing the desired Skills.

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "I feel very bad about hurting Michelle the other day.",
    "steps": [
      {
        "skill": "sentiments"
      },   
      {
        "skill": "emotions"
      }   
    ]
}'
```
```javascript Node.js
const OneAI = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "I feel very bad about hurting Michelle the other day.";
const pipeline = new oneai.Pipeline(
	oneai.skills.sentiments(),
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
		oneai.skills.Sentiments(),
		oneai.skills.Emotions(),
  ]
)

output = pipeline.run(text)
```



## Generator Skills vs. Analyzer Skills (why the order is important)

Some skills, e.g. `Summarize` generate new text based on the input. Other skills. e.g. `Emotions`, simply extract information from the input without altering it.  
When a Skill generates new text, the next skill in the pipeline will use the generated text as input. An analyzer skill simply "passes" the input as it is to the next skill.  
In this way when running the two Skills `Emotions` and `Summarize`, if `Emotions` is first it will extract emotions from the input text, but if it is second it will extract emotions from the summary.

```javascript Node.js
const OneAI = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "I feel very bad about hurting Michelle the other day.";
const pipeline = new oneai.Pipeline(
	oneai.skills.sentiments(), // extracts sentiments from the original input
	oneai.skills.summarize(),  // summarizes the original input
	oneai.skills.sentiments(), // extracts sentiments from the generated summary
);

pipeline.run(text).then(console.log);
```



## Generated Text

When a Skill generates text, you can find it in the response object under `output.text`

```javascript Node.js
const OneAI = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "I feel very bad about hurting Michelle the other day.";
const pipeline = new oneai.Pipeline(
	oneai.skills.summarize(),
);

pipeline.run(text).then(console.log);
```



## Labels

Most Skills return information in the `labels` array. A label describes the indices of specific words and sentences in the text that the skill extracted. 

```json
{
  "type": "emotion",
  "skill": "emotions",
  "name": "happiness",
  "span_text": "I was delighted to wake up and found out we won another two medals during the night.",
  "span": [
    29,
    113
  ],
  "output_spans": [
    {
      "section": 0,
      "start": 29,
      "end": 113
    }
  ]
}
```



### Label Properties

| Property Name | Description                                                                   |
| :------------ | :---------------------------------------------------------------------------- |
| type          | the type of the label                                                         |
| skill         | the skill that generated the label                                            |
| name          | the name of the label                                                         |
| value         | the value of the label                                                        |
| data          | additional data                                                               |
| span_text     | the portion of the input text that the label applies to                       |
| span          | the indices of `span_text` in the input.                                      |
| output_spans  | the indices of `span_text` in the output, in case the new text was generated. |
| input_spans   | the indices of `span_text` in the input                                       |
| timestamp     | audio indices, in case the origin of the text is audio                        |
| timestamp_end | audio indices, in case the origin of the text is audio                        |