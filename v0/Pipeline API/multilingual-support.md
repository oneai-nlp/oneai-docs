---
title: "Multilingual Support"
slug: "multilingual-support"
excerpt: "One AI has the capability to work and process text in many languages, automatically"
hidden: false
createdAt: "2022-12-29T15:45:49.509Z"
updatedAt: "2023-04-09T11:26:14.082Z"
---
Our APIs are capable of processing content in 97 languages, including English, Spanish, German, French, Japanese, Hebrew, Arabic, and more (see list at <https://oneai.com/languages>)

By default non-English inputs will be rejected.  
To enable multilingual inputs use the "multilingual" configuration object in your pipeline:

```
  "multilingual":
  {
    "enabled": true
	}
```



Additional Multilingual parameters:

[block:parameters]
{
  "data": {
    "h-0": "Name",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "`enabled`",
    "0-1": "boolean",
    "0-2": "Mark `true` if the input is not in English. The default is `false`.",
    "1-0": "`allowed_input_languages`",
    "1-1": "list",
    "1-2": "Limit processing to specific languages, if the input is detected as another language it will be blocked and the error \"40001 Language not supported\" will be returned. For example, `[\"es\",\"fr\"]`.",
    "2-0": "`expected_languages`",
    "2-1": "list",
    "2-2": "To improve language detection specify your expected input languages in a 2-letter ISO-639 language code format. For example,`[\"es\",\"fr\"]`.",
    "3-0": "`override_language_detection`",
    "3-1": "boolean",
    "3-2": "To disable language detection set to `true`, the system will then use the language from `expected_languages` field.  \nThis is useful in cases where the input language is known or in edge cases where language detection fails.",
    "4-0": "`translate_output_to`",
    "4-1": "string",
    "4-2": "Language to translate the output into. For example,`\"en\"`."
  },
  "cols": 3,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]

Pro-tip: To enable multilingual support with default behavior use `multilingual`:`true`.

To analyze multi-lingual audio, use the our Whisper powered transcription skill: <https://docs.oneai.com/docs/transcribe-audio>

#### Request

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "Después de prohibir de forma permanente las fiestas y eventos en todos los listados de Airbnb en junio, la compañía está endureciendo su postura contra las fiestas al lanzar nuevas herramientas de detección en los EE. UU. y Canadá.",
    "multilingual": {
        "enabled": true,
        "allowed_input_languages": ["es"],
        "expected_languages":["es"],
        "override_language_detection": true,
        "translate_output_to": "en"   
    },
    "steps": [
      {
        "skill": "article-topics"
      }
    ]
}'


```
```python
import requests

url = 'https://api.oneai.com/api/v0/pipeline'
headers = {
    'accept': 'application/json',
    'Content-Type': 'application/json',
    'api-key': '<YOUR-API-KEY-HERE>'
}

data = {
    "input": "Después de prohibir de forma permanente las fiestas y eventos en todos los listados de Airbnb en junio, la compañía está endureciendo su postura contra las fiestas al lanzar nuevas herramientas de detección en los EE. UU. y Canadá.",
    "steps": [
        {
            "skill": "article-topics"
        },
        {
            "multilingual": {
                "enabled": True,
                "allowed_input_languages": ["es"],
                "expected_languages": ["es"],
                "override_language_detection": True,
                "translate_output_to": "en"
            }
        }
    ]
}

response = requests.post(url, headers=headers, json=data)
print(response.json())

```