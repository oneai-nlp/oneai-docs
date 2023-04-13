---
title: "Quantity Label"
slug: "quantity-label"
excerpt: "Measurements, such as weight or distance."
hidden: false
createdAt: "2022-08-24T07:44:32.380Z"
updatedAt: "2023-04-02T15:26:31.094Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  It's quite hard to run a <span class=\"label_box\">QUANTITY</span><span class=\"label_text\"> ten kilometer</span> run when you have extra <span class=\"label_box\">QUANTITY</span><span class=\"label_text\"> ten kilograms</span> on you.\n</div>\n"
}
[/block]



### Example Input

```
It's quite hard to run a ten kilometer run when you have extra ten kilograms on you.
```



### Example Output

```json
[
   {
      "type":"number",
      "skill":"numbers",
      "name":"QUANTITY",
      "value":"10",
      "data":{
         "numeric_value":10
      },
      "span_text":"ten kilometer",
      "span":[
         25,
         38
      ],
      "output_spans":[
         {
            "section":0,
            "start":25,
            "end":38
         }
      ]
   },
   {
      "type":"number",
      "skill":"numbers",
      "name":"QUANTITY",
      "value":"10",
      "data":{
         "numeric_value":10
      },
      "span_text":"ten kilograms",
      "span":[
         63,
         76
      ],
      "output_spans":[
         {
            "section":0,
            "start":63,
            "end":76
         }
      ]
   }
]
```



### Additional Data

| Name            | Description                     | Example |
| :-------------- | :------------------------------ | :------ |
| `numeric_value` | The numeric value of the number | 1000    |