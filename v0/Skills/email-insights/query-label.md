---
title: "Query Label"
slug: "query-label"
hidden: false
createdAt: "2022-11-13T14:15:55.824Z"
updatedAt: "2023-04-02T15:21:54.533Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n <span class=\"label_box\">QUERY</span><span class=\"label_text\"> Interested in a walk-through from one of our NLP experts?\n</div>\n"
}
[/block]



### Example Input

```
Interested in a walk-through from one of our NLP experts?
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