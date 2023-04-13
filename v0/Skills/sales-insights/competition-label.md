---
title: "Competition Label"
slug: "competition-label"
hidden: false
createdAt: "2022-08-28T09:53:54.195Z"
updatedAt: "2023-04-02T15:27:03.294Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  Agent  2:23<br/>  \nSo when you have maybe 20 to 30 minutes, next week, just for a brief discovery call, and that way, you get a better understanding of our product and you see if it could be a value to you.<br/>\n<br/>\nProspect  3:10  <br/>\nProbably not. <span class=\"label_box\">COMPETITION</span><span class=\"label_text\"> We've got quite a bit in that space in the marketing side, so we might be sat there. </span>\n"
}
[/block]



### Example Input

```
Agent  2:23  
So when you have maybe 20 to 30 minutes, next week, just for a brief discovery call, and that way, you get a better understanding of our product and you see if it could be a value to you.

Prospect  3:10  
Probably not. We've got quite a bit in that space in the marketing side, so we might be sat there. 
```



### Example Output

```json
{
   "type":"sales-insights",
   "skill":"sales-insights",
   "name":"Competition",
   "value":"We've got quite a bit in that space in the marketing side, so we might be sat there.",
   "speaker":"Prospect",
   "span_text":"We've got quite a bit in that space in the marketing side, so we might be sat there.",
   "span":[
      234,
      318
   ],
   "output_spans":[
      {
         "section":1,
         "start":14,
         "end":98
      }
   ]
}
```