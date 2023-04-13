---
title: "Timing & Process Label"
slug: "timing-process-label"
hidden: false
createdAt: "2022-08-24T09:31:26.123Z"
updatedAt: "2023-04-02T15:27:17.243Z"
---
[block:html]
{
  "html": "<div class=\"example_box\">\n  Alex:<br/>\nHey Justin, We'd love to host a Zoom game for your team. Happy to expedite everything for your event on Monday. How many participants and what time are you looking at?<span class=\"label_box\">TIMING & PROCESS</span><span class=\"label_text\"> Let me know if you'd prefer to hop on a quick videochat tomorrow to go over all the logistics.</span>\n</div>\n"
}
[/block]



### Example Input

```
Alex:
Hey Justin, We'd love to host a Zoom game for your team. Happy to expedite everything for your event on Monday. How many participants and what time are you looking at? Let me know if you'd prefer to hop on a quick videochat tomorrow to go over all the logistics.
```



### Example Output

```json
{
   "type":"sales-insights",
   "skill":"sales-insights",
   "name":"Timing & Process",
   "value":"Let me know if you'd prefer to hop on a quick videochat tomorrow to go over all the logistics.",
   "speaker":"Alex",
   "span_text":"Let me know if you'd prefer to hop on a quick videochat tomorrow to go over all the logistics.",
   "span":[
      174,
      268
   ],
   "output_spans":[
      {
         "section":0,
         "start":168,
         "end":262
      }
   ]
}
```