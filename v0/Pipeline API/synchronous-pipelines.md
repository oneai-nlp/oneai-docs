---
title: "Synchronous Pipelines"
slug: "synchronous-pipelines"
excerpt: "The Pipeline API has two methods of invocation: synchronous, and asynchronous."
hidden: false
createdAt: "2022-08-18T12:55:01.552Z"
updatedAt: "2022-12-28T13:30:48.216Z"
---
When the content you wish to process is small, or you already have it in its textual form, you can use a sync pipeline, meaning you can submit the request to the Pipeline API and expect a synchronous response in a timely manner.

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "Whether to power translation to document summarization, enterprises are increasing their investments in natural language processing (NLP) technologies. According to a 2021 survey from John Snow Labs and Gradient Flow, 60% of tech leaders indicated that their NLP budgets grew by at least 10% compared to 2020, while a third said that spending climbed by more than 30%"
    "steps": [
      {
        "skill": "summarize"
      }   
    ]
}'
```