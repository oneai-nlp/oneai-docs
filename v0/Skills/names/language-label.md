---
title: "Language Label"
slug: "language-label"
excerpt: "A name of a language."
hidden: false
createdAt: "2022-08-24T07:04:31.676Z"
updatedAt: "2023-04-02T15:23:32.703Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I'm sorry but I don't speak <span class=\"label_box\">LANGUAGE</span><span class=\"label_text\"> Portuguese.</span>\n</div>\n\n"
}
[/block]



### Example Input

```
I'm sorry but I don't speak Portuguese.
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"LANGUAGE",
   "value":"Portuguese language",
   "data":{
      
   },
   "span_text":"Portuguese",
   "span":[
      29,
      39
   ],
   "output_spans":[
      {
         "section":0,
         "start":29,
         "end":39
      }
   ]
}
```