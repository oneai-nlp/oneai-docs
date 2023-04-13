---
title: "Headline"
slug: "headline"
excerpt: "**Generates** an appropriate headline for the input text."
hidden: false
createdAt: "2022-08-28T11:16:42.912Z"
updatedAt: "2023-04-02T15:22:35.630Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n    <span class=\"label_box\">Natural language processing (NLP)</span>\n   <br/>\n\tNatural language processing (NLP) is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data...\n</div>"
}
[/block]



> 📘 Use Headline Skill to generate headlines for:
> 
> - [Articles](https://studio.oneai.com/?pipeline=8p3e5Y)
> - [Conversations](https://studio.oneai.com/?pipeline=42CdtX)

> 🚦 [Benchmarks](https://docs.oneai.com/docs/headline-benchmarks)
> 
> | [Grade](https://docs.oneai.com/docs/rouge-metrics-for-summary-headline) | Rouge1 | RougeL |                                                                   |
> | :---------------------------------------------------------------------- | :----- | :----- | :---------------------------------------------------------------- |
> | 🟢A+                                                                    | 48.6   | 46.1   | [read benchmark](https://docs.oneai.com/docs/headline-benchmarks) |

## Parameters

[block:parameters]
{
  "data": {
    "h-0": "Name",
    "h-1": "Type",
    "h-2": "Description",
    "h-3": "Default",
    "0-0": "`headlines_type`",
    "0-1": "string",
    "0-2": "Either `headline`, `clickbait`or `subheadings`  \n  \n- `headline`- a short and to the point headline  \n- `clickbait`- a headline that is meant to attract more visitors to an article  \n- `subheading`- generate a subheading, more appropriate for excerpts, etc.",
    "0-3": "`headline`",
    "1-0": "`variations`",
    "1-1": "number",
    "1-2": "number of optional headline labels to receive in the output",
    "1-3": "1"
  },
  "cols": 4,
  "rows": 2,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]

## 

## Example

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "Natural language processing (NLP) is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data. The goal is a computer capable of "understanding" the contents of documents, including the contextual nuances of the language within them. The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, "cognitive" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.",
    "input_type": "article",
    "steps": [
      {
        "skill": "headline"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "Natural language processing (NLP) is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data. The goal is a computer capable of "understanding" the contents of documents, including the contextual nuances of the language within them. The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, "cognitive" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.";
const pipeline = new oneai.Pipeline(
	oneai.skills.headline(),
);


pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "Natural language processing (NLP) is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data. The goal is a computer capable of "understanding" the contents of documents, including the contextual nuances of the language within them. The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, "cognitive" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Headline(),
  ]
)


output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "Natural language processing (NLP) is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data. The goal is a computer capable of \"understanding\" the contents of documents, including the contextual nuances of the language within them. The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, \"cognitive\" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "Natural language processing (NLP) is a subfield of linguistics, computer science, and artificial intelligence concerned with the interactions between computers and human language, in particular how to program computers to process and analyze large amounts of natural language data. The goal is a computer capable of \"understanding\" the contents of documents, including the contextual nuances of the language within them. The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, \"cognitive\" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.",
      "labels": [
        {
          "type": "headline",
          "skill": "headline",
          "value": "Natural Language Processing (NLP)"
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