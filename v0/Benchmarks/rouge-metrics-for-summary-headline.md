---
title: "Rouge metrics for Summary & Headline"
slug: "rouge-metrics-for-summary-headline"
excerpt: "Rouge is a family of metrics that is commonly used to assess summarization models"
hidden: false
createdAt: "2022-09-15T17:48:58.631Z"
updatedAt: "2022-12-28T13:47:18.040Z"
---
### Rouge Certification Levels

Rouge metrics measure the word overlap between generated text and expected text.

Since good summaries & headings can be written differently, **Rouge scores around _50_ are considered excellent results**.

We grade models measured via Rouge scores on the following scale:  

| Grade | Rouge1 | RougeL |
| :---- | :----- | :----- |
| 🟢A+  | > 48   | > 46   |
| 🟢A   | > 45   | > 45   |
| 🟡B   | > 40   | > 40   |
| 🟠C   | > 35   | > 35   |
| 🔴F   | 0-35   | 0-35   |

### Rouge Metrics explained

_Note: This is a high-level description, designed to provide intuition for understanding Rouge metrics, for a more mathematically accurate explanation please see [this blog post](https://www.freecodecamp.org/news/what-is-rouge-and-how-it-works-for-evaluation-of-summaries-e059fb8ac840/) or the [original Rouge paper](https://aclanthology.org/W04-1013.pdf)_

- ROUGE-1: Shared words  
  Number of **words** that appear in both **model** output, and **expected **output  
  Example: 0.5 means half of the words appear in both model output and expected output
- ROUGE-2: Shared word-pairs  
  Number of **word-pairs** that appear in both **model** output, and **expected **output (as pairs)  
  Example: 0.5 means half of the adjacent word pairs appear in both model output and expected output.  
  This is a stricter metric than Rouge1, which is slightly more sensitive to the order
- ROUGE-L: Longest shared word-sequence  
  The number of **words** appear **in the exact same order**. in both **model** output, and \*\*expected  
  Example: 0.5 means half of the entire output of expected output is the same half of the entire expected text.  
  This metric is very sensitive to the generated order of words.

As two summaries or headlines are unlikely to be generated **exactly** the same (same words, order, inflections, and suffixes), Rouge metrics usually peak around 50 (0.50) while representing a very high-quality output.