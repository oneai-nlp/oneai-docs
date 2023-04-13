---
title: "Location Label"
slug: "location-label"
excerpt: "Cities, buildings, airports, highways, bridges"
hidden: false
createdAt: "2022-08-24T06:53:05.489Z"
updatedAt: "2023-04-02T15:23:42.888Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  Let's meet in <span class=\"label_box\">LOCATION</span><span class=\"label_text\"> Seattle.</span>\n</div>"
}
[/block]



### Example Input

```
Let's meet in Seattle.
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"LOCATION",
   "value":"Seattle",
   "data":{
      "type":"CITY"
   },
   "span_text":"Seattle",
   "span":[
      14,
      21
   ],
   "output_spans":[
      {
         "section":0,
         "start":14,
         "end":21
      }
   ]
}
```