---
title: "Person Label"
slug: "person-label"
excerpt: "People, including fictional characters."
hidden: false
createdAt: "2022-08-24T06:41:46.040Z"
updatedAt: "2023-04-02T15:23:53.975Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  Hey <span class=\"label_box\">PERSON</span><span class=\"label_text\"> Francis</span>, my name is <span class=\"label_box\">PERSON</span><span class=\"label_text\"> Garrett</span>, happy to meet you\n</div>"
}
[/block]



### Example Input

```
Hey Francis, my name is Garrett, happy to meet you
```



### Example Output

```json JSON
[
   {
      "type":"name",
      "skill":"names",
      "name":"PERSON",
      "value":"Francis",
      "data":{
         
      },
      "span_text":"Francis",
      "span":[
         4,
         11
      ],
      "output_spans":[
         {
            "section":0,
            "start":4,
            "end":11
         }
      ]
   },
   {
      "type":"name",
      "skill":"names",
      "name":"PERSON",
      "value":"Garrett",
      "data":{
         
      },
      "span_text":"Garrett",
      "span":[
         24,
         31
      ],
      "output_spans":[
         {
            "section":0,
            "start":24,
            "end":31
         }
      ]
   }
]
```