---
title: "Date Label"
slug: "date-label"
excerpt: "Absolute or relative dates or periods."
hidden: false
createdAt: "2022-08-24T07:19:04.709Z"
updatedAt: "2023-04-02T15:25:45.575Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I bought this land <span class=\"label_box\">DATE\n  <div class=\"tooltip\">{<br> \n    &nbsp;&nbsp;&nbsp;\"date_time\": \"2012-08-17T00:00\",<br> \n    &nbsp;&nbsp;&nbsp;\"timezone\": \"US/Eastern\",<br>\n    &nbsp;&nbsp;&nbsp;\"precision\": \"DAY\"<br> \n    }</div>\n  </span><span class=\"label_text\"> ten years ago</span>\n  <br>&nbsp;\n  <br>&nbsp;\n  <br>&nbsp;\n</div>\n"
}
[/block]



### Example Input

```
I bought this land ten years ago
```



### Example Output

```json
{
   "type":"number",
   "skill":"numbers",
   "name":"DATE",
   "value":"2012-08-24",
   "data":{
      "date_time":"2012-08-24T00:00",
      "timezone":null,
      "precision":"DAY"
   },
   "span_text":"ten years ago",
   "span":[
      19,
      32
   ],
   "output_spans":[
      {
         "section":0,
         "start":19,
         "end":32
      }
   ]
}
```



### Additional Data

| Name        | Description                                                         | Example          |
| :---------- | :------------------------------------------------------------------ | :--------------- |
| `value`     | Human readable output according to the precision level              | 2012-08-17 10:00 |
| `date_time` | Machine-readable full date-time string in `yyyy-mm-ddTHH:MM` format | 2012-08-17T10:00 |
| `timezone`  | The indicated timezone, `null` if not present                       | US/Pacific       |
| `precision` | The date/time precision is indicated. One of YEAR, MONTH, DAY, TIME | DAY              |