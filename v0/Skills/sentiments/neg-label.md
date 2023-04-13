---
title: "NEG Label"
slug: "neg-label"
excerpt: "Negative sentiment"
hidden: false
createdAt: "2022-08-24T09:09:11.925Z"
updatedAt: "2023-04-02T15:27:45.196Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  <span class=\"label_box\">NEGATIVE</span><span class=\"label_text\"> I am very pissed off about all of this</span>\n</div>\n"
}
[/block]



### Example Input

```
I am very pissed off about all of this
```



### Example Output

```json
{
   "type":"sentiment",
   "skill":"sentiments",
   "value":"NEG",
   "span_text":"I am very pissed off about all of this",
   "span":[
      0,
      38
   ],
   "output_spans":[
      {
         "section":0,
         "start":0,
         "end":38
      }
   ]
}
```