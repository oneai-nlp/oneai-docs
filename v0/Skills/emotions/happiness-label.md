---
title: "Happiness Label"
slug: "happiness-label"
hidden: false
createdAt: "2022-08-24T08:00:54.567Z"
updatedAt: "2023-04-02T15:22:14.849Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  <span class=\"label_box\">HAPPINESS</span><span class=\"label_text\"> I'm so excited and I just can't hide it.</span>\n</div>\n"
}
[/block]



### Example Input

```
I'm so excited and I just can't hide it.
```



### Example Output

```json
{
   "type":"emotion",
   "skill":"emotions",
   "name":"happiness",
   "span_text":"I'm so excited and I just can't hide it.",
   "span":[
      0,
      40
   ],
   "output_spans":[
      {
         "section":0,
         "start":0,
         "end":40
      }
   ]
}
```