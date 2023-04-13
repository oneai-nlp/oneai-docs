---
title: "Event Label"
slug: "event-label"
excerpt: "Sports events, Named hurricanes, wars, etc."
hidden: false
createdAt: "2022-08-24T06:58:09.099Z"
updatedAt: "2023-04-02T15:23:21.390Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I haven't had a house since the <span class=\"label_box\">EVENT</span><span class=\"label_text\"> Katerina</span> storm.\n</div>\n"
}
[/block]



### Example Input

```
I haven't had a house since the Katerina storm.
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"EVENT",
   "value":"Katerina",
   "data":{
      
   },
   "span_text":"Katerina",
   "span":[
      31,
      39
   ],
   "output_spans":[
      {
         "section":0,
         "start":31,
         "end":39
      }
   ]
}
```