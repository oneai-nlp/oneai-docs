---
title: "GEO Label"
slug: "geo-label"
excerpt: "Countries and States"
hidden: false
createdAt: "2022-08-24T06:54:43.327Z"
updatedAt: "2023-04-02T15:23:27.685Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  I grew up in <span class=\"label_box\">GEO</span><span class=\"label_text\"> Wyoming.</span>\n</div>\n"
}
[/block]



### Example Input

```
I grew up in Wyoming.
```



### Example Output

```json
{
   "type":"name",
   "skill":"names",
   "name":"GEO",
   "value":"Wyoming",
   "data":{
      "type":"STATE",
      "country":"UNITED STATES"
   },
   "span_text":"Wyoming",
   "span":[
      13,
      20
   ],
   "output_spans":[
      {
         "section":0,
         "start":13,
         "end":20
      }
   ]
}
```



### Additional data

A GEO label can represent a state or a country. If the label represents a state, then the `data` field will be populated also with the country. For example, if the input is 

```
I live in NSW
```



the response will contain:

```json
{
   "type":"name",
   "skill":"names",
   "name":"GEO",
   "value":"New South Wales",
   "data":{
      "type":"STATE",
      "country":"AUSTRALIA"
   },
   "span_text":"NSW",
}
```



Notice also how the `value` of the label became the full unabbreviated name of the state.