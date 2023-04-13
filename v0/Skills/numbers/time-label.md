---
title: "Time Label"
slug: "time-label"
excerpt: "Times smaller than a day"
hidden: false
createdAt: "2022-08-24T07:31:39.619Z"
updatedAt: "2023-04-02T15:25:51.203Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I'll meet you in the coffee shop at <span class=\"label_box\">TIME\n  <div class=\"tooltip\">12:00<br>{<br> \n    &nbsp;&nbsp;&nbsp;\"date_time\": \"2012-08-17T12:00\",<br> \n    &nbsp;&nbsp;&nbsp;\"timezone\": \"US/Eastern\",<br>\n    &nbsp;&nbsp;&nbsp;\"precision\": \"TIME\"<br> \n    }</div>\n  </span><span class=\"label_text\"> noon</span>\n  <br>&nbsp;\n  <br>&nbsp;\n  <br>&nbsp;\n  <br>&nbsp;\n</div>\n"
}
[/block]



### Example Input

```
I'll meet you in the coffee shop at noon.
```



### Example Output

```json
{
   "type":"number",
   "skill":"numbers",
   "name":"TIME",
   "value":"12:00",
   "data":{
      "date_time":"2022-08-24T12:00",
      "timezone":null
   },
   "span_text":"noon",
   "span":[
      36,
      40
   ],
   "output_spans":[
      {
         "section":0,
         "start":36,
         "end":40
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