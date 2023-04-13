---
title: "Clustering"
slug: "clustering-skill"
excerpt: "Automatically organizes various skill labels in clusters for later analytics"
hidden: false
createdAt: "2022-08-23T12:53:28.218Z"
updatedAt: "2022-12-25T13:32:34.483Z"
---
## What is text clustering?

Please read the [Analytics API Quick Start](doc:analytics-api) guide to understand what you can do with clustering. 

## Parameters

| Name            | Type   | Description                                                                                                         | Required? |
| :-------------- | :----- | :------------------------------------------------------------------------------------------------------------------ | :-------- |
| `input_skill`   | string | A name of the skill whose labels should act as inputs for the clustering                                            | Yes       |
| `collection`    | string | The collection in which to store the clusters. If the name provided doesn't exist, a new collection will be created | Yes       |
| `user_metadata` | string | Any metadata you wish to add                                                                                        | No        |

## Example

In this example, we take [Yesterday by the Beatles ](https://en.wikipedia.org/wiki/Yesterday_(Beatles_song)) lyrics as input, extract emotions, and cluster them. Let's say we run the same process on all Beatles songs, we can eventually see a single view that shows the distribution of emotions across their music using the [Analytics UI Component](doc:ui-component).

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "Yesterday all my troubles seemed so far away.\nNow it looks as though they'\''re here to stay.\nOh, I believe in yesterday.\n\nSuddenly, I'\''m not half the man I used to be.\nThere'\''s a shadow hanging over me.\nOh, yesterday came suddenly.\n\nWhy she had to go?\nI don'\''t know, she wouldn'\''t say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.\n\nWhy she had to go?\nI don'\''t know, she wouldn'\''t say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.",
    "input_type": "article",
    "steps": [
      {
        "skill": "emotions"
      },
      {
        "skill": "clustering",
        "params": {
          "input_skill": "emotions",
          "collection": "user emotions"
        }
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const text = "Yesterday all my troubles seemed so far away.\nNow it looks as though they're here to stay.\nOh, I believe in yesterday.\n\nSuddenly, I'm not half the man I used to be.\nThere's a shadow hanging over me.\nOh, yesterday came suddenly.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.";

const pipeline = new oneai.Pipeline(
	oneai.skills.emotions(),
	oneai.skills.clustering({
  	input_skill: "emotions",
  	collection: "user emotions",
	}),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"

text = "Yesterday all my troubles seemed so far away.\nNow it looks as though they're here to stay.\nOh, I believe in yesterday.\n\nSuddenly, I'm not half the man I used to be.\nThere's a shadow hanging over me.\nOh, yesterday came suddenly.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday."

pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Emotions(),
		oneai.skills.Clustering(
  		input_skill="emotions",
  		collection="Beatles emotions",
		),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "Yesterday all my troubles seemed so far away.\nNow it looks as though they're here to stay.\nOh, I believe in yesterday.\n\nSuddenly, I'm not half the man I used to be.\nThere's a shadow hanging over me.\nOh, yesterday came suddenly.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "Yesterday all my troubles seemed so far away.\nNow it looks as though they're here to stay.\nOh, I believe in yesterday.\n\nSuddenly, I'm not half the man I used to be.\nThere's a shadow hanging over me.\nOh, yesterday came suddenly.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.\n\nWhy she had to go?\nI don't know, she wouldn't say.\nI said something wrong.\nNow I long for yesterday.\n\nYesterday love was such an easy game to play.\nNow I need a place to hide away.\nOh, I believe in yesterday.",
      "labels": [
        {
          "type": "emotion",
          "skill": "emotions",
          "name": "sadness",
          "span_text": "Yesterday all my troubles seemed so far away.",
          "span": [
            0,
            45
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 0,
              "end": 45
            }
          ]
        },
        {
          "type": "emotion",
          "skill": "emotions",
          "name": "happiness",
          "span_text": "Yesterday love was such an easy game to play.",
          "span": [
            331,
            376
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 331,
              "end": 376
            }
          ]
        },
        {
          "type": "emotion",
          "skill": "emotions",
          "name": "happiness",
          "span_text": "Yesterday love was such an easy game to play.",
          "span": [
            541,
            586
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 541,
              "end": 586
            }
          ]
        },
        {
          "type": "status",
          "skill": "clustering",
          "data": {
            "status": "{\"status\":\"queued\",\"task_id\":\"ef86b042-3f1c-490e-942e-7b6fa5fcde3e\"}"
          }
        },
        {
          "type": "request_id",
          "skill": "clustering",
          "data": {
            "request_id": "abc80e20-79bd-4ce4-917c-bc5303977b0a"
          }
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