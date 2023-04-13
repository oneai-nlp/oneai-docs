---
title: "Intro Label"
slug: "intro-label"
hidden: false
createdAt: "2022-11-13T14:02:05.754Z"
updatedAt: "2023-04-02T15:21:37.843Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n <span class=\"label_box\">INTRO</span><span class=\"label_text\"> Hi George,</p>\n</div>\n"
}
[/block]



### Example Input

```
Hi George,
```



### Example Output

```json
{
  "type": "service-email-insights",
  "skill": "service-email-insights",
  "name": "Intro",
  "value": "Hi George,",
  "span_text": "Hi George,",
  "span": [
    0,
    10
  ],
  "output_spans": [
    {
      "section": 0,
      "start": 0,
      "end": 10
    }
  ]
}
```