---
title: "🟢Emotions Benchmarks"
slug: "emotions-benchmarks"
excerpt: "See our [Notebook and dataset to reproduce results](https://github.com/power-of-language/summary-example)"
hidden: false
createdAt: "2022-09-15T10:36:36.961Z"
updatedAt: "2022-12-25T13:43:00.424Z"
---
## Dataset

Dataset name: [Emotions_Go_OneAI_v1.2](https://github.com/power-of-language/Benchmarks/blob/main/Emotions/EmotionsGo_OneAI_v1.2.csv)  
Datapoints: 21,612  
Labels: anger, joy, neutral, sadness, surprise, neutral  
Description: Based on [Google's EmotionsGo](https://ai.googleblog.com/2021/10/goemotions-dataset-for-fine-grained.html) dataset, cleaned and further annotated by native-speaker human annotators.

## Results

See our [Notebook and dataset to reproduce results](https://github.com/power-of-language/Benchmarks/tree/main/Emotions)

| Grade | Model                                                                                                                          | Accuracy | Precision (Micro) | Recall (Micro) |
| :---- | :----------------------------------------------------------------------------------------------------------------------------- | :------- | :---------------- | :------------- |
| 🟡B   | **Ours _(One-AI-emotions-1.1)_**                                                                                               | **0.75** | **0.75**          | **0.75**       |
| 🟠C   | 2 [Emotion-english-distilroberta-base by j-hartmann](https://huggingface.co/j-hartmann/emotion-english-distilroberta-base)     | 0.67     | 0.62              | 0.72           |
| 🔴F   | 3 [distilbert-base-uncased-emotiom by bhadresh-savani](https://huggingface.co/bhadresh-savani/distilbert-base-uncased-emotion) | 0.44     | 0.43              | 0.44           |

Notes: Using 'Micro' measurement metric to account for inherent label imbalance in labeled data. Specifically, there are 8X more 'neutral' labels than any other emotion label. Microanalysis gives equal weight to all data points which will translate to real-world precision & recall performance.

## Methodology

### Data prep

- Emotions_go dataset was filtered to the main emotions that exhibit clearer user agreement.  
  In both user testing and in manual annotation tasks we found that other labels did not reach any agreement threshold. The other models tested were also trained on a nearly identical set of labels which stre
- Joy & Happiness labels from the dataset were merged into a unified 'joy' label

### Measurement

- As each model identifies a slightly different set of emotions, the comparison was normalized as follows:

One AI labels = ['anger', 'joy', 'neutral', 'sadness', 'surprise']  
model2 labels = ['anger', 'disgust', 'fear', 'joy', 'neutral', 'sadness', 'surprise']  
model3 labels = ['anger', 'fear', 'joy', 'love', 'neutral', 'sadness', 'surprise']

dataset labels = ['anger', 'joy', 'neutral', 'sadness', 'surprise']

- [distilbert-base-uncased-emotiom by bhadresh-savani](🔗) model does not have a neutral label so if there is no emotion with above 0.8 score the result will be considered 'neutral', 0.8 was found to provide the best results.
- As the One-AI model can detect multiple emotions per text input (as it supports per-span annotation) unlike the other 2 models that can only select a single emotion for the entire text input, we consider the sample a correct match if the correct emotions are included in detected emotions.  
  If none of the items match the golden label we consider the first item in the list.  
  For example, if the One-AI response was ['happiness', 'sadness'] and the true-label label was 'sadness' we consider the One-AI response to be 'sadness',  
  But if the golden label were 'neutral' I would take the first value in the list ('happiness') as oneai response.
- Execution command for reference models:

```python
model2 = pipeline("text-classification", model="j-hartmann/emotion-english-distilroberta-base", return_all_scores=True)

model3 = pipeline("text-classification",model='bhadresh-savani/distilbert-base-uncased-emotion', return_all_scores=True)
```