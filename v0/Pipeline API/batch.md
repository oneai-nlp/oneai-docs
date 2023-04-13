---
title: "Articles vs. Conversations"
slug: "batch"
hidden: false
createdAt: "2022-08-18T12:54:33.038Z"
updatedAt: "2023-01-05T09:13:20.625Z"
---
## Articles and Conversations

The API handles articles and conversations differently. In fact, from the AI perspective articles and conversations are so distinguished, that it employs completely different models to handle each of them. For this reason, the Pipeline API needs to identify the input type.

### Passing `input_type`

In any case when you know the type of input you are processing, please make sure to pass it in the payload for the pipeline request. 

#### Native

If you work with a native library, set the `input_type` field of the payload to either `article` or `conversation`.

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": [{ "speaker": "Josh", "utterance": "Do you like math?", "timestamp": "0:00" }, { "speaker": "Mellisa", "utterance": "I like it but I'\''m not so good at it", "timestamp": "0:00" }, { "speaker": "Josh", "utterance": "...", "timestamp": "..." }],
    "input_type": "conversation",
    "steps": [
      {
        "skill": "summarize"
      }   
    ]
}'
```



#### SDK

When working with the SDK, the default `input_type` is `article`, unless you pass a `Conversation` object to the pipeline, which then sets the  `input_type` to `conversation` behind the scenes.

```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const conversation = new oneai.Conversation(
  [
    { "speaker": "Josh", "utterance": "Do you like math?", "timestamp": "0:00" },
    { "speaker": "Mellisa", "utterance": "I like it but I'm not so good at it", "timestamp": "0:02" },
	]
);

const pipeline = new oneai.Pipeline(
	oneai.skills.splitByTopic(),
);

pipeline.run(conversation).then(console.log);
```
```python Python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.SplitByTopic(),
  ]
)

conversation = oneai.Conversation(
  [
    oneai.Utterance(speaker="Josh", utterance="Do you like math?"), 
    oneai.Utterance(speaker="Mellisa", utterance="I like it but I'm not so good at it"),  
  ]
)

output = pipeline.run(conversation)
```



## Conversation Format

The API accepts conversations in the following format:

```json
[
	{ 
    "speaker": "Josh", 
    "utterance": "Do you like math?", 
    "timestamp": "0:00" 
  },
  { 
    "speaker": "Mellisa", 
    "utterance": "I like it but I'm not so good at it", 
    "timestamp": "0:02" 
  },
]
```



As you can see, a conversation is an array of utterances, each containing`speaker`, `timestamp` and the `utterance` itself (i.e. what was actually said by the speaker at the timestamp.

## Conversation Parsing

To help you format the conversation correctly, our SDKs contain a utility to help just with that

```javascript
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const text = `
Josh 00:00
Do you like math?

Mellisa 00:02
I like it but I'm not so good at it.
`;

const conversation = oneai.Conversation.parse(text)
```
```python
import oneai

text = """
Josh 00:00
Do you like math?

Mellisa 00:02
I like it but I'm not so good at it.
"""

oneai.api_key = "<YOUR-API-KEY-HERE>"

conversation = oneai.Conversation.parse(text)
```