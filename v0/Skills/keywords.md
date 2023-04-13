---
title: "Keywords"
slug: "keywords"
excerpt: "**Extracts** keywords from the input text."
hidden: false
createdAt: "2022-08-17T10:44:37.492Z"
updatedAt: "2023-04-02T16:00:34.206Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\nIn an effort to expand its <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">KEYWORD</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> social platform</span> for<span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">KEYWORD</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> virtual reality</span>, <span style=\"box-sizing: border-box; border-width: 0px; border-style: solid; border-bottom-left-radius: 0.25rem; border-top-left-radius: 0.25rem; border-top-right-radius: 0.25rem; background-color: rgb(241, 59, 233); color: white; padding: 2px; outline-style: none;\">KEYWORD</span><span style=\"box-sizing: border-box; border-width: 0px 0px 2px; border-style: solid; border-color: rgb(241, 59, 233);\"> Horizon Worlds</span>, Meta is launching it in France and Spain today — building on the existing three markets including the U.S., Canada, and the UK where it was already available. In a Facebook post, Mark Zuckerberg announced the launch with an unappealing photo and noted that it plans to expand the platform to more countries.    \n</div>"
}
[/block]



> 📘 Use Keyword Skill to extract:
> 
> - [Keywords from articles](https://studio.oneai.com/?pipeline=kdDbHP)
> - [Keywords from conversations](https://studio.oneai.com/?pipeline=y9W23K)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type    | Name             | Value           |
| :------ | :--------------- | :-------------- |
| keyword | The keyword text | Relevance score |

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
    "input": "Tesla, Inc. is an American multinational automotive and clean energy company headquartered in Austin, Texas. Tesla designs and manufactures electric vehicles (electric cars and trucks), battery energy storage from home to grid-scale, solar panels and solar roof tiles, and related products and services. ",
    "steps": [
      {
        "skill": "keywords"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "Tesla, Inc. is an American multinational automotive and clean energy company headquartered in Austin, Texas. Tesla designs and manufactures electric vehicles (electric cars and trucks), battery energy storage from home to grid-scale, solar panels and solar roof tiles, and related products and services. ";
const pipeline = new oneai.Pipeline(
	oneai.skills.topics(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "Tesla, Inc. is an American multinational automotive and clean energy company headquartered in Austin, Texas. Tesla designs and manufactures electric vehicles (electric cars and trucks), battery energy storage from home to grid-scale, solar panels and solar roof tiles, and related products and services. "
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
  "input_text": "Tesla, Inc. is an American multinational automotive and clean energy company headquartered in Austin, Texas. Tesla designs and manufactures electric vehicles (electric cars and trucks), battery energy storage from home to grid-scale, solar panels and solar roof tiles, and related products and services. ",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "Tesla, Inc. is an American multinational automotive and clean energy company headquartered in Austin, Texas. Tesla designs and manufactures electric vehicles (electric cars and trucks), battery energy storage from home to grid-scale, solar panels and solar roof tiles, and related products and services. ",
      "labels": [
        {
          "type": "keyword",
          "skill": "keywords",
          "name": "electric vehicles",
          "value": 0.098,
          "span_text": "electric vehicles",
          "span": [
            140,
            157
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 140,
              "end": 157
            }
          ]
        },
        {
          "type": "keyword",
          "skill": "keywords",
          "name": "tesla",
          "value": 0.085,
          "span_text": "Tesla",
          "span": [
            0,
            5
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 0,
              "end": 5
            }
          ]
        },
        {
          "type": "keyword",
          "skill": "keywords",
          "name": "tesla",
          "value": 0.085,
          "span_text": "Tesla",
          "span": [
            109,
            114
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 109,
              "end": 114
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
  text: 'Tesla, Inc. is an American multinational automotive and clean energy company headquartered in Austin, Texas. Tesla designs and manufactures electric vehicles (electric cars and trucks), battery energy storage from home to grid-scale, solar panels and solar roof tiles, and related products and services. ',
  topics: [
    { type: 'topic', skill: 'article-topics', value: 'Clean Energy' },
    { type: 'topic', skill: 'article-topics', value: 'Tesla' },
    { type: 'topic', skill: 'article-topics', value: 'Storage' },
    { type: 'topic', skill: 'article-topics', value: 'Tesla, Inc.' },
    { type: 'topic', skill: 'article-topics', value: 'Electric Vehicles'},
    { type: 'topic', skill: 'article-topics', value: 'Home' },
    { type: 'topic', skill: 'article-topics', value: 'Grid' }
  ]
}
```