---
title: "Complaint Label"
slug: "complaint-label"
hidden: false
createdAt: "2022-11-13T14:19:31.284Z"
updatedAt: "2023-04-02T15:21:59.184Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n <span class=\"label_box\">COMPLAINT</span><span class=\"label_text\"> I ordered socks size 7 however I received socks size 8.5\n</div>\n"
}
[/block]



### Example Input

```
I ordered socks size 7 however I received socks size 8.5
```



### Example Output

```json
{
  "type": "service-email-insights",
  "skill": "service-email-insights",
  "name": "Complaint",
  "value": "however I received socks size 8.5",
  "span_text": "however I received socks size 8.5",
  "span": [
    23,
    56
  ],
  "output_spans": [
    {
      "section": 0,
      "start": 23,
      "end": 56
    }
  ]
}
```