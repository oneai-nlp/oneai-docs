---
title: "PDF Extract Text"
slug: "pdf-extract-text"
excerpt: "PDF Extract Text is a skill that enables isolating text out of your PDF files"
hidden: false
createdAt: "2023-01-12T08:52:24.793Z"
updatedAt: "2023-02-06T17:19:10.794Z"
---
> 📘 Use PDF Extract Text Skill to extract text and wide variety of insights from your PDF

The image below illustrates extracting keywords from a scientific paper on top of the basic PDF to text extraction using One Ai Studio. 

![](https://files.readme.io/6638e8c-Screenshot_2023-02-06_at_11.38.17.png)



# Examples

## Uploading a file: async file upload or link to file

You may upload your file by providing:

1. A base-64 encoded binary using our async upload endpoint.
2. A url to your file hosted elsewhere.

Let's use the following PDF file as an example:

[block:html]
{
  "html": "<iframe src=\"https://drive.google.com/file/d/1lcn9OJS3t7nsDYOPpIwsa6PAr5F0OOva/preview\" width=\"640\" height=\"480\" allow=\"autoplay\"></iframe>"
}
[/block]

## 1. How to async file upload

#### Request

URL-encode the following payload according to the instructions given in the [File Uploads](doc:file-uploads) section.

```json
{
    "input_type": "article",
    "content_type": "text/pdf",
    "steps": [
      {
        "skill": "pdf-extract-text"
      }  
    ]
}
```

The JSON above will now look like this:

```
%7B%22input_type%22%3A%22article%22%2C%22steps%22%3A%5B%7B%22skill%22%3A%22pdf-extract-text%22%7D%5D%2C%22content_type%22%3A%22application%2Fpdf%22%7D
```

Append it to our async API URL:

```
 https://api.oneai.com/api/v0/pipeline/async/file?pipeline=
```

And use it in your API call like this:

```curl
curl -X POST \
"https://api.oneai.com/api/v0/pipeline/async/file?pipeline=%7B%22input_type%22%3A%22article%22%2C%22steps%22%3A%5B%7B%22skill%22%3A%22pdf-extract-text%22%7D%5D%2C%22content_type%22%3A%22application%2Fpdf%22%7D",\
-H 'accept: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
--upload-file '<PATH-TO-LOCAL-FILE>'
```
```javascript Node.js
// Node.js SDK currently supports only synchronous pipelines
// Asynchronous support is coming soon
const { OneAI } = require("oneai");
const oneai = new
OneAI("<YOUR-API-KEY-HERE>");
const pipeline = new oneai.Pipeline(
oneai.skills.pdf_extract_text({ speaker_detection: true, }) );
pipeline.runFile("YOUR_FILE_PATH").then(console.log);
```
```python
# Python SDK currently supports only synchronous pipelines
# Asynchronous support is coming soon
import oneai
import base64

with open("<YOUR-FILE-PATH>", "rb") as f:
  textParsed = base64.b64encode(f.read())
oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.pdf_extract_text(
  		speaker_detection=True,
		),
  ]
)

conversation = oneai.Article(
  textParsed
)

output = pipeline.run(conversation)
```

## 2. How to use URL to your file

Simply provide url to your file inside the "input" of your payload:

```json
{
  	"input": "https://drive.google.com/file/d/1lcn9OJS3t7nsDYOPpIwsa6PAr5F0OOva/view?usp=sharing",
    "input_type": "article",
    "content_type": "text/pdf",
    "steps": [
      {
        "skill": "pdf-extract-text"
      }  
    ]
}
```



# Response:

The response will come in the following format:

```json
{
  "input": [
    {
      "utterance": "\r\n\r\n\r\n\r\n\r\n\r\n\r\n\r\nOne Ai PDF Extract Text Skill Demo\r\nWelcome to One AI Studio! This is a demo of our PDF extract text skill. Text from this file can be extracted in a text format from our API .json response to be used according to your needs. You may also use our other skills (âkeywordsâ, ânumbersâ, âsentimentsâ etc.) to get useful insights from the text in your arbitrary PDF. We currently support files of up to 5MB in size. You may use our async file upload to hand over your file to us or you can simply provide a link to your file in the request body âinputâ field. Now letâs add a little table.\r\n\r\nTable 1\r\nHeader 1    Header 2    Header 3    Header 4    Header 5    Header 6\r\n\r\nData 2.1    Data 2.2    Data 2.3    Data 2.4    Data 2.5    Data 2.6\r\n\r\nData 3.1    Data 3.2    Data 3.3    Data 3.4    Data 3.5    Data 3.6\r\n"
    }
  ],
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "pdf-extract-text",
      "text_generated_by_step_id": 1,
      "contents": [
        {
          "utterance": "\r\n\r\n\r\n\r\n\r\n\r\n\r\n\r\nOne Ai PDF Extract Text Skill Demo\r\nWelcome to One AI Studio! This is a demo of our PDF extract text skill. Text from this file can be extracted in a text format from our API .json response to be used according to your needs. You may also use our other skills (âkeywordsâ, ânumbersâ, âsentimentsâ etc.) to get useful insights from the text in your arbitrary PDF. We currently support files of up to 5MB in size. You may use our async file upload to hand over your file to us or you can simply provide a link to your file in the request body âinputâ field. Now letâs add a little table.\r\n\r\nTable 1\r\nHeader 1    Header 2    Header 3    Header 4    Header 5    Header 6\r\n\r\nData 2.1    Data 2.2    Data 2.3    Data 2.4    Data 2.5    Data 2.6\r\n\r\nData 3.1    Data 3.2    Data 3.3    Data 3.4    Data 3.5    Data 3.6\r\n"
        }
      ],
      "labels": []
    }
  ],
  "stats": {
    "concurrency_wait_time": 0,
    "total_running_jobs": 1,
    "total_waiting_jobs": 0
  }
}
```

## 

Thank you for visiting our documentation. We hope this article was helpful. If you have any questions please [contact](https://www.oneai.com/contact) us 😌.