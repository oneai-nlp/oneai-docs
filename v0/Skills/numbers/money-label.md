---
title: "Money Label"
slug: "money-label"
excerpt: "Monetary values, including unit."
hidden: false
createdAt: "2022-08-24T07:40:52.279Z"
updatedAt: "2023-04-02T15:26:12.163Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  We made <span class=\"label_box\">MONEY</span><span class=\"label_text\"> a thousand bucks</span> in no time.\t\n</div>\n"
}
[/block]



### Example Input

```
We made a thousand bucks in no time.
```



### Example Output

```json
{
   "type":"number",
   "skill":"numbers",
   "name":"MONEY",
   "value":"1,000",
   "data":{
      "numeric_value":1000
   },
   "span_text":"a thousand bucks",
   "span":[
      8,
      24
   ],
   "output_spans":[
      {
         "section":0,
         "start":8,
         "end":24
      }
   ]
}
```



### Additional Data

| Name            | Description                     | Example |
| :-------------- | :------------------------------ | :------ |
| `numeric_value` | The numeric value of the number | 1000    |