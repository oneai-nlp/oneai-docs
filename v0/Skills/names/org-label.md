---
title: "Org Label"
slug: "org-label"
excerpt: "Companies, agencies, institutions, etc."
hidden: false
createdAt: "2022-08-24T06:47:39.407Z"
updatedAt: "2023-04-02T15:23:49.235Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I was working for <span class=\"label_box\">ORG</span><span class=\"label_text\"> Microsoft</span> for a few years.\n</div>"
}
[/block]



### Example Input

```
I was working for Microsoft for a few years.
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"ORG",
   "value":"Microsoft",
   "data":{
      
   },
   "span_text":"Microsoft",
   "span":[
      18,
      27
   ],
   "output_spans":[
      {
         "section":0,
         "start":18,
         "end":27
      }
   ]
}
```