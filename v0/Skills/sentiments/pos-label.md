---
title: "POS Label"
slug: "pos-label"
excerpt: "Positive sentiment"
hidden: false
createdAt: "2022-08-24T09:06:47.816Z"
updatedAt: "2023-04-02T15:27:30.907Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  <span class=\"label_box\">POSITIVE</span><span class=\"label_text\"> This is truly an amazing achievement.</span>\n</div>\n"
}
[/block]



### Example Input

```
This is truly an amazing achievement.
```



### Example Output

```json
{
   "type":"sentiment",
   "skill":"sentiments",
   "value":"POS",
   "span_text":"This is truly an amazing achievement.",
   "span":[
      0,
      37
   ],
   "output_spans":[
      {
         "section":0,
         "start":0,
         "end":37
      }
   ]
}
```