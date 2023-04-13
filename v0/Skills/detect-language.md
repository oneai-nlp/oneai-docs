---
title: "Detect Language"
slug: "detect-language"
excerpt: "Detects the input text's language."
hidden: false
createdAt: "2022-08-18T07:06:02.790Z"
updatedAt: "2023-04-02T15:21:16.549Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  <div>\n  <svg width=\"1em\" height=\"1em\" viewBox=\"0 0 22 23\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\"><g clip-path=\"url(#clip0_125_1787)\"><path d=\"M11.0002 20.6668C16.0628 20.6668 20.1668 16.5628 20.1668 11.5002C20.1668 6.43755 16.0628 2.3335 11.0002 2.3335C5.93755 2.3335 1.8335 6.43755 1.8335 11.5002C1.8335 16.5628 5.93755 20.6668 11.0002 20.6668Z\" stroke=\"#4D4DFE\" stroke-width=\"3\" stroke-linecap=\"round\" stroke-linejoin=\"round\"></path><path d=\"M1.8335 11.5H20.1668\" stroke=\"#4D4DFE\" stroke-width=\"3\" stroke-linecap=\"round\" stroke-linejoin=\"round\"></path><path d=\"M11.0002 2.3335C13.293 4.84365 14.596 8.10119 14.6668 11.5002C14.596 14.8991 13.293 18.1567 11.0002 20.6668C8.70732 18.1567 7.40431 14.8991 7.3335 11.5002C7.40431 8.10119 8.70732 4.84365 11.0002 2.3335V2.3335Z\" stroke=\"#4D4DFE\" stroke-width=\"3\" stroke-linecap=\"round\" stroke-linejoin=\"round\"></path></g><defs><clipPath id=\"clip0_125_1787\"><rect width=\"22\" height=\"22\" fill=\"white\" transform=\"translate(0 0.5)\"></rect></clipPath></defs></svg>\n    <span>French</span>\n  </div>\nArrivé sur le central avec seulement quelques jours d'entraînement à haute intensité dans les jambes et peu de certitudes sur sa capacité à servir à 100 % sur la durée d'un match, lui qui avait redoublé de prudence ces derniers jours pour protéger sa ceinture abdominale, Nadal a plutôt rassuré sur son entame de match.</div>\n"
}
[/block]



> 📘 Use Detect Language Skill to detect language of:
> 
> - [Articles](https://studio.oneai.com/?pipeline=E8RYS9)
> - [Conversations](https://studio.oneai.com/?pipeline=kiaT0q)

> 👍 Benchmarks
> 
> Coming soon...

## Output labels

| Type            | Value                                       |
| :-------------- | :------------------------------------------ |
| detect-language | The long-form name of the detected language |

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
    "input": "Arrivé sur le central avec seulement quelques jours d'entraînement à haute intensité dans les jambes et peu de certitudes sur sa capacité à servir à 100 % sur la durée d'un match, lui qui avait redoublé de prudence ces derniers jours pour protéger sa ceinture abdominale, Nadal a plutôt rassuré sur son entame de match.",
    "steps": [
      {
        "skill": "detect-language"
      }   
    ]
}'
```
```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = "Arrivé sur le central avec seulement quelques jours d'entraînement à haute intensité dans les jambes et peu de certitudes sur sa capacité à servir à 100 % sur la durée d'un match, lui qui avait redoublé de prudence ces derniers jours pour protéger sa ceinture abdominale, Nadal a plutôt rassuré sur son entame de match.";
const pipeline = new oneai.Pipeline(
	oneai.skills.detectLanguage(),
);

pipeline.run(text).then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
text = "Arrivé sur le central avec seulement quelques jours d'entraînement à haute intensité dans les jambes et peu de certitudes sur sa capacité à servir à 100 % sur la durée d'un match, lui qui avait redoublé de prudence ces derniers jours pour protéger sa ceinture abdominale, Nadal a plutôt rassuré sur son entame de match."
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.DetectLanguage(),
  ]
)

output = pipeline.run(text)
```



#### Response

```json API Response
{
  "input_text": "Arrivé sur le central avec seulement quelques jours d'entraînement à haute intensité dans les jambes et peu de certitudes sur sa capacité à servir à 100 % sur la durée d'un match, lui qui avait redoublé de prudence ces derniers jours pour protéger sa ceinture abdominale, Nadal a plutôt rassuré sur son entame de match.",
  "status": "success",
  "output": [
    {
      "text_generated_by_step_name": "input",
      "text_generated_by_step_id": 0,
      "text": "Arrivé sur le central avec seulement quelques jours d'entraînement à haute intensité dans les jambes et peu de certitudes sur sa capacité à servir à 100 % sur la durée d'un match, lui qui avait redoublé de prudence ces derniers jours pour protéger sa ceinture abdominale, Nadal a plutôt rassuré sur son entame de match.",
      "labels": [
        {
          "type": "detect-language",
          "skill": "detect-language",
          "name": "language",
          "value": "French"
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
  text: "Arrivé sur le central avec seulement quelques jours d'entraînement à haute intensité dans les jambes et peu de certitudes sur sa capacité à servir à 100 % sur la durée d'un match, lui qui avait redoublé de prudence ces derniers jours pour protéger sa ceinture abdominale, Nadal a plutôt rassuré sur son entame de match.",
  language: [
    {
      type: 'detect-language',
      skill: 'detect-language',
      name: 'language',
      value: 'French'
    }
  ]
}
```