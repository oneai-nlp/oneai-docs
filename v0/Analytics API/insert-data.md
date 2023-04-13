---
title: "Insert Data into a Collection"
slug: "insert-data"
hidden: false
metadata: 
createdAt: "2023-03-29T11:31:35.990Z"
updatedAt: "2023-04-03T12:52:10.737Z"
---
Items are inserted to a collection through the `clustering` Skill in the [Pipeline API](https://docs.oneai.com/docs/clustering-skill).

There are three ways to upload data to a collection:

- Single item
- multiple inputs
- CSV file upload

Each item can contain **meta-data fields ** which will be inserted to the collection along with the text.  
This meta-data could be used later to filter the clusters and phrases, allowing deeper and fine-grained queries and analysis.

In many use-cases it is preferrable to be selective of the text inserted to the collection, and it is common to use One AI Skills to identify and select relevant texts for analysis. For example, it is common to [Split to Sentences](https://docs.oneai.com/docs/split-by-sentence) and insert each sentence for analysis separately; or from an article, it is common to insert only the [Highlights ](https://docs.oneai.com/docs/highlights)and the [Positive/Negative Sentiments](https://docs.oneai.com/docs/sentiments) into a collection for more focused and insightful analysis.

> 👍 Pro-tip: You can also use your own [Custom-Skills](https://www.oneai.com/skills/custom) to identify and select data for analysis

> 📘 Use the [Async endpoint](https://docs.oneai.com/docs/asynchronous-pipelines) for high-performance item insertion

## Quick Start - Inserting a single item

Insert a single item to your collection '<YOUR COLLECTION>':

```curl cURL
curl --location 'https://api.oneai.com/api/v0/pipeline' \
--header 'api-key: <YOUR API KEY>' \
--header 'Content-Type: application/json' \
--data '{
    "input": "This is an example input",
    "steps": [
        {
            "skill": "clustering",
            "params": {
                "collection": "<YOUR COLLECTION>"
            }
        }
    ]
}'
```
```curl JSON
{
    "input": "This is an example input",
    "steps": [
        {
            "skill": "clustering",
            "params": {
                "collection": "<YOUR COLLECTION>"
            }
        }
    ]
}
```
```python Python
import requests
import json

url = "https://api.oneai.com/api/v0/pipeline"

payload = json.dumps({
  "input": "This is an example input",
  "steps": [
    {
      "skill": "clustering",
      "params": {
        "collection": "<YOUR COLLECTION>""
      }
    }
  ]
})
headers = {
  'api-key': '<YOUR API KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
```javascript Node
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://api.oneai.com/api/v0/pipeline',
  'headers': {
    'api-key': '<YOUR API KEY>',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    "input": "This is an example input",
    "steps": [
      {
        "skill": "clustering",
        "params": {
          "collection": "<YOUR COLLECTION>""
        }
      }
    ]
  })

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



## Insert an item with Meta-data

You can assign meta-data values for your item by passing `labels` as input. Meta-data will be inserted as key-value pairs, where label `name` is the key, and the label `value` is the value.

```curl cURL
curl --location 'https://api.oneai.com/api/v0/pipeline' \
--header 'api-key: <YOUR API KEY>' \
--header 'Content-Type: application/json' \
--data '{
    "input": "This is an example input",
    "labels": [
                {
                    "name": "class",
                    "value": "example"
                },
                {
                    "name": "timestamp",
                    "value": "2023-01-02T01:02:03"
                }
              ],
    "steps": [
        {
            "skill": "clustering",
            "params": {
                "collection": "<COLLECTION NAME>"
            }
        }
    ]
}'
```
```curl JSON
{
    "input": "This is an example input",
    "labels": [
                {
                    "name": "class",
                    "value": "example"
                },
                {
                    "name": "timestamp",
                    "value": "2023-01-02T01:02:03"
                }
              ],
    "steps": [
        {
            "skill": "clustering",
            "params": {
                "collection": "<COLLECTION NAME>",
                "input_skill": "sentences"
            }
        }
    ]
}
```
```python Python
import requests
import json

url = "https://api.oneai.com/api/v0/pipeline"

payload = json.dumps({
  "input": "This is an example input",
  "labels": [
    {
      "name": "class",
      "value": "example"
    },
    {
      "name": "timestamp",
      "value": "2023-01-02T01:02:03"
    }
  ],
  "steps": [
    {
      "skill": "clustering",
      "params": {
        "collection": "<COLLECTION NAME>""
      }
    }
  ]
})
headers = {
  'api-key': '<YOUR API KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
```javascript Node
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://api.oneai.com/api/v0/pipeline',
  'headers': {
    'api-key': '<YOUR API KEY>',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    "input": "This is an example input",
    "labels": [
      {
        "name": "class",
        "value": "example"
      },
      {
        "name": "timestamp",
        "value": "2023-01-02T01:02:03"
      }
    ],
    "steps": [
      {
        "skill": "clustering",
        "params": {
          "collection": "<COLLECTION NAME>""
        }
      }
    ]
  })

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



## Insert multiple items

You can also insert a few items to the collection at the same time, using the following API:

```curl cURL
curl --location 'https://api.oneai.com/api/v0/pipeline' \
--header 'api-key: <YOUR API KEY>' \
--header 'Content-Type: application/json' \
--data '{
    "inputs":[
        {
        	"input": "This is an example input",
          "labels": [
            {
            "name": "class",
            "value": "example"
            },
            {
            "name": "timestamp",
            "value": "2023-03-02T01:02:03"
            }
          ]},
        	{
          	"input": "This is another example input 2",
            "labels": [
                {
                    "name": "class",
                    "value": "example"
                },
                {
                    "name": "timestamp",
                    "value": "2023-04-02T01:02:03"
                }
            ]}
    ],
    "steps": [
        {
            "skill": "clustering",
            "params": {
                "collection": "<COLLECTION NAME>"
            }
        }
    ]
}'
```
```json JSON
{
    "inputs":[
        {
        	"input": "This is an example input",
          "labels": [
            {
            "name": "class",
            "value": "example"
            },
            {
            "name": "timestamp",
            "value": "2023-03-02T01:02:03"
            }
          ]},
        	{
          	"input": "This is another example input 2",
            "labels": [
                {
                    "name": "class",
                    "value": "example"
                },
                {
                    "name": "timestamp",
                    "value": "2023-04-02T01:02:03"
                }
            ]}
    ],
    "steps": [
        {
            "skill": "clustering",
            "params": {
                "collection": "<COLLECTION NAME>"
            }
        }
    ]
}
```
```python
import requests
import json

url = "https://api.oneai.com/api/v0/pipeline"

payload = json.dumps({
  "inputs": [
    {
      "input": "This is an example input",
      "labels": [
        {
          "name": "class",
          "value": "example"
        },
        {
          "name": "timestamp",
          "value": "2023-03-02T01:02:03"
        }
      ]
    },
    {
      "input": "This is another example input 2",
      "labels": [
        {
          "name": "class",
          "value": "example"
        },
        {
          "name": "timestamp",
          "value": "2023-04-02T01:02:03"
        }
      ]
    }
  ],
  "steps": [
    {
      "skill": "clustering",
      "params": {
        "collection": "<COLLECTION NAME>""
      }
    }
  ]
})
headers = {
  'api-key': '<YOUR API KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
```javascript Node
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://api.oneai.com/api/v0/pipeline',
  'headers': {
    'api-key': '<YOUR API KEY>',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    "inputs": [
      {
        "input": "This is an example input",
        "labels": [
          {
            "name": "class",
            "value": "example"
          },
          {
            "name": "timestamp",
            "value": "2023-03-02T01:02:03"
          }
        ]
      },
      {
        "input": "This is another example input 2",
        "labels": [
          {
            "name": "class",
            "value": "example"
          },
          {
            "name": "timestamp",
            "value": "2023-04-02T01:02:03"
          }
        ]
      }
    ],
    "steps": [
      {
        "skill": "clustering",
        "params": {
          "collection": "<COLLECTION NAME>""
        }
      }
    ]
  })

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



## Using Skills for enriching items' meta-data & text selection

Use any One AI Skill to enrich your items with additional meta-data automatically.  
For example, you can automatically enrich your item with relevant people Names, Locations and Sentiments.

Just add additional Skills to the pipeline prior to the `clustering` Skill, and the detected meta-data will be automatically assigned to your items and will be queryable and searchable in your collection.

Common use case:

- Tag articles and mentions with relevant [People, Organization & Product Names](https://docs.oneai.com/docs/names).
- Tag tickets with relevant type of ticket using [Service Insights](https://docs.oneai.com/docs/email-insights).
- Tag reviews and survey answers with [Emotions](https://docs.oneai.com/docs/emotions) and [Sentiments](https://docs.oneai.com/docs/sentiments).

```curl JSON
{
    "inputs":[
        {
        	"input": "This is an example input",
          "labels": [
            {
            "name": "class",
            "value": "example"
            },
            {
            "name": "timestamp",
            "value": "2023-03-02T01:02:03"
            }
          ]},
        	{
          	"input": "This is another example input 2",
            "labels": [
                {
                    "name": "class",
                    "value": "example"
                },
                {
                    "name": "timestamp",
                    "value": "2023-04-02T01:02:03"
                }
            ]}
    ],
    "steps": [
        {
            "skill": "emotions"
        },
        {
            "skill": "sentiments"
        },
        {
            "skill": "service-email-insights"
        },
        {
            "skill": "clustering",
            "params": {
                "collection": "<COLLECTION NAME>"
            }
        }
    ]
}
```



## Using Skills for selecting & identifying input text spans

When you want to split long texts into smaller pieces for analysis (or querying), you can use any One AI Skill to serve as the input selector. It is possible to use Skills in both single-input and multiple-inputs modes.

Common use-cases:

- Use [Sentences](https://docs.oneai.com/docs/split-by-sentence) to analyze individual sentences from a customer review separately, each sentence can be grouped into a different cluster.
- Use [Service-Insights](https://docs.oneai.com/docs/email-insights) to only include the sentences from a ticket that have service related information (complaint, request, etc.)
- Use [Emotions](https://docs.oneai.com/docs/emotions) & [Sentiment](https://docs.oneai.com/docs/sentiments) to only include sentences with Emotion/Sentiment signals.

```curl cURL - Service Insights, Multiple Inputs
curl --location 'https://api.oneai.com/api/v0/pipeline' \
--header 'api-key: <YOUR API KEY>' \
--header 'Content-Type: application/json' \
--data '{
    "inputs": [
        {
            "input": "ticket input 1 - we will extract service insights from this text"
        },
        {
            "input": "ticket input 2 -also sentiment will be detected and applied to all input items",
            "labels": [
                {
                    "name": "timestamp",
                    "value": "2023-04-02T01:02:03"
                }
            ]
        }
],
"steps": [
    {
        "skill": "sentiments"
    },
    {
        "skill": "service-email-insights"
    },
    {
        "skill": "clustering",
        "params": {
            "collection": "<COLLECTION NAME>",
            "input_skill": "service-email-insights"
        }
    }
]
}'
```
```curl cURL - Sentences single-input
curl --location 'https://api.oneai.com/api/v0/pipeline' \
--header 'api-key: <YOUR API KEY>' \
--header 'Content-Type: application/json' \
--data '{
   "input": "This is an example input. it has multiple sentences. the last sentence has a different topic",
   "steps": [
        {
            "skill": "sentences"
        },
        {
            "skill": "clustering",
            "params": {
                "collection": "<COLLECTION NAME>",
                "input_skill":"sentences"
            }
        }
    ]
}'
```
```json
{
   "input": "This is an example input. it has multiple sentences. the last sentence has a different topic",
   "steps": [
        {
            "skill": "sentences"
        },
        {
            "skill": "clustering",
            "params": {
                "collection": "<COLLECTION NAME>",
                "input_skill":"sentences"
            }
        }
    ]
}
```
```python Python
import requests
import json

url = "https://api.oneai.com/api/v0/pipeline"

payload = json.dumps({
  "input": "This is an example input.It has multiple sentences. The last sentence has a different topic",
  "steps": [
    {
      "skill": "sentences"
    },
    {
      "skill": "clustering",
      "params": {
        "collection": "<COLLECTION NAME>",
        "input_skill": "sentences"
      }
    }
  ]
})
headers = {
  'api-key': '<YOUR API KEY>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
```javascript Node
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://api.oneai.com/api/v0/pipeline',
  'headers': {
    'api-key': '<YOUR API KEY>',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    "input": "This is an example input. it has multiple sentences. the last sentence has a different topic",
    "steps": [
      {
        "skill": "sentences"
      },
      {
        "skill": "clustering",
        "params": {
          "collection": "<COLLECTION NAME>",
          "input_skill": "sentences"
        }
      }
    ]
  })

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});

```



## CSV Upload

You can upload a csv file using a python script or via our Analytics UI. See more details about each one of the methods below.

## CSV Upload through Python script

To upload a csv file to a collection, use the following Python script. It reads a csv which includes the data along with all relevant meta data, and insert its content one row at a time through the API pipeline.

```curl Python
import requests
import json
import urllib.parse

with open(<File Path>, "rb") as f:
  csv_file = f.read()
  payload = {
  "input_type": "article",
  "content_type": "text/csv",
  "multilingual": {
    "enabled": True,
},
  "csv_params": {
    "columns": [
      "label",
      False,
      False,
      "INPUT",
      "timestamp",
    ],
    "skip_rows": 1,
    "max_rows": None,
  },
  "steps": [
    {
      "skill": "clustering",
      "params": {
        "collection": <COLLECTION NAME>,
      }
    }
  ]
}

payload_json = json.dumps(payload)

url = f'https://api.oneai.com/api/v0/pipeline/async/file?pipeline='+urllib.parse.quote(payload_json)

headers = {
    'api-key': <YOUR API KEY>,
    } 

r = requests.post(url, csv_file, headers=headers)
```



## CSV Upload through One AI Analytics UI

In order to upload a file through the Analytics UI, Enter the [upload page](https://oneai-nlp.github.io/oneai-analytics/?path=/story/one-ai-analytics-upload--one-ai-analytics-upload-example). 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/88641a6-image.png",
        null,
        ""
      ],
      "align": "center",
      "border": true
    }
  ]
}
[/block]



After picking the file at the upper part of the page, you should define each column using the dropdowns at the top:

- Text
- Translation
- Time and Date
- Custom value (according to your preferences. This is how to insert user metadata)
- Ignore (not to be uploaded into the collection).

Then, several mandatory parameters should be defined in the lower part of the page:

- API key (provided in the Studio)
- Collection (it could be the name of an existing collection or a means of creating a new one)
- Steps (insert “sentences” in this case. More Skills could be added, separated by a comma)
- Input skill (insert “sentences” in this case)

After inserting all parameters, click “Upload X items”  in the upper part of the page. You will get a confirmation message, “Upload complete,” indicating it loaded successfully.