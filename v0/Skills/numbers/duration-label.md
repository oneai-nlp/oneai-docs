---
title: "Duration Label"
slug: "duration-label"
excerpt: "Periods of time"
hidden: false
createdAt: "2022-08-24T07:32:19.090Z"
updatedAt: "2023-04-02T15:25:57.239Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  it's going to take <span class=\"label_box\">DURATION\n  <div class=\"tooltip\">{<br> \n    &nbsp;&nbsp;&nbsp;\"days\": 2,<br> \n    &nbsp;&nbsp;&nbsp;\"days_in_seconds\": 172800,<br>\n    &nbsp;&nbsp;&nbsp;\"months\": 0<br> \n    &nbsp;&nbsp;&nbsp;\"years\": 0<br/>\n    }</div>\n  </span><span class=\"label_text\"> two days</span> to complete.\t\n  <br>&nbsp;<br>&nbsp;\n  <br>&nbsp;\n  <br>&nbsp;\n</div>\n"
}
[/block]



### Example Input

```
it's going to take two days to complete.	
```



### Example Output

```json
{
   "type":"number",
   "skill":"numbers",
   "name":"DURATION",
   "value":"2 Days",
   "data":{
      "days":2,
      "days_in_seconds":172800,
      "months":0,
      "years":0
   },
   "span_text":"two days",
   "span":[
      19,
      27
   ],
   "output_spans":[
      {
         "section":0,
         "start":19,
         "end":27
      }
   ]
}
```



### Additional Data

| Name              | Description                                                        | Example |
| :---------------- | :----------------------------------------------------------------- | :------ |
| `days`            | Days component of the duration, expressed in fractional days value | 2.5     |
| `days_in_seconds` | Duration expressed in whole seconds (e.g 3600 = 1 hour)            | 216000  |
| `months`          | Months component of the duration                                   | 1       |
| `years`           | Years component of the duration                                    | 0       |