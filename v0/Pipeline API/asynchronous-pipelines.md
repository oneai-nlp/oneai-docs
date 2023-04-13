---
title: "Asynchronous Pipelines"
slug: "asynchronous-pipelines"
excerpt: "The Pipeline API has two methods of invocation: synchronous, and asynchronous."
hidden: false
createdAt: "2022-08-24T08:37:30.864Z"
updatedAt: "2023-04-09T11:23:59.104Z"
---
When the content you wish to process is either located online and requires download, or if it's in a source format that requires text conversion, like an audio file that requires transcription, or a PDF document that requires OCR, then invoking an asynchronous pipeline is the better choice. If you invoke a sync pipeline, you will have to wait for the response for as much time as it takes to process.

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline/async' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
-d '{
    "input": "<URL-TO-AUDIO-FILE>",
    "input_type": "conversation",
		"content_type": "audio/wav",
    "steps": [
      {
        "skill": "transcribe",
        "params": {
          "speaker_detection": true
        }
      },
      {
        "skill": "summarize"
      }  
    ]
}'
```



If your file is local, you could use a different method to upload it by using an API platform such as POSTMAN. In this case, you should provide all of the call parameters in the URL itself, while the file will be your only input, selected directly from your local environment.

```curl cURL
curl -X POST \
'https://api.oneai.com/api/v0/pipeline/async/file?pipeline={"steps":[{"skill":"transcribe", "params":{"engine":"whisper","expected_languages":["<LANGUAGE CODE>"],"speaker_detection":true}}], "input_type":"conversation","content_type":"audio/mp3"}
' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
```



Here is an example of such a file picked under "Body" section inside POSTMAN, using the "binary" option. Do remember to provide your API key as a header for this call as well (under "Headers"):

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3bffb52-image.png",
        null,
        ""
      ],
      "align": "center",
      "border": true
    }
  ]
}
[/block]



The response for an async Pipeline invocation will contain a task ID:

```json
{
  "status":"QUEUED",
  "task_id":"075f954c-e1d7-4b80-b24d-e460fd266c2c"
}
```



Now you can poll `/async/tasks/075f954c-e1d7-4b80-b24d-e460fd266c2`. Expect the status to be RUNNING as long as the job is still running. You can stop polling once the status changes to either COMPLETED or FAILED. If the status is COMPLETED, you can find the pipeline result in the `result` field, if it is FAILED, you can find the error in the `error` field.

```curl
curl -X 'GET' \
  'https://api.oneai.com/api/v0/pipeline/async/tasks/075f954c-e1d7-4b80-b24d-e460fd266c2c' \
  -H 'accept: application/json' \
  -H 'api-key: <YOUR-API-KEY-HERE>'
```



Once the status is `COMPLETED`, you can fetch the results of the Pipeline API from the `result` field.

```json JSON Response
{
   "result":{
      "input_text":"<THE-TEXT-EXTRACTED-FROM-THE-INPUT-FILE>",
      "status":"success",
      "error":null,
      "output":[
         {
            "text_generated_by_step_name":"input",
            "text_generated_by_step_id":0,
            "text":"<THE-TEXT-EXTRACTED-FROM-THE-INPUT-FILE>",
            "labels":[
               {
                  "type":"detect-language",
                  "skill":"detect-language",
                  "name":"language",
                  "value":"Spanish",
                  "speaker":null,
                  "data":null,
                  "span_text":null,
                  "span":null,
                  "output_spans":null,
                  "origin":null,
                  "input_spans":null
               }
            ]
         }
      ],
      "stats":{
         "concurrency_wait_time":0.0,
         "total_running_jobs":1,
         "total_waiting_jobs":0
      }
   },
   "task_id":"075f954c-e1d7-4b80-b24d-e460fd266c2c",
   "status":"COMPLETED",
   "completion_time":"2022-08-21T09:15:39.040000",
   "creation_time":"2022-08-21T09:15:39.007000"
}
```