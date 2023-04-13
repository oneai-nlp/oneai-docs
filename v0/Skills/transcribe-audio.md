---
title: "Transcribe Audio"
slug: "transcribe-audio"
excerpt: "Transcribes audio files into text that other skills can process.\nGenerates a new output."
hidden: false
createdAt: "2022-08-18T08:17:31.060Z"
updatedAt: "2023-04-02T09:46:59.621Z"
---
> 📘 Use Transcribe Audio Skill to:
> 
> - [Transcribe conversations](https://studio.oneai.com/?pipeline=czIRwV)

> 🚦 [Benchmarks](https://docs.oneai.com/docs/transcribe-audio-benchmarks)
> 
> | Grade | Benchmark                                                                          | Accuracy   | WER (lower is better) |
> | :---- | :--------------------------------------------------------------------------------- | :--------- | :-------------------- |
> | 🟢A+  | [**YouTube Videos**](https://docs.oneai.com/docs/transcribe-audio-benchmarks)      | **93.42%** | 6.58%                 |
> | 🟢A+  | [**News**](https://docs.oneai.com/docs/transcribe-audio-benchmarks)                | **96.13%** | 3.87%                 |
> | 🟢A+  | [**Phone Earning Calls**](https://docs.oneai.com/docs/transcribe-audio-benchmarks) | **93.09%** | 6.09%                 |
> 
> [_See comparison with other services_](https://docs.oneai.com/docs/transcribe-audio-benchmarks)

## Audio Inputs

See [File Uploads](./file-uploads) to read about uploading audio files (`.mp3`, `.wav`, etc.).

## Synchronous vs Asynchronous considerations

We recommend using [asynchronous pipelines](doc:asynchronous-pipelines) to transcribe an audio file.  
It is also possible to use a synchronous Pipeline call with the limitation that the audio file will not exceed 8 minutes.

## Parameters

| Parameter             | Type    | Description                                                                                                                                                                                         | Default   |
| :-------------------- | :------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------- |
| `speaker_detection`   | boolean | Automatically detect individual speakers in the audio, and include in utterances in transcription.                                                                                                  | `true`    |
| `timestamp_per_label` | boolean | Enhance other skills-generated labels with the corresponding timestamp of the words in the label. Whisper can not provide this data.                                                                | `true`    |
| `timestamp_per_word`  | boolean | Generate a `word` label for every transcribed word and include both text and audio timestamps (start & end)                                                                                         | `false`   |
| `engine`              | string  | Either `default` or `whisper`. Determines which transcription engine to use. `default` is the premium One AI transcription service while `whisper` is an open-source engine.                        | `default` |
| `expected_languages`  | string  | like in "multilingual" - copyyyyyyyyyyy . could be used to define the language of audio. The default does not support any language othet than English, while Whisper can be used for all languages. | `default` |

## Output text

The transcribed text in the response JSON in `output.text` field

## Example

As an example, let's transcribe the following audio file:

[block:html]
{
  "html": "<div>\n  <audio controls>\n    <source src=\"https://storage.googleapis.com/web-assests-oneai/How%20I%20create%20long%20hours%20of%20Deep%20Work%20-%20PhD%20student.wav\" type=\"audio/wav\">\n  </audio>\n</div>\n\n<style></style>"
}
[/block]



#### Request

URL encoding the following payload as described in [File Uploads](doc:file-uploads)...

```json
{
    "input_type": "conversation",
    "content_type": "audio/wav",
    "steps": [
      {
        "skill": "transcribe",
        "params": {
          "speaker_detection": true
        }
      }  
    ]
}
```



... and attaching it to this Pipeline API call

```curl
curl -X POST \
'https://api.oneai.com/api/v0/pipeline/async/file?pipeline=%7B%0A%20%20%20%20%22input_type%22%3A%20%22conversation%22%2C%0A%20%20%20%20%22content_type%22%3A%20%22audio%2Fwav%22%2C%0A%20%20%20%20%22steps%22%3A%20%5B%0A%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%22skill%22%3A%20%22transcribe%22%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%5D%0A%7D' \
-H 'accept: application/json' \
-H 'api-key: <YOUR-API-KEY-HERE>' \
--upload-file '<PATH-TO-LOCAL-FILE>'
```
```javascript Node.js
// Node.js SDK currently supports only synchronous pipelines
// Asynchronous support is coming soon
const { OneAI } = require("oneai");
const oneai = new
OneAI("<YOUR-API-KEY-HERE>");
const pipeline = new oneai.Pipeline(
oneai.skills.transcribe({ speaker_detection: true, }) );
pipeline.runFile("YOUR_FILE_PATH").then(console.log);
```
```python
# Python SDK currently supports only synchronous pipelines
# Asynchronous support is coming soon
import oneai
import base64

with open("<YOUR-FILE-PATH>", "rb") as f:
  textParsed = base64.b64encode(f.read())
oneai.api_key = "<YOUR-API-KEY-HERE>"
pipeline = oneai.Pipeline(
  steps = [
		oneai.skills.Transcribe(
  		speaker_detection=True,
		),
  ]
)

conversation = oneai.Conversation(
  textParsed
)

output = pipeline.run(conversation)
```



#### Response

```json
{
   "result":{
      "input_text":"[00:00:00.170] speaker 0:\nA so today I want to talk to you about the concept of deep work. So when we look at artists, presidents and also sciences, we really see that they craft dedicated time to put in the hours for deep work. And I find it personally a really interesting concept, and I've seen in my own work when I really put dedicated time towards a deeply working into my science and into my craft that I get better a lot faster and then I get results quite fast. And today I want to give you some tips, tools, and techniques to really allow for this deep work to happen. So a deep work was kind of introduced by call Newport under the name deep work, but I've known it for a little bit longer under the name of flow. And I think that when we look at different schedules of people that we can really see that most artists and most scientists usually have these dedicated time blocks for deep work. So I personally really like this book daily rituals by amazing curry and he really nice deep into these daily rituals are famous people. So I want to show you one that I really like and it's the first one by Benjamin Franklin and he demonstrated his schedule that was first in the morning to wake up and do the question what good shall I do today? So we talked about doing one thing every day and I think that kind of amplifies this. Then there's a new afternoon and in the evening he has another question which is what good have I done today? And I really like his schedule but today I want to give you the tips and tricks to kind of design your own schedule such that you may optimize your workflow for deep work. So the first thing first is to kind of know thyself and I think knowing yourself and knowing your own optimal working hours is really important. Because when I read the book of mason curry on daily rituals, I really saw that different artists, different scientists have different peak moments. So some of the artists he describes, they say that they work best at night, so they always craft in a few hours every night that they work on writing their book, for example, or painting. Whereas other people in this book are really early morning people. And they dedicate the time in the morning, so every morning they have a block of around three hours where they work. And I think in general, it's not really important when you work, although all the morning people on YouTube would say differently. But I think it's more important to be consistent every day that you have a couple of hours every day where you are alone without friends and distraction of your phone or computer and where you really dedicate your time towards that one project or one goal that you want to go towards. So the second thing I find personally really important is to optimize your space for deep work. So for example, I have my desk behind me and I usually only do work at this desk. So I don't really do leisure time or I don't do gaming. I don't watch YouTube videos at this desk. I only do work. And I personally also like going, for example, to different spaces like a library or a cafe. When I'm kind of stuck or when I want to work on another dedicated project, so personally I really like writing in cafes and I think it's kind of your task to find a space in your house that's dedicated to deep work. And maybe some of you will have only a one space bedroom. But even then, I think you can dedicate a tiny corner of your room or even a space in your bed where when you sit there, you will only do deep work. And I think this slowly kind of rewires the way we think about that space. And once we enter that space, we will automatically go into this flow of deep working. The third thing I find really important is to have a clear goal. So every deep working session I would have one goal or one thing I kind of want to finish. So for example, it could be making a YouTube video, but it could also be a dedicated programming practice that I wanted to do that day or having something finished for my science, right? But every day could be different, but I think it's quite important to have this one go quite clear for yourself that you would work towards that during your deep working hours. Because I think if we go into deep work without any goal or any direction, we usually just end up kind of twiddling our time away. So it's really nice if before each session you set a clear goal. And the fourth thing I want to talk about is to be a little bit flexible with your time. So sometimes we set in two hours and then immediately after these two hours, we plan in something else. But one thing I've noticed a lot is that sometimes I just have really good sessions and I kind of want to keep on working all day or all evening and then if I have something immediately planned after that's just kind of a sad thing, right? Because you're finally in this flow and this amazing deep work mindset. So what I would do is to be a little bit flexible with your schedule. So I personally don't really over plan. Things I usually set dedicated time blocks for things I want to accomplish that day. But the rest of the time is usually a little bit more free such that if I want to continue my two hours of deep work to the rest of the day that this is possible and the 5th thing is just something I personally find really important and that's the mind body connection and I've talked about this a lot, but I want to keep emphasizing this. So I think personally for myself, I'm usually pretty jittery and pretty high energy throughout the day. So if I don't move, I get really stuck in my thoughts sometimes. So I think it's really important to also when you do deep work, you can also move around, like some of us think when we do deep work, we have to be really focused and really intensely scheduled in one place, but I think it's also okay to bring in movement throughout these deep working sessions. Because I think once you are stuck in a little problem, for example, to walk around or to go outside or to take your work to another place, it's kind of brings new energy to your thought process. And I think this kind of movement and flexibility in your body kind of allows your mind to sometimes relax and really solve the solutions a lot faster than if you just stay dedicatedly at your spot for. 6 hours. So yeah, these were my tips on deep work for now. I would also highly recommend to read the book. He really goes into how he schedules deep work, how he has different opinions on how to schedule it. And I learned a lot from this book. It's still one of my favorites, and I revisit it. A lot of times. And I also want to say if you have any tips or tricks for me or if you know an amazing way to get to deep work, I would love to hear them so put them down in the comments below and otherwise see you next week. Bye.\n\n",
      "status":"success",
      "error":null,
      "output":[
         {
            "text_generated_by_step_name":"transcribe",
            "text_generated_by_step_id":1,
            "text":"[00:00:00.170] speaker 0:\nA so today I want to talk to you about the concept of deep work. So when we look at artists, presidents and also sciences, we really see that they craft dedicated time to put in the hours for deep work. And I find it personally a really interesting concept, and I've seen in my own work when I really put dedicated time towards a deeply working into my science and into my craft that I get better a lot faster and then I get results quite fast. And today I want to give you some tips, tools, and techniques to really allow for this deep work to happen. So a deep work was kind of introduced by call Newport under the name deep work, but I've known it for a little bit longer under the name of flow. And I think that when we look at different schedules of people that we can really see that most artists and most scientists usually have these dedicated time blocks for deep work. So I personally really like this book daily rituals by amazing curry and he really nice deep into these daily rituals are famous people. So I want to show you one that I really like and it's the first one by Benjamin Franklin and he demonstrated his schedule that was first in the morning to wake up and do the question what good shall I do today? So we talked about doing one thing every day and I think that kind of amplifies this. Then there's a new afternoon and in the evening he has another question which is what good have I done today? And I really like his schedule but today I want to give you the tips and tricks to kind of design your own schedule such that you may optimize your workflow for deep work. So the first thing first is to kind of know thyself and I think knowing yourself and knowing your own optimal working hours is really important. Because when I read the book of mason curry on daily rituals, I really saw that different artists, different scientists have different peak moments. So some of the artists he describes, they say that they work best at night, so they always craft in a few hours every night that they work on writing their book, for example, or painting. Whereas other people in this book are really early morning people. And they dedicate the time in the morning, so every morning they have a block of around three hours where they work. And I think in general, it's not really important when you work, although all the morning people on YouTube would say differently. But I think it's more important to be consistent every day that you have a couple of hours every day where you are alone without friends and distraction of your phone or computer and where you really dedicate your time towards that one project or one goal that you want to go towards. So the second thing I find personally really important is to optimize your space for deep work. So for example, I have my desk behind me and I usually only do work at this desk. So I don't really do leisure time or I don't do gaming. I don't watch YouTube videos at this desk. I only do work. And I personally also like going, for example, to different spaces like a library or a cafe. When I'm kind of stuck or when I want to work on another dedicated project, so personally I really like writing in cafes and I think it's kind of your task to find a space in your house that's dedicated to deep work. And maybe some of you will have only a one space bedroom. But even then, I think you can dedicate a tiny corner of your room or even a space in your bed where when you sit there, you will only do deep work. And I think this slowly kind of rewires the way we think about that space. And once we enter that space, we will automatically go into this flow of deep working. The third thing I find really important is to have a clear goal. So every deep working session I would have one goal or one thing I kind of want to finish. So for example, it could be making a YouTube video, but it could also be a dedicated programming practice that I wanted to do that day or having something finished for my science, right? But every day could be different, but I think it's quite important to have this one go quite clear for yourself that you would work towards that during your deep working hours. Because I think if we go into deep work without any goal or any direction, we usually just end up kind of twiddling our time away. So it's really nice if before each session you set a clear goal. And the fourth thing I want to talk about is to be a little bit flexible with your time. So sometimes we set in two hours and then immediately after these two hours, we plan in something else. But one thing I've noticed a lot is that sometimes I just have really good sessions and I kind of want to keep on working all day or all evening and then if I have something immediately planned after that's just kind of a sad thing, right? Because you're finally in this flow and this amazing deep work mindset. So what I would do is to be a little bit flexible with your schedule. So I personally don't really over plan. Things I usually set dedicated time blocks for things I want to accomplish that day. But the rest of the time is usually a little bit more free such that if I want to continue my two hours of deep work to the rest of the day that this is possible and the 5th thing is just something I personally find really important and that's the mind body connection and I've talked about this a lot, but I want to keep emphasizing this. So I think personally for myself, I'm usually pretty jittery and pretty high energy throughout the day. So if I don't move, I get really stuck in my thoughts sometimes. So I think it's really important to also when you do deep work, you can also move around, like some of us think when we do deep work, we have to be really focused and really intensely scheduled in one place, but I think it's also okay to bring in movement throughout these deep working sessions. Because I think once you are stuck in a little problem, for example, to walk around or to go outside or to take your work to another place, it's kind of brings new energy to your thought process. And I think this kind of movement and flexibility in your body kind of allows your mind to sometimes relax and really solve the solutions a lot faster than if you just stay dedicatedly at your spot for. 6 hours. So yeah, these were my tips on deep work for now. I would also highly recommend to read the book. He really goes into how he schedules deep work, how he has different opinions on how to schedule it. And I learned a lot from this book. It's still one of my favorites, and I revisit it. A lot of times. And I also want to say if you have any tips or tricks for me or if you know an amazing way to get to deep work, I would love to hear them so put them down in the comments below and otherwise see you next week. Bye.\n\n",
            "labels":[
               
            ]
         }
      ],
      "stats":{
         "concurrency_wait_time":0.0,
         "total_running_jobs":1,
         "total_waiting_jobs":0
      }
   },
   "task_id":"8d05788e-452f-4bb0-b75e-005fc1a62971",
   "status":"COMPLETED",
   "completion_time":"2022-08-24T12:30:43.530000",
   "creation_time":"2022-08-24T12:29:44.528000"
}
```



#### `timestamp_per_label` Example

When setting `timestamp_per_word` to `true`, each label generated by other skill will be enriched with the audio indices. That is, the same way labels describe the portion of the text they are referring to by stating the spans, they will also do it for audio by stating starting and ending timestamps of the relevant portion of the text in the original audio file.

For example, if we take the same input file from the first example, and run it against the same payload as before only this time we also add `Emotions` skill:

```json
{
    "input_type": "conversation",
    "content_type": "audio/wav",
    "steps": [
      {
        "skill": "transcribe"
      },
      {
        "skill": "emotions"
      } ,
    ]
}
```



Then the response will look like this. Notice how the `emotion` labels received two extra fields that weren't there before: `timestamp` and `timestamp_end`.

```json
{
   "result":{
      "input_text":"[00:00:00.170] speaker 0:\nA so today I want to talk to you about the concept of deep work. So when we look at artists, presidents and also sciences, we really see that they craft dedicated time to put in the hours for deep work. And I find it personally a really interesting concept, and I've seen in my own work when I really put dedicated time towards a deeply working into my science and into my craft that I get better a lot faster and then I get results quite fast. And today I want to give you some tips, tools, and techniques to really allow for this deep work to happen. So a deep work was kind of introduced by call Newport under the name deep work, but I've known it for a little bit longer under the name of flow. And I think that when we look at different schedules of people that we can really see that most artists and most scientists usually have these dedicated time blocks for deep work. So I personally really like this book daily rituals by amazing curry and he really nice deep into these daily rituals are famous people. So I want to show you one that I really like and it's the first one by Benjamin Franklin and he demonstrated his schedule that was first in the morning to wake up and do the question what good shall I do today? So we talked about doing one thing every day and I think that kind of amplifies this. Then there's a new afternoon and in the evening he has another question which is what good have I done today? And I really like his schedule but today I want to give you the tips and tricks to kind of design your own schedule such that you may optimize your workflow for deep work. So the first thing first is to kind of know thyself and I think knowing yourself and knowing your own optimal working hours is really important. Because when I read the book of mason curry on daily rituals, I really saw that different artists, different scientists have different peak moments. So some of the artists he describes, they say that they work best at night, so they always craft in a few hours every night that they work on writing their book, for example, or painting. Whereas other people in this book are really early morning people. And they dedicate the time in the morning, so every morning they have a block of around three hours where they work. And I think in general, it's not really important when you work, although all the morning people on YouTube would say differently. But I think it's more important to be consistent every day that you have a couple of hours every day where you are alone without friends and distraction of your phone or computer and where you really dedicate your time towards that one project or one goal that you want to go towards. So the second thing I find personally really important is to optimize your space for deep work. So for example, I have my desk behind me and I usually only do work at this desk. So I don't really do leisure time or I don't do gaming. I don't watch YouTube videos at this desk. I only do work. And I personally also like going, for example, to different spaces like a library or a cafe. When I'm kind of stuck or when I want to work on another dedicated project, so personally I really like writing in cafes and I think it's kind of your task to find a space in your house that's dedicated to deep work. And maybe some of you will have only a one space bedroom. But even then, I think you can dedicate a tiny corner of your room or even a space in your bed where when you sit there, you will only do deep work. And I think this slowly kind of rewires the way we think about that space. And once we enter that space, we will automatically go into this flow of deep working. The third thing I find really important is to have a clear goal. So every deep working session I would have one goal or one thing I kind of want to finish. So for example, it could be making a YouTube video, but it could also be a dedicated programming practice that I wanted to do that day or having something finished for my science, right? But every day could be different, but I think it's quite important to have this one go quite clear for yourself that you would work towards that during your deep working hours. Because I think if we go into deep work without any goal or any direction, we usually just end up kind of twiddling our time away. So it's really nice if before each session you set a clear goal. And the fourth thing I want to talk about is to be a little bit flexible with your time. So sometimes we set in two hours and then immediately after these two hours, we plan in something else. But one thing I've noticed a lot is that sometimes I just have really good sessions and I kind of want to keep on working all day or all evening and then if I have something immediately planned after that's just kind of a sad thing, right? Because you're finally in this flow and this amazing deep work mindset. So what I would do is to be a little bit flexible with your schedule. So I personally don't really over plan. Things I usually set dedicated time blocks for things I want to accomplish that day. But the rest of the time is usually a little bit more free such that if I want to continue my two hours of deep work to the rest of the day that this is possible and the 5th thing is just something I personally find really important and that's the mind body connection and I've talked about this a lot, but I want to keep emphasizing this. So I think personally for myself, I'm usually pretty jittery and pretty high energy throughout the day. So if I don't move, I get really stuck in my thoughts sometimes. So I think it's really important to also when you do deep work, you can also move around, like some of us think when we do deep work, we have to be really focused and really intensely scheduled in one place, but I think it's also okay to bring in movement throughout these deep working sessions. Because I think once you are stuck in a little problem, for example, to walk around or to go outside or to take your work to another place, it's kind of brings new energy to your thought process. And I think this kind of movement and flexibility in your body kind of allows your mind to sometimes relax and really solve the solutions a lot faster than if you just stay dedicatedly at your spot for. 6 hours. So yeah, these were my tips on deep work for now. I would also highly recommend to read the book. He really goes into how he schedules deep work, how he has different opinions on how to schedule it. And I learned a lot from this book. It's still one of my favorites, and I revisit it. A lot of times. And I also want to say if you have any tips or tricks for me or if you know an amazing way to get to deep work, I would love to hear them so put them down in the comments below and otherwise see you next week. Bye.\n\n",
      "status":"success",
      "error":null,
      "output":[
         {
            "text_generated_by_step_name":"transcribe",
            "text_generated_by_step_id":1,
            "text":"[00:00:00.170] speaker 0:\nA so today I want to talk to you about the concept of deep work. So when we look at artists, presidents and also sciences, we really see that they craft dedicated time to put in the hours for deep work. And I find it personally a really interesting concept, and I've seen in my own work when I really put dedicated time towards a deeply working into my science and into my craft that I get better a lot faster and then I get results quite fast. And today I want to give you some tips, tools, and techniques to really allow for this deep work to happen. So a deep work was kind of introduced by call Newport under the name deep work, but I've known it for a little bit longer under the name of flow. And I think that when we look at different schedules of people that we can really see that most artists and most scientists usually have these dedicated time blocks for deep work. So I personally really like this book daily rituals by amazing curry and he really nice deep into these daily rituals are famous people. So I want to show you one that I really like and it's the first one by Benjamin Franklin and he demonstrated his schedule that was first in the morning to wake up and do the question what good shall I do today? So we talked about doing one thing every day and I think that kind of amplifies this. Then there's a new afternoon and in the evening he has another question which is what good have I done today? And I really like his schedule but today I want to give you the tips and tricks to kind of design your own schedule such that you may optimize your workflow for deep work. So the first thing first is to kind of know thyself and I think knowing yourself and knowing your own optimal working hours is really important. Because when I read the book of mason curry on daily rituals, I really saw that different artists, different scientists have different peak moments. So some of the artists he describes, they say that they work best at night, so they always craft in a few hours every night that they work on writing their book, for example, or painting. Whereas other people in this book are really early morning people. And they dedicate the time in the morning, so every morning they have a block of around three hours where they work. And I think in general, it's not really important when you work, although all the morning people on YouTube would say differently. But I think it's more important to be consistent every day that you have a couple of hours every day where you are alone without friends and distraction of your phone or computer and where you really dedicate your time towards that one project or one goal that you want to go towards. So the second thing I find personally really important is to optimize your space for deep work. So for example, I have my desk behind me and I usually only do work at this desk. So I don't really do leisure time or I don't do gaming. I don't watch YouTube videos at this desk. I only do work. And I personally also like going, for example, to different spaces like a library or a cafe. When I'm kind of stuck or when I want to work on another dedicated project, so personally I really like writing in cafes and I think it's kind of your task to find a space in your house that's dedicated to deep work. And maybe some of you will have only a one space bedroom. But even then, I think you can dedicate a tiny corner of your room or even a space in your bed where when you sit there, you will only do deep work. And I think this slowly kind of rewires the way we think about that space. And once we enter that space, we will automatically go into this flow of deep working. The third thing I find really important is to have a clear goal. So every deep working session I would have one goal or one thing I kind of want to finish. So for example, it could be making a YouTube video, but it could also be a dedicated programming practice that I wanted to do that day or having something finished for my science, right? But every day could be different, but I think it's quite important to have this one go quite clear for yourself that you would work towards that during your deep working hours. Because I think if we go into deep work without any goal or any direction, we usually just end up kind of twiddling our time away. So it's really nice if before each session you set a clear goal. And the fourth thing I want to talk about is to be a little bit flexible with your time. So sometimes we set in two hours and then immediately after these two hours, we plan in something else. But one thing I've noticed a lot is that sometimes I just have really good sessions and I kind of want to keep on working all day or all evening and then if I have something immediately planned after that's just kind of a sad thing, right? Because you're finally in this flow and this amazing deep work mindset. So what I would do is to be a little bit flexible with your schedule. So I personally don't really over plan. Things I usually set dedicated time blocks for things I want to accomplish that day. But the rest of the time is usually a little bit more free such that if I want to continue my two hours of deep work to the rest of the day that this is possible and the 5th thing is just something I personally find really important and that's the mind body connection and I've talked about this a lot, but I want to keep emphasizing this. So I think personally for myself, I'm usually pretty jittery and pretty high energy throughout the day. So if I don't move, I get really stuck in my thoughts sometimes. So I think it's really important to also when you do deep work, you can also move around, like some of us think when we do deep work, we have to be really focused and really intensely scheduled in one place, but I think it's also okay to bring in movement throughout these deep working sessions. Because I think once you are stuck in a little problem, for example, to walk around or to go outside or to take your work to another place, it's kind of brings new energy to your thought process. And I think this kind of movement and flexibility in your body kind of allows your mind to sometimes relax and really solve the solutions a lot faster than if you just stay dedicatedly at your spot for. 6 hours. So yeah, these were my tips on deep work for now. I would also highly recommend to read the book. He really goes into how he schedules deep work, how he has different opinions on how to schedule it. And I learned a lot from this book. It's still one of my favorites, and I revisit it. A lot of times. And I also want to say if you have any tips or tricks for me or if you know an amazing way to get to deep work, I would love to hear them so put them down in the comments below and otherwise see you next week. Bye.\n\n",
            "labels":[
               {
                  "type":"emotion",
                  "skill":"emotions",
                  "name":"happiness",
                  "value":null,
                  "speaker":"speaker 0",
                  "data":null,
                  "span_text":"Because you're finally in this flow and this amazing deep work mindset.",
                  "span":[
                     4824,
                     4895
                  ],
                  "output_spans":[
                     {
                        "section":0,
                        "start":4798,
                        "end":4869
                     }
                  ],
                  "origin":null,
                  "input_spans":null,
                  "timestamp":"00:04:280.730",
                  "timestamp_end":"00:04:284.510"
               },
               {
                  "type":"emotion",
                  "skill":"emotions",
                  "name":"happiness",
                  "value":null,
                  "speaker":"speaker 0",
                  "data":null,
                  "span_text":"And I learned a lot from this book.",
                  "span":[
                     6503,
                     6538
                  ],
                  "output_spans":[
                     {
                        "section":0,
                        "start":6477,
                        "end":6512
                     }
                  ],
                  "origin":null,
                  "input_spans":null,
                  "timestamp":"00:06:377.810",
                  "timestamp_end":"00:06:379.490"
               },
            ]
         }
      ],
      "stats":{
         "concurrency_wait_time":0.0,
         "total_running_jobs":1,
         "total_waiting_jobs":0
      }
   },
   "task_id":"d2296e2e-a063-416d-a5ce-0863da1e5adb",
   "status":"COMPLETED",
   "completion_time":"2022-08-25T06:51:46.825000",
   "creation_time":"2022-08-25T06:50:42.561000"
}
```