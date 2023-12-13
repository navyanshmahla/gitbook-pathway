# Similarity Search in Vectors

While the upcoming section dives a bit deeper into this topic, it's essential to note that this is a bonus section for a reason.&#x20;

Gaining insights into similarity search and the algorithms in play can enrich your understanding. However, if you're primarily focused on implementing by the end of this course, a detailed grasp isn't mandatory. You'll still be able to understand the inner workings and construct a real-time LLM App suitable for production use cases. But for those curious about the underpinnings, this section might be interesting for you.

## Similarity Search in Vector Embeddings

By now you know, vector embeddings allow us to represent complex data, such as words or images, in a way that captures their underlying semantics. One of the critical tasks in many applications, from semantic search to recommendation systems to large language models, is determining the similarity between these vector embeddings.

Three of the most commonly used metrics to measure the similarity between vectors are Euclidean Distance, Dot Product Similarity, and Cosine Similarity. Here's a closer look at each:

### 1. Euclidean Distance

* **Description**: Represents the straight-line distance between two vectors in a multi-dimensional space.
* **Formula**: The Euclidean distance between two vectors, `a` and `b`, is calculated as the square root of the sum of the squared differences between their corresponding components.
* **Considerations**: This metric is sensitive to both the magnitudes and the relative location of vectors in space. It's a natural choice when vectors contain information about counts or measurements. For example, it can be used in recommendation systems to measure the absolute difference between embeddings of item purchase frequencies.

### 2. Dot Product Similarity

* **Description**: Calculates the similarity by adding the products of the vectors' corresponding components.
* **Formula**: The dot product between vectors `a` and `b` is the sum of the product of their corresponding components.
* **Considerations**: This metric considers both the direction and magnitude of vectors. It can be particularly useful in situations where the angle between vectors is of interest, such as in collaborative filtering recommendation systems.

### 3. Cosine Similarity

* **Description**: Measures the cosine of the angle between two vectors, focusing purely on the direction and not on the magnitude.
* **Formula**: The cosine similarity between vectors `a` and `b` is the dot product of the vectors divided by the product of their magnitudes.
* **Considerations**: This metric is not influenced by the magnitude of vectors, making it suitable for tasks like semantic search or document classification, where the direction or angle between vectors is more significant than their length.

**Comparing and Summarizing the three options**

You now have embeddings for any pair of examples.

| Similarity Metric  | Description                                                                                    | Formula                                                                            | Correlation with Similarity                                |
| ------------------ | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Euclidean Distance | Measures the straight-line distance between two points in space represented by vectors         | <p><span class="math">\sqrt{\sum_{i=1}^{n} (a_i - b_i)^2} </span></p><p></p>       | Inversely related (higher distance means lower similarity) |
| Cosine Similarity  | Evaluates the cosine of the angle between two vectors, indicating their orientation similarity | $$\frac{\mathbf{a} \cdot \mathbf{b}}{\|\mathbf{a}\| \|\mathbf{b}\|}$$              | Directly related (higher cosine means higher similarity)   |
| Dot Product        | The product of the magnitudes of two vectors and the cosine of the angle between them          | $$a_1b_1 + a_2b_2 + \ldots + a_nb_n = \|\mathbf{a}\| \|\mathbf{b}\| \cos(\theta)$$ | Directly related and increases with vector magnitudes      |

### See Cosine Similarity Search in Action

{% embed url="https://www.youtube.com/embed/Rg_7JcdZtbg?start=530&end=1195" %}

_(Credits: Microsoft Reactor)_

You should notice and appreciate that cosine similarity has found extensive applications in areas such as **semantic search** and **document classification**. It provides a robust mechanism to gauge the directional similarity of vectors, which translates to comparing the overall essence or content of documents. Imagine trying to find documents or articles that resonate with a given topic or theme; cosine similarity is your tool of choice.

Further, if you've ever used a recommendation system, like those on streaming platforms or e-commerce sites, they might be leveraging cosine similarity. These systems aim to suggest items to users, drawing parallels from their historical behavior and preferences.

However, it's crucial to note that cosine similarity may not always be the best fit. In scenarios where the magnitude or 'size' of vectors carries significance, relying solely on cosine similarity might be misleading. Take, for instance, image embeddings that are formulated based on pixel intensities. Here, merely comparing the direction of vectors might not suffice, and the magnitude becomes critical.

### kNN (k-Nearest-Neighbors) in the Context of Vector Embeddings

Moving further, if you've been exploring this domain, you might have come across mentions of kNN (k-Nearest-Neighbors). So, what exactly is kNN? Why do we need it, especially when we already have tools like cosine similarity at our disposal? Let's understand.

* **Role of kNN with Vector Embeddings**: Once we have vector representations of data and a measure of similarity like cosine similarity, the next logical step is to leverage these vectors for practical applications. kNN is a powerful algorithm that does just that. Given a query vector, it identifies the 'k' vectors in the dataset that are closest (most similar) to the query.
* **Why kNN?**: The core principle behind kNN is the assumption that similar vectors (or data points) tend to have similar properties or belong to similar classes. For instance, in a text classification problem, if a majority of your 'k' nearest vectors correspond to articles about 'technology', it's likely that the query article is also related to 'technology'.
* **The kNN approach has gained success** due to its straightforward nature. The basic version is not only easy to implement but also offers high accuracy. Unlike many alternative methods, kNN isn't a black box and offers **explainability**, meaning its decision-making process is clear and understandable. This transparency enhances user trust in the system, and thus easier adoption within enterprises.

### Challenges with kNN

* **Computational Intensity**: The brute-force approach of kNN, where every query vector is compared with all vectors in the dataset, is computationally expensive.&#x20;
* For example, at Pathway, we work with large datasets with high-dimensional data. On such datasets, this naive approach doesn't work. As datasets grow, the time taken for these pairwise comparisons becomes a bottleneck.
* Moreover, managing frequent updates in scenarios with regular data changes is both costly and complex. Introducing new data points requires recalculating distances for all queries, consuming significant resources. In real-time or frequently updated data scenarios, this presents notable challenges. Moreover, modifying or deleting data points necessitates reevaluating all query responses, adding to the complexity.

### Introducing LSH (Local Sensitive Hashing) to Optimize kNN

* **What is LSH?**: LSH is a hashing technique wherein similar data points are probabilistically mapped to the same bucket. By doing so, we don't need to compare our query vector with the entire dataset but only with vectors in the relevant buckets.
* **How LSH Complements kNN**: Instead of comparing the query vector with every other vector in the dataset, we can use LSH to quickly identify a subset of vectors that are likely to be similar. We then perform kNN on this subset, making the entire process much more efficient.
* **LSH with Cosine Similarity**: While LSH can be designed for various distance metrics, for cosine similarity, specific LSH methods ensure that vectors that are close in terms of their cosine similarity end up in the same or nearby buckets. This allows us to speed up similarity-based searches in high-dimensional spaces effectively.

For those keen on diving deeper into the intricacies of how kNN and LSH work together, especially in the context of large-scale datasets, we recommend checking out this [comprehensive resource by Olivier Ruas on KNN+LSH](https://pathway.com/developers/showcases/lsh/lsh\_chapter2). It provides a more detailed exploration, complete with visual aids and practical examples.



