---
title: "Anger Label"
slug: "anger-label"
hidden: false
createdAt: "2022-08-24T08:06:24.739Z"
updatedAt: "2023-04-02T15:22:09.669Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  <span class=\"label_box\">ANGER</span><span class=\"label_text\"> I am very pissed off about all of this.</span>\n</div>\n"
}
[/block]



### Example Input

```
I am very pissed off about all of this.
```



### Example Output

```json
{
  "type": "emotion",
  "skill": "emotions",
  "name": "anger",
  "span_text": "I am very pissed off about all of this.",
  "span": [
    0,
    39
  ],
  "output_spans": [
    {
      "section": 0,
      "start": 0,
      "end": 39
    }
  ]
}
```