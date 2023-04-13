---
title: "Highlights"
slug: "highlights"
excerpt: "Finds **spans** in the text with the most important information."
hidden: false
createdAt: "2022-08-16T20:40:13.021Z"
updatedAt: "2023-04-02T15:22:42.626Z"
---
[block:html]
{
  "html": "  <div class=\"example_box\">\n    The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves.<br/>\n    <span class=\"label_box\">HIGHLIGHT</span><span class=\"label_text\"> Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. </span>\n    Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, \"cognitive\" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.\n</div>"
}
[/block]



> 📘 Use Highlights Skill to extract highlights from
> 
> - [Articles](https://studio.oneai.com/?pipeline=LmQfjT)
> - [Conversations](https://studio.oneai.com/?pipeline=hGy7VM)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type      | Value                |
| :-------- | :------------------- |
| highlight | The highlighted text |

## Parameters

| Name     | Type   | Description                                                                       | Default  |
| :------- | :----- | :-------------------------------------------------------------------------------- | :------- |
| `amount` | string | The amount of highlights to return. valid values are `less`, `normal` and `more`. | `normal` |

## Example

#### Request

```curl
curl -X POST \
'https://staging.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, "cognitive" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.",
    "steps": [
      {
        "skill": "highlights"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract,\"cognitive\" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.";
const pipeline = new oneai.Pipeline(
	oneai.skills.highlights(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, "cognitive" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Highlights(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
   "input_text":"The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, cognitive aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.",
   "status":"success",
   "output":[
      {
         "text_generated_by_step_name":"input",
         "text_generated_by_step_id":0,
         "text":"The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, cognitive aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.",
         "labels":[
            {
               "type":"highlight",
               "skill":"highlights",
               "value":"The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves.",
               "data":{
                  "score":"0.344"
               },
               "span_text":"The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves.",
               "span":[
                  0,
                  155
               ],
               "output_spans":[
                  {
                     "section":0,
                     "start":0,
                     "end":155
                  }
               ]
            },
            {
               "type":"highlight",
               "skill":"highlights",
               "value":"Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation.",
               "data":{
                  "score":"0.442"
               },
               "span_text":"Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation.",
               "span":[
                  156,
                  301
               ],
               "output_spans":[
                  {
                     "section":0,
                     "start":156,
                     "end":301
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
  text: 'The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation. Based on long-standing trends in the field, it is possible to extrapolate future directions of NLP. As of 2020, three trends among the topics of the long-standing series of CoNLL Shared Tasks can be observed: Interest on increasingly abstract, "cognitive" aspects of natural language, Increasing interest in multilinguality and Elimination of symbolic representations.',
  highlights: [
    {
      type: 'highlight',
      skill: 'highlights',
      value: 'The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves.',
      data: { score: '0.344' },
      span_text: 'The technology can then accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves.',
      span: [ 0, 155 ],
      output_spans: [ { section: 0, start: 0, end: 155 } ]
    },
    {
      type: 'highlight',
      skill: 'highlights',
      value: 'Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation.',
      data: { score: '0.442' },
      span_text: 'Challenges in natural language processing frequently involve speech recognition, natural language understanding, and natural language generation.',
      span: [ 156, 301 ],
      output_spans: [ { section: 0, start: 156, end: 301 } ]
    }
  ]
}
```