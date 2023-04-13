---
title: "Product Label"
slug: "product-label"
excerpt: "Products and services"
hidden: false
createdAt: "2022-08-24T06:57:25.079Z"
updatedAt: "2023-04-02T15:23:59.156Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I just got a ne <span class=\"label_box\">PRODUCT</span><span class=\"label_text\"> iPhone.</span>\n</div>\n"
}
[/block]



### Example Input

```
I just got a new iPhone.
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"PRODUCT",
   "value":"IPhone",
   "data":{
      
   },
   "span_text":"iPhone",
   "span":[
      18,
      24
   ],
   "output_spans":[
      {
         "section":0,
         "start":18,
         "end":24
      }
   ]
}
```