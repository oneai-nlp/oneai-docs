---
title: "Errors"
slug: "errors"
hidden: false
createdAt: "2022-09-07T08:55:06.243Z"
updatedAt: "2022-12-28T13:34:24.113Z"
---
### Error Payload Structure

```json
{
  "status_code":40009,
  "message":"Input does not match specified content type",
  "details":"Content-Type application/json does not match input of type conversation",
  "request_id":"46ac6a45-5b6b-4fd6-804f-bc94766c587e"
}
```



When the API returns an error, it returns a payload that describes it

| Field         | Description                                                               |
| :------------ | :------------------------------------------------------------------------ |
| `status_code` | A numerical code (not an HTTP status code)                                |
| `message`     | A message describing the general error                                    |
| `details`     | A more detailed explanation                                               |
| `request_id`  | Use this when you contact support with this error to uniquely identify it |

### Errors List

#### Client errors

| `status_code` | HTTP status | message                                                 |
| :------------ | :---------- | :------------------------------------------------------ |
| 40001         | 400         | Language not supported                                  |
| 40002         | 400         | The input text is empty                                 |
| 40003         | 400         | Invalid input type for skill                            |
| 40004         | 400         | Failed to parse the conversation                        |
| 40005         | 400         | Input type not supported                                |
| 40006         | 400         | No channels in the audio file                           |
| 40007         | 400         | HTML input requires an HTML-to-text preprocessing skill |
| 40008         | 400         | Failed to parse input                                   |
| 40009         | 400         | Input does not match the specified content type         |
| 40010         | 400         | VTT conversation parsing failed                         |
| 40011         | 400         | Voice input requires `transcibe` skill                  |
| 40012         | 400         | Failed to transcribe audio                              |

#### API Key errors

| `status_code` | HTTP status | message                                               |
| :------------ | :---------- | :---------------------------------------------------- |
| 60001         | 401         | Missing API key header                                |
| 60002         | 401         | API key not found                                     |
| 60003         | 403         | Daily API key quota exceeded                          |
| 60004         | 403         | The monthly API key quota exceeded                    |
| 60005         | 403         | Daily organization quota exceeded                     |
| 60006         | 403         | The monthly organization quota exceeded               |
| 60007         | 403         | The API key is expired                                |
| 60008         | 403         | Skill not allowed                                     |
| 60009         | 429         | Exceeded the allowed number of concurrent connections |
| 60010         | 403         | Organization suspended                                |
| 60011         | 403         | Transcription quota exceeded                          |

#### Server errors

| `status_code` | HTTP status | message                               |
| :------------ | :---------- | :------------------------------------ |
| 50000         | 500         | Server error                          |
| 50001         | 500         | Failed to retrieve URL                |
| 50002         | 503         | The service is temporarily overloaded |
| 50003         | 500         | Failed to connect to the API endpoint |
| 50004         | 500         | Health check failed                   |
| 50005         | 500         | Analytics cluster request error       |