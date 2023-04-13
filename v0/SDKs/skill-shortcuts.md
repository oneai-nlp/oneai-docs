---
title: "Skill Classes"
slug: "skill-shortcuts"
excerpt: "The SDK enables you to build more structured pipelines using named Skill classes"
hidden: false
createdAt: "2022-08-22T10:01:57.489Z"
updatedAt: "2022-12-28T13:45:29.744Z"
---
With native code, you configure the Pipeline query using a JSON payload that describes the Pipeline, the Skills, and each Skill configuration.

Our SDKs make it easier for you to build Pipelines using named Skills, to add more readability and simplicity to your code.

Let's compare the native style to the SDK style

### Native style

```javascript Node.js
const axios = require("axios");

const apiKey = "<YOUR-API-KEY-HERE>";
const config = { 
  method: "POST", 
  url: "https://api.oneai.com/api/v0/pipeline",
  headers: { 
    "api-key": apiKey, 
    "Content-Type": "application/json",
  },
  data: {
    input: "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
    input_type: "article",
		content_type: "application/json",
    steps: [
      {
        skill: "article-topics"
      },
	    {
        skill: "numbers"
      },
	    {
        skill: "names"
      },
	    {
        skill: "emotions"
      },
	    {
        skill: "summarize",
        "params": {
          max_length: 100
        }
      }
    ],
  },
};
axios(config)
  .then((response) => {
    console.log(JSON.stringify(response.data));
  })
  .catch((error) => {
    console.log(error);
  });
```
```python
import requests

api_key = "<YOUR-API-KEY-HERE>"
url = "https://api.oneai.com/api/v0/pipeline"
headers = {
  "api-key": api_key, 
  "content-type": "application/json"
}
payload = {
  "input": "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%",
  "input_type": "article",
	"content_type": "application/json",
  "steps": [
    {
      "skill": "article-topics"
    },
    {
      "skill": "numbers"
    },
    {
      "skill": "names"
    },
    {
      "skill": "emotions"
    },
    {
      "skill": "summarize",
      "params": {
      	max_length: 100
      }
    }
  ],
}
r = requests.post(url, json=payload, headers=headers)
data = r.json()
print(data)
```



### SDK style

```javascript Node.js
const { OneAI } = require("oneai");
const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const text = "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%";

const pipeline = new oneai.Pipeline(
	oneai.skills.topics(),
	oneai.skills.numbers(),
	oneai.skills.names(),
	oneai.skills.emotions(),
	oneai.skills.summarize({ max_length: 100 }),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Topics(),
		oneai.skills.Numbers(),
		oneai.skills.Names(),
		oneai.skills.Emotions(),
		oneai.skills.Summarize(max_length=100),
  ]
)

text = "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%"

output = pipeline.run(text)
```



### Conclusion

The SDK style is much more readable and consumable by the human eye.