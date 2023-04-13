---
title: "Names"
slug: "names"
excerpt: "Finds **spans** in the text with names, and **identifies** the name type (person, organization, location etc.)."
hidden: false
createdAt: "2022-08-17T12:27:58.729Z"
updatedAt: "2023-04-02T15:22:57.847Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n<span class=\"label_box\">PERSON</span><span class=\"label_text\"> Michael Jordan</span> \n  played most of his career in\n  <span class=\"label_box\">GEO <div class=\"tooltip\">{\n    <br>&nbsp;&nbsp;\"value\":\"New York City\",<br/>&nbsp;&nbsp;\"type\":\"CITY\"<br/>}</div>\n  </span><span class=\"label_text\"> NYC</span>.\n  <br/>&nbsp;\n</div>\n"
}
[/block]



> 📘 Use Names Skill to extract names from:
> 
> - [Articles](https://studio.oneai.com/?pipeline=80wq6L)
> - [Conversations](https://studio.oneai.com/?pipeline=MF6bTh)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

Identities:

- [ORG](doc:org-label) - Companies, agencies, institutions, etc.
- [PERSON](doc:person-label) - People, real or fictional characters
- [PRODUCT](doc:product-label) - Products and services

Places:

- [GEO](doc:geo-label) - Countries and States
- [LOCATION](doc:location-label) - Cities, buildings, airports, highways, bridges
- [EVENT](doc:event-label) - Sports events, Named hurricanes, wars, etc.

Others:

- [ART](doc:art-label) - Titles of books, movies, songs, etc.
- [LANGUAGE](doc:language-label) - Language names.
- [LAW](doc:law-label) - Named documents made into laws.

## Parameters

| Name         | Type    | Description                                | Default |
| :----------- | :------ | :----------------------------------------- | :------ |
| `enrichment` | boolean | Whether to enrich each label with metadata | `true`  |

## Example

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "My name is Shawn, I live in Chicago in the state of Illinois but I don't speak Portuguese.",
    "steps": [
      {
        "skill": "names"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");
const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "My name is Shawn, I live in Chicago in the state of Illinois but I don't speak Portuguese.";
const pipeline = new oneai.Pipeline(
	oneai.skills.names(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "My name is Shawn, I live in Chicago in the state of Illinois but I don't speak Portuguese."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Names(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "My name is Shawn, I live in Chicago in the state of Illinois but I don't speak Portuguese.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "My name is Shawn, I live in Chicago in the state of Illinois but I don't speak Portuguese.",
      "labels": [
        {
          "type": "name",
          "skill": "names",
          "name": "PERSON",
          "value": "Shawn",
          "data": {},
          "span_text": "Shawn",
          "span": [
            11,
            16
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 11,
              "end": 16
            }
          ]
        },
        {
          "type": "name",
          "skill": "names",
          "name": "LOCATION",
          "value": "Chicago",
          "data": {
            "type": "CITY"
          },
          "span_text": "Chicago",
          "span": [
            28,
            35
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 28,
              "end": 35
            }
          ]
        },
        {
          "type": "name",
          "skill": "names",
          "name": "GEO",
          "value": "Illinois",
          "data": {
            "type": "STATE",
            "country": "UNITED STATES"
          },
          "span_text": "Illinois",
          "span": [
            52,
            60
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 52,
              "end": 60
            }
          ]
        },
        {
          "type": "name",
          "skill": "names",
          "name": "LANGUAGE",
          "value": "Portuguese language",
          "data": {},
          "span_text": "Portuguese",
          "span": [
            79,
            89
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 79,
              "end": 89
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
  text: "My name is Shawn, I live in Chicago in the state of Illinois but I don't speak Portuguese.",
  names: [
    {
      type: 'name',
      skill: 'names',
      name: 'PERSON',
      value: 'Shawn',
      data: {},
      span_text: 'Shawn',
      span: [ 11, 16 ],
      output_spans: [ { section: 0, start: 11, end: 16 } ]
    },
    {
      type: 'name',
      skill: 'names',
      name: 'LOCATION',
      value: 'Chicago',
      data: { type: 'CITY' },
      span_text: 'Chicago',
      span: [ 28, 35 ],
      output_spans: [ { section: 0, start: 28, end: 35 } ]
    },
    {
      type: 'name',
      skill: 'names',
      name: 'GEO',
      value: 'Illinois',
      data: { type: 'STATE', country: 'UNITED STATES' },
      span_text: 'Illinois',
      span: [ 52, 60 ],
      output_spans: [ { section: 0, start: 52, end: 60 } ]
    },
    {
      type: 'name',
      skill: 'names',
      name: 'LANGUAGE',
      value: 'Portuguese language',
      data: {},
      span_text: 'Portuguese',
      span: [ 79, 89 ],
      output_spans: [ { section: 0, start: 79, end: 89 } ]
    }
  ]
}
```