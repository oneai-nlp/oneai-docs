---
title: "Sadness Label"
slug: "sadness-label"
hidden: false
createdAt: "2022-08-24T08:04:27.241Z"
updatedAt: "2023-04-02T15:22:19.680Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  <span class=\"label_box\">SADNESS</span><span class=\"label_text\"> I feel bad for hurting you.</span>\n</div>\n"
}
[/block]



### Example Input

```
I feel bad for hurting you.	
```



### Example Output

```json
{
   "type":"emotion",
   "skill":"emotions",
   "name":"sadness",
   "span_text":"I feel bad for hurting you.",
   "span":[
      0,
      27
   ],
   "output_spans":[
      {
         "section":0,
         "start":0,
         "end":27
      }
   ]
}
```