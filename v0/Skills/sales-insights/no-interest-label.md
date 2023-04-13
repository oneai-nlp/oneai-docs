---
title: "No Interest Label"
slug: "no-interest-label"
hidden: false
createdAt: "2022-08-24T09:34:38.073Z"
updatedAt: "2023-04-02T15:27:22.096Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  Agent  1:13<br/>  \n Cuz I think our platform could help you guys out over at Giant Games.<br/>\n<br/>\nProspect  1:17  <br/>\n You seem to want to sell me something. So I'm going to say goodbye. <span class=\"label_box\">NO INTEREST</span><span class=\"label_text\"> Don't call again!</span>\n</div>\n"
}
[/block]



### Example Input

```
Agent  1:13  
Cuz I think our platform could help you guys out over at Giant Games.

Prospect  1:17  
You seem to want to sell me something. So I'm going to say goodbye. Don't call again!
```



### Example Output

```json
{
   "type":"sales-insights",
   "skill":"sales-insights",
   "name":"No interest",
   "value":"Don't call again!",
   "speaker":"Prospect",
   "span_text":"Don't call again!",
   "span":[
      170,
      187
   ],
   "output_spans":[
      {
         "section":1,
         "start":68,
         "end":85
      }
   ]
}
```