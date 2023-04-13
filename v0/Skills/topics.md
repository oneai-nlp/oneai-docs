---
title: "Topics"
slug: "topics"
excerpt: "**Generate** topic-labels representing the input text.\nCan be used for categorization and hash-tag creation."
hidden: false
createdAt: "2022-08-17T10:21:52.176Z"
updatedAt: "2023-04-02T15:28:04.568Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n    <span class=\"label_box\">#SPEECH RECOGNITION</span>\n\t\t<span class=\"label_box\">#ARTIFICIAL INTELLIGENCE</span>\n\t\t<span class=\"label_box\">#NLP</span>\n\t\t<span class=\"label_box\">#TRENDS</span>\n\t\t<span class=\"label_box\">#ABSTRACT</span>\n\t\t<span class=\"label_box\">#LINGUISTICS</span>\n\t\t<span class=\"label_box\">#NATURAL LANGUAGE</span>\n\t\t<span class=\"label_box\">#FUTURE</span>\n\t\t<span class=\"label_box\">#COMPUTER SCIENCE</span>\n   <br/>\n\tNatural language processing (NLP) is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data. The goal is a computer capable of \"understanding\" the contents of documents, including the contextual nuances of the language within them. The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, \"cognitive\" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.\n</div>\n"
}
[/block]



> 📘 Use Topics Skill to extract:
> 
> - [Topics from articles](https://studio.oneai.com/?pipeline=jbfy3F)
> - [Topics from conversations](https://studio.oneai.com/?pipeline=AIa79i)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type  | Value                |
| :---- | :------------------- |
| topic | The determined topic |

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
    "input": "After permanently banning parties and events on all Airbnb listings in June, the company is hardening its anti-party stance by launching new screening tools in the U.S. and Canada.",
    "steps": [
      {
        "skill": "article-topics"
      }
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "After permanently banning parties and events on all Airbnb listings in June, the company is hardening its anti-party stance by launching new screening tools in the U.S. and Canada.";
const pipeline = new oneai.Pipeline(
	oneai.skills.topics(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "After permanently banning parties and events on all Airbnb listings in June, the company is hardening its anti-party stance by launching new screening tools in the U.S. and Canada."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Topics(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "After permanently banning parties and events on all Airbnb listings in June, the company is hardening its anti-party stance by launching new screening tools in the U.S. and Canada.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "After permanently banning parties and events on all Airbnb listings in June, the company is hardening its anti-party stance by launching new screening tools in the U.S. and Canada.",
      "labels": [
        {
          "type": "topic",
          "skill": "article-topics",
          "value": "Listings"
        },
        {
          "type": "topic",
          "skill": "article-topics",
          "value": "Tools"
        },
        {
          "type": "topic",
          "skill": "article-topics",
          "value": "Airbnb"
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
  text: 'After permanently banning parties and events on all Airbnb listings in June, the company is hardening its anti-party stance by launching new screening tools in the U.S. and Canada.',
  topics: [
    { type: 'topic', skill: 'article-topics', value: 'Tools' },
    { type: 'topic', skill: 'article-topics', value: 'Airbnb' },
    { type: 'topic', skill: 'article-topics', value: 'Listings' }
  ]
}
```