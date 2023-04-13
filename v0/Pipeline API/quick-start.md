---
title: "Quick Start"
slug: "quick-start"
excerpt: "We will have you running your first One AI query in less than a minute."
hidden: false
createdAt: "2022-08-15T12:43:58.022Z"
updatedAt: "2022-12-28T13:27:49.772Z"
---
## Grab an API key

Grab your API key from [your One AI account](https://studio.oneai.com/settings/api-keys). If you haven't yet, sign up to generate an API Key.

## Prepare your first One AI Pipeline API call

Let's summarize a paragraph using One AI's Pipeline API:

1. Copy this code (select between `curl`, `Node.js` or `Python`).

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
    "steps": [
      {
        "skill": "summarize"
      }   
    ]
}'
```
```javascript Node.js
// npm install oneai
const OneAI = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%";
const pipeline = new oneai.Pipeline(
	oneai.skills.summarize(),
);

pipeline.run(text).then(console.log);
```
```python
# pip install oneai
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Summarize(),
  ]
)

output = pipeline.run(text)
print(output)
```



2. Paste your API Key instead of the `<YOUR-API-KEY-HERE>` placeholder.
3. `pip3 install oneai` or `npm install oneai` if you selected to use the `Python` or `Node.js` examples respectively.

## Run the sample

You should be getting an output similar to

```json JSON Response
{
  "input_text": "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "summarize",
      "text_generated_by_step_id": 1,
      "text": "60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020. A third said that spending climbed by more than 30%.",
      "labels": [
        {
          "type": "origin",
          "skill": "origin",
          "span_text": "60",
          "span": [
            0,
            2
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 0,
              "end": 2
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 218,
              "end": 220
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " tech",
          "span": [
            6,
            11
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 6,
              "end": 11
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 225,
              "end": 229
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " tech",
          "span": [
            6,
            11
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 6,
              "end": 11
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 230,
              "end": 237
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " leaders",
          "span": [
            11,
            19
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 11,
              "end": 19
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 230,
              "end": 237
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " indicated",
          "span": [
            19,
            29
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 19,
              "end": 29
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 238,
              "end": 247
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " their",
          "span": [
            34,
            40
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 34,
              "end": 40
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 263,
              "end": 270
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " N",
          "span": [
            40,
            42
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 40,
              "end": 42
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 259,
              "end": 260
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": "LP",
          "span": [
            42,
            44
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 42,
              "end": 44
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 260,
              "end": 262
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": "LP",
          "span": [
            42,
            44
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 42,
              "end": 44
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 263,
              "end": 270
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " budgets",
          "span": [
            44,
            52
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 44,
              "end": 52
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 263,
              "end": 270
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " budgets",
          "span": [
            44,
            52
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 44,
              "end": 52
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 271,
              "end": 275
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " grew",
          "span": [
            52,
            57
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 52,
              "end": 57
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 271,
              "end": 275
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " by",
          "span": [
            57,
            60
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 57,
              "end": 60
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 288,
              "end": 290
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " at",
          "span": [
            60,
            63
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 60,
              "end": 63
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 282,
              "end": 287
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " least",
          "span": [
            63,
            69
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 63,
              "end": 69
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 282,
              "end": 287
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " least",
          "span": [
            63,
            69
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 63,
              "end": 69
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 288,
              "end": 290
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " 10",
          "span": [
            69,
            72
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 69,
              "end": 72
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 288,
              "end": 290
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": "%",
          "span": [
            72,
            73
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 72,
              "end": 73
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 292,
              "end": 300
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " compared",
          "span": [
            73,
            82
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 73,
              "end": 82
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 292,
              "end": 300
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " to",
          "span": [
            82,
            85
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 82,
              "end": 85
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 292,
              "end": 300
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " to",
          "span": [
            82,
            85
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 82,
              "end": 85
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 304,
              "end": 308
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " 2020",
          "span": [
            85,
            90
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 85,
              "end": 90
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 304,
              "end": 308
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": ".",
          "span": [
            90,
            91
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 90,
              "end": 91
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 318,
              "end": 323
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " A",
          "span": [
            91,
            93
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 91,
              "end": 93
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 318,
              "end": 323
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " third",
          "span": [
            93,
            99
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 93,
              "end": 99
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 318,
              "end": 323
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " said",
          "span": [
            99,
            104
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 99,
              "end": 104
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 324,
              "end": 328
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " spending",
          "span": [
            109,
            118
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 109,
              "end": 118
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 334,
              "end": 342
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " spending",
          "span": [
            109,
            118
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 109,
              "end": 118
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 343,
              "end": 350
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " climbed",
          "span": [
            118,
            126
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 118,
              "end": 126
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 343,
              "end": 350
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " by",
          "span": [
            126,
            129
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 126,
              "end": 129
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 364,
              "end": 366
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " than",
          "span": [
            134,
            139
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 134,
              "end": 139
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 364,
              "end": 366
            }
          ]
        },
        {
          "type": "origin",
          "skill": "origin",
          "span_text": " 30",
          "span": [
            139,
            142
          ],
          "output_spans": [
            {
              "section": 0,
              "start": 139,
              "end": 142
            }
          ],
          "input_spans": [
            {
              "section": 0,
              "start": 364,
              "end": 366
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
```json SDK Response
{
  text: 'Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%',
  summary: {
    text: '60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020. A third said that spending climbed by more than 30%.',
    origins: []
  }
}
```



## Congratulations!

You have run your first One AI Pipeline query. Too many more to come!