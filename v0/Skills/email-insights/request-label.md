---
title: "Request Label"
slug: "request-label"
hidden: false
createdAt: "2022-11-13T14:14:00.396Z"
updatedAt: "2023-04-02T15:21:49.888Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n ACME CORP requires no commitments and no minimum spend. <span class=\"label_box\">REQUEST</span><span class=\"label_text\"> Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!\n</div>\n"
}
[/block]



### Example Input

```
ACME CORP requires no commitments and no minimum spend. Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!
```



### Example Output

```json
{
  "type": "service-email-insights",
  "skill": "service-email-insights",
  "name": "Request",
  "value": "Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!",
  "span_text": "Feel free to make a free account and explore the calibration capabilities, maybe you can launch a batch in the morning and check the results at lunchtime!",
  "span": [
    56,
    210
  ],
  "output_spans": [
    {
      "section": 0,
      "start": 56,
      "end": 210
    }
  ]
}
```