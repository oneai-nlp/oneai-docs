---
title: "Ordinal Label"
slug: "ordinal-label"
excerpt: "Position in a list - “first”, “second”, etc."
hidden: false
createdAt: "2022-08-24T07:46:33.023Z"
updatedAt: "2023-04-02T15:26:06.416Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  You'll be <span class=\"label_box\">ORDINAL</span><span class=\"label_text\"> first</span> to jump and you'll be <span class=\"label_box\">ORDINAL</span><span class=\"label_text\"> second.</span>\n</div>\n"
}
[/block]



### Example Input

```
You'll be first to jump and you'll be second.
```



### Example Output

```json
[
   {
      "type":"number",
      "skill":"numbers",
      "name":"ORDINAL",
      "value":"1",
      "data":{
         "numeric_value":1
      },
      "span_text":"first",
      "span":[
         10,
         15
      ],
      "output_spans":[
         {
            "section":0,
            "start":10,
            "end":15
         }
      ]
   },
   {
      "type":"number",
      "skill":"numbers",
      "name":"ORDINAL",
      "value":"2",
      "data":{
         "numeric_value":2
      },
      "span_text":"second",
      "span":[
         38,
         44
      ],
      "output_spans":[
         {
            "section":0,
            "start":38,
            "end":44
         }
      ]
   }
]
```



### Additional Data

| Name            | Description                     | Example |
| :-------------- | :------------------------------ | :------ |
| `numeric_value` | The numeric value of the number | 1000    |