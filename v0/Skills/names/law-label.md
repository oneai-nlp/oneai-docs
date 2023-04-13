---
title: "Law Label"
slug: "law-label"
excerpt: "Named documents made into laws."
hidden: false
createdAt: "2022-08-24T07:02:55.580Z"
updatedAt: "2023-04-02T15:23:38.249Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  According to the <span class=\"label_box\">LAW</span><span class=\"label_text\"> fifth amendment</span> you shouldn't do this.\n</div>\n"
}
[/block]



### Example Input

```
According to the fifth amendment you shouldn't do this.
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"LAW",
   "value":"Fifth Amendment to the United States Constitution",
   "data":{
      
   },
   "span_text":"the fifth amendment",
   "span":[
      13,
      32
   ],
   "output_spans":[
      {
         "section":0,
         "start":13,
         "end":32
      }
   ]
}
```