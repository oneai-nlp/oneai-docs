---
title: "Overview"
slug: "analytics-api"
hidden: false
createdAt: "2022-08-15T13:51:39.404Z"
updatedAt: "2023-04-02T14:26:54.297Z"
---
## Introduction

One AI Analytics allows the transformation of a large pool of language inputs into meaningful hierarchical groups. You can then use the clustered data structure for analytics, or you can automate actions based on querying new inputs against the clustered data.

## Use-Cases

- Create a document/knowledge base as memory for a generative LLM model (e.g your internal documents or customer conversations)
- Analyze customer support tickets by clustering repeating meanings (like complaints, requests, products and more) and respond automatically.
- Cluster subject lines of articles, analyze them and post to different twitter tags.
- Cluster sales conversation highlights, analyze them, and ranks employees accordingly.

Analytics can be helpful in any case where you have large amounts of language data that need to be sorted, or grouped, so you can execute different actions on each group, without prior knowledge of the exact groups you want to split the language data into. 

## Workflow:

- ### [Create a collection](Create)
  It is possible to create as many collection as you like, a collection defines the way data is processed and allows querying and slicing the data by text meaning and meta-data.
- ### [Populate with data]\(Insert data)
  ...
- ### [Query the collection for insights](query)
  ....

## Quick Start

Let's create and query a collection in 3 minutes, [take our quick-start tutorial](quick-start)

## Understanding 'Analytics Collections' data structure 

As an example, let’s say you have plenty of support tickets, and you want to extract the most significant cases that repeat themselves. This can easily be done using Analytics; You first create a collection named “customer feedback”, and add all the tickets to the collection as items. Our clustering engine will cluster the collection for you, and you will be able to identify different groups of items.

Let’s say we have the following 5 sentences (=items):

- Your service was great
- You helped me a lot
- Can I have a discount?
- Your service is too expensive
- Why can’t your service be cheaper?

We create a collection named “customer feedback” and add those 5 items to it. The clustering engine will understand that there are two clusters here: one for praising the service and one for complaining about the service price.

| Your service was great | Your service is too expensive      |
| ---------------------- | ---------------------------------- |
| You helped me a lot.   | Can I have a discount?             |
|                        | Why can’t your service be cheaper? |

The engine is smart enough to pick the clusters itself. It can pick as few as two clusters or as many as n clusters, where n is the number of items, which is limitless. As the “title” of each cluster, one of the items in the cluster is randomly selected and written in bold.

# Phrases

There are two layers of groupings while clustering; The more granular of them is grouping items into phrases. For example, “Your service is very expensive” and “Your service is so expensive”, are very strongly related and can be treated the same, so they are grouped together under the phrase “Your service is very expensive”. These groupings of phrases are then clustered.

Let’s enhance our example to demonstrate phrases. We’ll add two sentences to the previous list of items (new items underlined):

- Your service was great
- _Your service was awesome_
- You helped me a lot
- Can I have a discount?
- Your service is too expensive
- _Your service is very expensive_
- Why can’t your service be cheaper?

Now when we cluster, the engine will first find phrases:

| Phrase                             | Item                               |
| ---------------------------------- | ---------------------------------- |
| Your service was great             | Your service was great             |
|                                    | Your service was awesome           |
| You helped me a lot                | You helped me a lot                |
| Can I have a discount?             | Can I have a discount?             |
| Your service is too expensive      | Your service is too expensive      |
|                                    | Your service is very expensive     |
| Why can’t your service be cheaper? | Why can’t your service be cheaper? |

The original list of 7 items resulted in 5 phrases. Now on that list of phrases, clustering will be done.

| Cluster                       | Phrase                             | Item                               |
| ----------------------------- | ---------------------------------- | ---------------------------------- |
| Your service was great        | Your service was great             | Your service was great             |
|                               |                                    | Your service was awesome           |
|                               | You helped me a lot                | You helped me a lot                |
| Your service is too expensive | Can I have a discount?             | Can I have a discount?             |
|                               | Your service is too expensive      | Your service is too expensive      |
|                               |                                    | Your service is very expensive     |
|                               | Why can’t your service be cheaper? | Why can’t your service be cheaper? |

In this way, from an original list of 7 items, we ended up with 5 phrases and 2 clusters