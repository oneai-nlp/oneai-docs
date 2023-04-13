---
title: "🟢Subheading Benchmarks"
slug: "subheadline-benchmarks"
excerpt: "Dataset name: [Subheadings_OneAI_v1.3](https://github.com/power-of-language/Benchmarks/tree/main/Subheadings)"
hidden: false
createdAt: "2022-09-16T14:01:18.769Z"
updatedAt: "2022-09-21T09:56:44.663Z"
---
# Dataset

Name: [Subheadings_OneAI_v1.3](https://github.com/power-of-language/Benchmarks/tree/main/Subheadings)  
Datapoints: 32,561 (tested & reported), 10,000 (published)  
Sources: Various sources for news & blogs from various domains (news, politics, tech, finance, etc.) 

## Results Overview

| [Grade](https://docs.oneai.com/docs/rouge-metrics-for-summary-headline) | model                                                                                   | [Rouge1](https://docs.oneai.com/docs/rouge-metrics-for-summary-headline) | [RougeL](https://docs.oneai.com/docs/rouge-metrics-for-summary-headline) | RougeLsum |
| :---------------------------------------------------------------------- | :-------------------------------------------------------------------------------------- | :----------------------------------------------------------------------- | :----------------------------------------------------------------------- | :-------- |
| 🟢A                                                                     | **Ours (_One-AI-subheading-v1.7_)**                                                     | 0.469                                                                    | 0.464                                                                    | 0.464     |
| 🟠F                                                                     | SOTA open-source model 1                                                                | 0.186                                                                    | 0.178                                                                    | 0.178     |
| 🟠F                                                                     | [SOTA open-source model 2](https://huggingface.co/Lysa/subheading_generator_en)         | 0.133                                                                    | 0.044                                                                    | 0.127     |
|                                                                         | _Did we miss a model? [suggest one and we'll add it](https://www.oneai.com/contact-us)_ |                                                                          |                                                                          |           |

Note: see our [overview on the **Rouge** metrics](https://docs.oneai.com/docs/rouge-metrics-for-summary-headline)

## Detailed results

### Ours (_One-AI-subheadling-v1.7_)

![](https://files.readme.io/fd6bf72-sub_oneai.png)

### SOTA open-source model 1

![](https://files.readme.io/9840b16-other_one.png)

### SOTA open-source model 2

![](https://files.readme.io/b97adff-subheading3.png)