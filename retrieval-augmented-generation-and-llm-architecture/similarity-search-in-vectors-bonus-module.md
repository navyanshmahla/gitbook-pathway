# Similarity Search in Vectors (Bonus Module)

We now shift our focus to a more nuanced aspect of natural language processing and machine learning: Similarity Search in Vector Embeddings. The significance of this topic, especially after understanding RAG, cannot be overstated. RAG, with its unique blend of retrieval and generation, underscores the importance of accurately finding and utilizing relevant information from a vast corpus, which is stored as vector indexes. &#x20;

Hence, this principle is closely related to the concept of similarity search in vector embeddings, a cornerstone in understanding and leveraging the full potential of large language models (LLMs). While the upcoming section dives a bit deeper into this topic, it's essential to note that this is a bonus section for a reason. Gaining insights into similarity search and the algorithms in play can enrich your understanding. However, if you're primarily focused on implementing by the end of this course, a detailed grasp isn't mandatory.&#x20;

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



