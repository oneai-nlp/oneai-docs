---
title: "Surprise Label"
slug: "surprise-label"
hidden: false
createdAt: "2022-08-24T08:07:45.164Z"
updatedAt: "2023-04-02T15:22:24.614Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  <span class=\"label_box\">SURPRISE</span><span class=\"label_text\"> I just couldn't believe that he remembered my birthday after so many years.</span>\n</div>\n"
}
[/block]



### Example Input

```
I just couldn't believe that he remembered my birthday after so many years.
```



### Example Output

```json
{
   "type":"emotion",
   "skill":"emotions",
   "name":"surprise",
   "span_text":"I just couldn't believe that he remembered my birthday after so many years.",
   "span":[
      0,
      75
   ],
   "output_spans":[
      {
         "section":0,
         "start":0,
         "end":75
      }
   ]
}
```