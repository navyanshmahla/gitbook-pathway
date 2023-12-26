# Transforming Vectors into LLM Responses

Alright, you've got a handle on word vectors and the role of context. Before we delve into the comprehensive pipelines that make Large Language Models (LLMs) function, it's crucial to understand the roles of tokenisers and detokenisers.

Think of a tokenizer as a "sentence chopper." It breaks down a sentence into smaller parts, like words, characters, subwords, or symbols, which the model can understand. This generally depends on the type and the size of the model. Detokenizers do the reverse; they take the LLM's output and stitch it back into sentences we can understand. This process is a foundational step for LLMs to translate human queries into actionable tasks.

### Up Next: Explainer by Mike Chambers from AWS

To give you a more concrete understanding, our next resource is an insightful video by Mike Chambers. This video demystifies what happens when you send a ‘prompt’ (or an input text) to an LLM.&#x20;

Though the internal mathematics may be intricate, the overall goal is straightforward: word prediction. The video will guide you through how your prompts are processed to generate coherent text responses. This will set the stage for our subsequent discussions on Prompt Engineering and LLM pipelines, offering a cohesive picture of how these models operate.

{% embed url="https://www.youtube.com/watch?v=ibr5wmtinG0" %}

_(Credits: Build on AWS)_

Here you see how a Large Language Model’s job is to predict the next word based on the context.&#x20;

Now that you understand the role of "context," you might want to grasp some concepts to appreciate how these models work at a granular level. Given the timelines of this course, while foundational for a better understanding of LLMs, these concepts are tagged as Bonus Resources.&#x20;

* **Attention in Large Language Models:** Imagine being in a room where multiple conversations are happening. Your ability to focus on one conversation over the others is similar to how Attention works in neural networks. It allows the model to 'focus' on relevant parts of the input for tasks.&#x20;
* **Encoder-Decoder Architecture:** An encoder translates the input (e.g., a sentence) into a fixed-size context vector. The decoder takes this context vector to generate an output sequence (e.g., a translated sentence). When the attention mechanism is in action,  it guides the Decoder to focus on certain parts of the Encoder’s output, enhancing the translation or text generation task. The concept of Attention complements the Encoder-Decoder architecture, making it more effective and efficient. This architecture is a building block for LLMs such as GPT-3.5.&#x20;

### Bonus Links

If you're interested in delving further into the details, you may find the following links on embeddings, attention mechanisms, and encoder-decoder architecture beneficial. A foundational understanding of neural networks, backpropagation, the softmax function, and cross-entropy will enhance your comprehension of these resources. These topics are not the primary focus of this course, so they're provided as bonus links.

* **Understanding Transformers:** Check the Bonus Module Right Ahead.
* [Attention mechanism: Overview](https://youtu.be/fjJOgb-E41w?t=18) | Short Video by Google Cloud
* [Word2Vec and Word Embeddings](https://youtu.be/viZrOnJclY0) | Video by StatQuest
* [Seq2Seq Encoder-Decoder Neural Networks](https://youtu.be/L8HKweZIOmg) | Video by StatQuest
* [Attention is all you need](https://arxiv.org/abs/1706.03762) | Read the Paper on ArXiv
* [Attention is all you need](https://youtu.be/XfpMkf4rD6E?t=1211) | Watch the seminar by Stanford Online
