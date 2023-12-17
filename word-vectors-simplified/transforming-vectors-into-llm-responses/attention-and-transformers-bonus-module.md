# Attention and Transformers (Bonus Module)

Having understood the sequential nature of RNNs and their limitations, it's time to introduce the game-changer in the world of language processing: Transformers.

* **Breaking the Sequential Barrier:** Unlike RNNs that process words one after another, transformers can look at an entire sentence, or even a paragraph, all at once. This ability to process data in parallel is a major leap forward, significantly speeding up how the model learns and understands language.
* **Efficiency in Learning:** Since transformers don't have to read in sequence, they can be trained on much larger chunks of data at a time. This parallel processing means they can learn from vast amounts of text more efficiently, using powerful hardware to speed things up.

### Foundation of Transformers: Attention Mechanism

At the core of transformers is a technique called the "Attention Mechanism." Initially developed for machine translation, it's now used for various language tasks.

* **How It Works:** Imagine the model as focusing its 'attention' on different parts of a sentence to understand its meaning better. For instance, in the sentence "Taylor is setting new benchmarks with her Eras Tour " the model pays more attention to the word "Taylor" when trying to understand who is doing the action.
* **Different Flavors:** While there are many types of attention mechanisms, transformers use a specific kind called "Scaled Dot-Product Attention." It's a fancy way of saying the model calculates attention based on a mathematical formula, which involves queries, keys, values, and a scaling factor.

### Scaled Dot-Product Attention

The attention mechanism described in the paper [Attention is all you Need](https://arxiv.org/abs/1706.03762) is called _Scaled Dot-Product Attention_, and is defined via the forumula below:

* $$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$&#x20;
* Here, $$Q$$, $$K$$, and $$V$$ represent matrices for queries, keys, and values. How do we get those matrices? We'll understand it soon. But for now, you can know that the formula calculates attention as a weighted sum of values, where the weights are determined by a compatibility function of the query with the corresponding keys.
* **Understanding the Components:**
  * **Queries, Keys, Values:** These are vectors representing different aspects of the input data, that we'll understand now.
  * **Softmax Function:** This part of the formula helps in normalizing the weights, ensuring they sum up to 1.
  * **Scaling Factor:** The $$\sqrt{d_k}$$ term helps in stabilizing the gradients during training, where $${d_k}$$ is the dimension of the key vectors.

### Calculating Q, K, and V

Let's break down the process of calculating Q (Query), K (Key), and V (Value) in the context of a self-attention mechanism in a more digestible way. We'll start from the very beginning with a simple example sentence and go through each step.

#### Step 1: Getting the vector embeddings

* For example, let's take this sentence "Manchester United hopes to perform better."
* Now the first thing we know is that the sentence is split into words or sub-words, known as tokens. So, we get tokens like \["Manchester", "United", "hopes", "to", "perform", "better"]. Each token is then mapped to a unique integer for ease of processing. Here, let's say it's \[0, 1, 2, 3, 4, 5].
* In practice, an embedding matrix is created where each row corresponds to the embedding of a token. The size of this matrix is typically \[vocabulary size x embedding dimension]. For large models like GPT, the vocabulary size is vast, often in the range of tens of thousands, and the embedding dimension can be large as well, such as 768 or more.
* **Note**: Initially, the values in the embedding matrix are randomly initialized. This means that each token is assigned a random vector. During the training phase, these random embeddings are gradually adjusted through [backpropagation](https://youtu.be/IN2XmBhILt4). Backpropagation is a method used to improve neural networks by going backwards through the network to fine-tune how it makes decisions, based on the errors it made. The model learns to change these embeddings to capture semantic meanings and relationships between words.

For example, in our example, we're using random numbers for simplicity. Let's say the embedding dimension is 3. The embeddings for the tokens might look like this after initialization:

* <pre class="language-makefile" data-overflow="wrap"><code class="lang-makefile">Manchester: [ 0.321, -1.024,  0.876]
  United:     [ 1.234,  0.567, -0.890]
  <strong>hopes:    [-0.456,  0.789,  1.234]
  </strong>to: [ 1.111, -0.333,  0.222]
  perform:        [-0.777,  0.888, -0.999]
  better:      [ 0.555, -0.666,  0.777]
  </code></pre>

These numbers are arbitrary and for illustrative purposes only. In a real scenario, these embeddings would be learned and adjusted during the training process of the model.

#### Step 2: Calculate Q, K, V

First, we need to define three distinct weight matrices for calculating Q, K, and V. These matrices are randomly initialized. Here we're using NumPy, a powerful & easy to learn library in Python for numerical computing, especially for operations involving arrays and matrices.

Example Code:

{% code overflow="wrap" %}
```python
w_q = np.random.random((embedding_dim, 3))  # Weight matrix for Q
w_k = np.random.random((embedding_dim, 3))  # Weight matrix for K
w_v = np.random.random((embedding_dim, 3))  # Weight matrix for V
```
{% endcode %}

Each of these weight matrices is then multiplied with the embedding matrix to create Q, K, and V.

Example Code:

{% code overflow="wrap" %}
```python
Q = embeddings @ w_q  # Query
K = embeddings @ w_k  # Keys
V = embeddings @ w_v  # Values
```
{% endcode %}

The outputs of Q, K, and V will be matrices. This operation is a form of linear transformation where each input (embedding) is transformed into three different spaces represented by Q, K, and V. Let's assume our embeddings look like this (using the embeddings from our previous example):

Here's an example of what they might look like:

{% code overflow="wrap" %}
```python
# Sample Output (these values are for illustration and will vary)
print("Query (Q):")
print(Q)
# Output:
# [[ 0.456, -0.789,  1.234],
#  [ 1.111, -0.333,  0.222],
#  ... ]

print("Keys (K):")
print(K)
# Output:
# [[-0.456,  0.789, -1.234],
#  [-1.111,  0.333, -0.222],
#  ... ]

print("Values (V):")
print(V)
# Output:
# [[ 0.123, -0.456,  0.789],
#  [ 0.321, -0.654,  0.987],
#  ... ]
```
{% endcode %}

#### Step 3: Calculate Attention Scores

The attention scores are computed by taking the dot product of the Q and K matrices. This step measures the similarity between each query and key.

* The dot product is divided by the square root of the dimensionality of K, i.e. $$\sqrt{d_k}$$  to keep the gradients stable.
* The softmax function is then applied to convert these scores into a probability distribution.
*   Example Code:

    {% code overflow="wrap" %}
    ```python
    def softmax(x: np.ndarray, axis: int) -> np.ndarray:
        x = np.exp(x - np.amax(x, axis=axis, keepdims=True))
        return x / np.sum(x, axis=axis, keepdims=True)

    scores = Q @ K.T  # Dot product between Q and K
    scores = softmax(scores / np.sqrt(K.shape[1]), axis=1)
    ```
    {% endcode %}
* The resulting scores are a matrix where each element indicates the attention score, representing the relevance of each word in the context of other words in the sentence.

#### Step 4: Applying the Attention Scores to Values

Finally, the attention scores are multiplied with the V matrix. This operation selectively weighs the importance of each value based on the computed attention scores. Example Code:

```python
attention_output = scores @ V
```

The resulting `attention_output` matrix contains the final output of the attention mechanism, where each row represents an aggregated representation of each word, taking into account the context provided by the entire sentence.

This process, starting from the creation of Q, K, and V to the computation of attention scores and their application to V, forms the core of the **self-attention mechanism**, allowing models to dynamically focus on different parts of the input sequence based on the context.

