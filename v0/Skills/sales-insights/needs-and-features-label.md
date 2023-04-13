---
title: "Needs & Features Label"
slug: "needs-and-features-label"
hidden: false
createdAt: "2022-08-24T09:22:54.300Z"
updatedAt: "2023-04-02T15:27:13.078Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  customer:<br/>\n\tYeah, anything. <span class=\"label_box\">NEEDS & FEATURES</span><span class=\"label_text\"> Anything that would prevent her from making costly mistakes would be highly appreciated.</span>\n</div>\n"
}
[/block]



### Example Input

```
customer:
Yeah, anything. Anything that would prevent her from making costly mistakes would be highly appreciated.
```



### Example Output

```json
{
   "type":"sales-insights",
   "skill":"sales-insights",
   "name":"Needs & Features",
   "value":"Anything that would prevent her from making costly mistakes would be highly appreciated.",
   "speaker":"customer",
   "span_text":"Anything that would prevent her from making costly mistakes would be highly appreciated.",
   "span":[
      4576,
      4663
   ],
   "output_spans":[
      {
         "section":17,
         "start":16,
         "end":103
      }
   ]
}
```