---
title: "Conversation Parsing"
slug: "conversation-parsing"
excerpt: "The SDKs contain nifty tools to help you with converting a blob of unstructured text into a conversation format"
hidden: false
createdAt: "2022-08-22T07:46:19.854Z"
updatedAt: "2022-12-28T13:43:56.081Z"
---
Let's say you have the input conversation unstructured in a text file that looks like:

```
Josh 00:00
Do you like math?

Mellisa 00:02
I like it but I'm not so good at it.
```



Let's also say that you want to parse this text into One AI conversation format so you can analyze it.  
Here is what you do:

```javascript Node.js
const { neAI } = require("oneai");
const fs = require("fs");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");

const text = fs.readFileSync("<YOUR-FILE-PATH>", {encoding: "ascii"});
const conversation = oneai.parsing.parseConversation(text)

console.log(conversation)
```
```python
# pip install oneai
import oneai
import base64

oneai.api_key = "<YOUR-API-KEY-HERE>"

with open("<YOUR-FILE-PATH>", "r") as f:
  text = f.read()

pipeline = oneai.Pipeline(
  steps = [
    oneai.skills.Summarize()
  ]
)

conversation = oneai.Conversation.parse(text)

print(conversation)
```



which results in

```json
Conversation {
  type: 'conversation',
  contentType: 'application/json',
  text: [
    {
      speaker: 'Josh',
      utterance: 'Do you like math?',
      speaker_line: 0,
      text_line: 1,
      speaker_length: 10
    },
    {
      speaker: 'Mellisa',
      utterance: "I like it but I'm not so good at it.",
      speaker_line: 3,
      text_line: 4,
      speaker_length: 13
    }
  ]
}
```