---
title: "Outro Label"
slug: "outro-label"
hidden: false
createdAt: "2022-11-13T14:11:45.689Z"
updatedAt: "2023-04-02T15:21:44.611Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n <span class=\"label_box\">OUTRO</span><span class=\"label_text\"> Hope to hear from you soon,</p>\n</div>\n"
}
[/block]



### Example Input

```
Hope to hear from you soon
```



### Example Output

```json
{
  "type": "service-email-insights",
  "skill": "service-email-insights",
  "name": "Outro",
  "value": "hope to hear from you soon",
  "span_text": "hope to hear from you soon",
  "span": [
    0,
    26
  ],
  "output_spans": [
    {
      "section": 0,
      "start": 0,
      "end": 26
    }
  ]
}
```