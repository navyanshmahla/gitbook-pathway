# Using kNN and LSH to Enhance Similarity Search in Vector Embeddings (Bonus Module)

Diving into the intricacies of kNN (k-Nearest-Neighbors) and LSH (Locality Sensitive Hashing), we find ourselves at the intersection of mathematics, data science, and algorithmic strategy.&#x20;

### kNN (k-Nearest-Neighbors) in the Context of Vector Embeddings

If you've been exploring this domain, you might have come across mentions of kNN (k-Nearest-Neighbors). So, what exactly is kNN? Why do we need it, especially when we already have tools like cosine similarity at our disposal? Let's understand.

* **Role of kNN with Vector Embeddings**: Once we have vector representations of data and a measure of similarity like cosine similarity, the next logical step is to leverage these vectors for practical applications. kNN is a powerful algorithm that does just that. Given a query vector, it identifies the 'k' vectors in the dataset that are closest (most similar) to the query.
* **Why kNN?**: kNN hinges on the premise that similar data points in a vector space are likely to share attributes or classifications. For instance, in a text classification problem, if a majority of your 'k' nearest vectors correspond to articles about 'F1 Racing', it's likely that the query article is also related to F1 Racing.
* **The kNN approach has gained success due to** its straightforward nature. The basic version is not only easy to implement but also offers high accuracy. Unlike many alternative methods, kNN isn't a black box and offers **explainability**, meaning its decision-making process is clear and understandable. This transparency enhances user trust in the system, and thus easier adoption within enterprises.

### Challenges with kNN

* **Computational Intensity**: The brute-force approach of kNN, where every query vector is compared with all vectors in the dataset, is computationally expensive.&#x20;
* For example, using Pathway, often developers with large datasets with high-dimensional data. On such datasets, this naive approach doesn't work. As datasets grow, the time taken for these pairwise comparisons becomes a bottleneck. The standard kNN algorithm compares a query vector to every vector in the dataset, which is demanding in terms of computation, especially as the size of the dataset grows. This method's time complexity is $$O(d n_t n_q)$$ where $$d$$ represents the dimensions, and $$n_t$$ and $$n_q$$ are the numbers of training and query points, respectively. This can become very inefficient with large datasets.
* Moreover, managing frequent updates in scenarios with regular data changes is both costly and complex. With new data points coming in, it brings in the requirement for recalculating distances for all queries, which consumes significant resources. In real-time or frequently updated data scenarios, this presents notable challenges. Moreover, modifying or deleting data points necessitates reevaluating all query responses, adding to the complexity.

To overcome this, Pathway uses a better approach.

### Leveraging LSH to Optimize kNN

* **What is LSH?**: LSH (Local Sensitive Hashing) is a hashing technique wherein similar data points are probabilistically mapped to the same bucket. Understandably, unlike hash functions used for security, which scatter similar items widely to prevent predictability, LSH clusters related items together to streamline similarity searches.
* **How LSH Complements kNN**: LSH enhances kNN's effectiveness by grouping vectors based on similarity into the same or adjacent buckets, utilizing hashing functions defined as $$h_{v,b,w}(p) : h_{v,b,w}(p) = \left\lfloor \frac{\mathbf{p} \cdot \mathbf{v} + b}{A} \right\rfloor$$ where $$v$$ is a random chosen vector and b is a random bias $$b$$ is used to offset the vector, and $$A$$ is the bucket width. This method efficiently narrows down the pool of vectors kNN needs to analyze, boosting the overall speed and performance of the search.

If you are keen on diving deeper into the intricacies of how kNN and LSH work together, especially in the context of large-scale datasets, we recommend checking out the below resource by Olivier Ruas on KNN+LSH. It provides a more detailed exploration, complete with visual aids and practical examples.

{% embed url="https://pathway.com/developers/showcases/lsh/lsh_chapter2" %}

### Incremental Indexing in [LLM App](https://github.com/pathwaycom/llm-app)

Building on similarity search, vector embeddings, and RAG, the next piece offers insights into managing vector indexes in dynamic settings, like an e-commerce platform with constantly changing product data.&#x20;

It delves into LSM (Log-Structured Merge-tree) indexes and how Pathway's indexing approach for its RAG Framework – [LLM App](https://github.com/pathwaycom/llm-app) adapts to streaming (live) data, balancing computational efficiency with user needs. The article includes practical scenarios, such as table joins and real-time alerts in Pathway, enhancing your understanding of indexing in fluid data environments.

{% embed url="https://pathway.com/developers/tutorials/indexes/" %}

