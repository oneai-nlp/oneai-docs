---
title: "Number Label"
slug: "number-label"
excerpt: "Numerals that do not fall under another type."
hidden: false
createdAt: "2022-08-24T07:50:30.612Z"
updatedAt: "2023-04-02T15:26:02.069Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I can count to <span class=\"label_box\">NUMBER</span><span class=\"label_text\"> six.</span>\n</div>\n"
}
[/block]



### Example Input

```
I can count to six.
```



### Example Output

```json
{
   "type":"number",
   "skill":"numbers",
   "name":"NUMBER",
   "value":"6",
   "data":{
      "numeric_value":6
   },
   "span_text":"six",
   "span":[
      15,
      18
   ],
   "output_spans":[
      {
         "section":0,
         "start":15,
         "end":18
      }
   ]
}
```



### Additional Data

| Name            | Description                     | Example |
| :-------------- | :------------------------------ | :------ |
| `numeric_value` | The numeric value of the number | 1000    |