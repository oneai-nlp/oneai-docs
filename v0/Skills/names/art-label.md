---
title: "Art Label"
slug: "art-label"
excerpt: "Titles of books, movies, songs, etc."
hidden: false
createdAt: "2022-08-24T07:00:09.262Z"
updatedAt: "2023-04-02T15:23:16.547Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I just saw the <span class=\"label_box\">ART</span><span class=\"label_text\"> Mona Lisa</span> first hand!\n</div>\n"
}
[/block]



### Example Input

```
I just saw the Mona Lisa first hand!
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"ART",
   "value":"Mona Lisa",
   "data":{
      
   },
   "span_text":"the Mona Lisa",
   "span":[
      16,
      29
   ],
   "output_spans":[
      {
         "section":0,
         "start":16,
         "end":29
      }
   ]
}
```