---
title: "File Uploads"
slug: "file-uploads"
excerpt: "In order to analyze files, you can upload them directly to a Pipeline query, either synchronously or asynchronously."
hidden: false
createdAt: "2022-08-21T09:53:11.697Z"
updatedAt: "2023-01-10T09:01:01.155Z"
---
## Note about cloud-stored files

If your files are stored in some cloud storage, and you can provide API access to them, it is more efficient to simply use the file URL as an input to the Pipeline API rather than uploading it. 

```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const url = "https://aws.amazon.com/some-bucket/some-object.wav?access-token=some-token";
const pipeline = new oneai.Pipeline(
    oneai.skills.transcribe(),
    oneai.skills.summarize()
);

pipeline.run(url).then(console.log);
```
```python
import oneai

url = "https://aws.amazon.com/some-bucket/some-object.wav?access-token=some-token"
pipeline = oneai.Pipeline(
  steps = [
    oneai.skills.Transcribe(),
    oneai.skills.Summarize()
  ]
)

output = pipeline.run(url)
```



To learn how to enable the Pipeline API access to your cloud-stored files, please refer to the specific cloud docs. Here are [AWS S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html) and [Google Cloud](http://google.com) solutions.

## Synchronous file uploads

For small files, you can simply send their data encoded in base64 as the `input` parameter. This is a less efficient upload and will take longer, however, if you need a synchronous response from the API, this is the way to go.

```javascript Node.js
const { OneAI } = require("oneai");
const fs = require("fs");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const text = fs.readFileSync("<YOUR-FILE-PATH>", {encoding: "base64"});;
const pipeline = new oneai.Pipeline(
    oneai.skills.transcribe()
    oneai.skills.summarize()
);

pipeline.run(text).then(console.log);
```
```python
import oneai
import base64

with open("<YOUR-FILE-PATH>", "rb") as f:
  textParsed = base64.b64encode(f.read())
oneai.api_key = "<YOUR-API-KEY-HERE>"
text = textParsed
pipeline = oneai.Pipeline(
  steps = [
    oneai.skills.Transcribe(),
    oneai.skills.Summarize()
  ]
)

output = pipeline.run(text)
```



## Asynchronous file uploads

For bigger files, such as OCR and Audio/Video files, you can use the [asynchronous Pipeline API](https://docs.oneai.com/docs/sync-vs-async#asynchronous-pipelines) with the pipeline payload as a URL-encoded query parameter.

So you can encode this payload (notice there is no `input` field)...

```json Decoded query
{
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
}
```



..and generate the following request, notice the added `pipeline` query parameter in the `url`

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline/async/file?pipeline=%7B%0A%09%09%22content_type%22%3A%20%22audio%2Fwav%22%2C%0A%20%20%20%20%22steps%22%3A%20%5B%0A%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%22skill%22%3A%20%22transcribe%22%2C%0A%20%20%20%20%20%20%20%20%22params%22%3A%20%7B%0A%20%20%20%20%20%20%20%20%20%20%22speaker_detection%22%3A%20true%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%2C%0A%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%22skill%22%3A%20%22summarize%22%0A%20%20%20%20%20%20%7D%20%20%0A%20%20%20%20%5D%0A%7D' \
-H 'accept: application/json' \
-H 'Content-Type: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
--upload-file "<PATH-TO-LOCAL-FILE>"
```



An upload is by definition an async Pipeline run. So the previous curl will return a `task_id` which you can poll and expect results to be returned in the exact same way a simple async Pipeline returns them.

### Asynchronous file uploads using our SDKs

Our SDKs help you make asynchronous file uploads even easier, as they encapsulate the upload operation and even do the polling for you, so you eventually get a response as if you were working against a synchronous API.

```javascript Node.js
const { OneAI } = require("oneai");

const oneai = new OneAI("<YOUR-API-KEY-HERE>");
const pipeline = new oneai.Pipeline(
  oneai.skills.transcribe({
    speaker_detection: true
  }),
  oneai.skills.summarize({
);

pipeline.runFile("<PATH-TO-LOCAL-FILE>").then(console.log);
```
```python
import oneai

oneai.api_key = "<YOUR-API-KEY-HERE>"

pipeline = oneai.Pipeline(steps=[
    oneai.skills.Transcribe(),
    oneai.skills.Summarize(),
])

async def main():
    with open('<PATH-TO-LOCAL-FILE>', 'rb') as inputf:
        output = await pipeline.run_async(inputf)

asyncio.run(main())
```