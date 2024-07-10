---
layout: post
title: "5x'ing our recommendation speed with Embeddings"
---

When you're looking to categorize, search, or recommend relevant content embeddings are incredibly powerful.

Here I use the OpenAI embeddings API to get a 5x speed increase in our template recommender feature.

### Where we started

Users would provide a page title they wanted to use for their new process. We returned to the user a list of relevant example templates based on that page title. 

Previously, we provided the title of a new page and all of our template titles to GPT.  We then asked it to return a JSON formatted list of similar templates.

For example, with the suggested title  “How to call a customer” we get back the following:

```
[
  { name: 'Run a discovery call', relevance: 4 },
  { name: 'Learn how to run discovery calls', relevance: 5 },
  { name: 'Learn how to handle an objection', relevance: 3 }
]
```

These are the names of some of our pre-built templates.

However, this process was too slow.  The average benchmarked speed was ~5500 milliseconds, where the user would have to wait to receive their recommendations.

### Introducing embeddings

Word embeddings reduce phrases down to 2d coordinate points. The smaller the distance between two coordinates, the more similar the phrases.

![The Ultimate Guide to Word Embeddings](https://i0.wp.com/neptune.ai/wp-content/uploads/2022/10/Word-embeddings-model.png?ssl=1)

After pre-calculating and storing the similarity for all our page templates, the code to get similar templates starts to look real simple:

```
async function getEmbeddings ({title, itemId}, context) {
  const openAIApi = await getOpenAIApi(context);

  // Pre-calculated embeddings for the titles of each template
  const templateEmbeddings = getTemplateEmbeddings()

  // The embedding for the user suggested page title
  const titleEmbedding = await openAIApi.createEmbedding({
    model: 'text-embedding-ada-002',
    input: title,
  });

   // Calculate similarity with a geometric equation,
   // usually cosine similarity
  const embeddingsWithSimilarities = embeddings.map(...);

  return embeddingsWithSimilarities
}
```
<br>
### The final result

Now averaging <1000ms response times, our template recommender is a viable feature.

If you're looking to handle recommendations, I highly suggest you take a look into Embeddings. If they fit your use case they can be a complete game-changer!

<div style="position: relative; padding-bottom: 62.7177700348432%; height: 0;"><iframe src="https://www.loom.com/embed/f5958b73b8e04bddaffe6d1326e86979?sid=b7cd4c0e-1b9b-419a-944e-056167b90e63" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>
