# What is Retrieval Augmented Generation (RAG)?

Large Language Models (LLMs) like GPT-4 or Mistral-7b are extraordinary in many ways, yet they come with a set of challenges—something we've summarized toward the end of this module. For now, let's focus on one specific limitation: the timeliness of their data. Since these models are trained up to a particular cut-off date, they aren't well-suited for real-time or organization-specific information.

<figure><img src="../.gitbook/assets/chatgpt outdated.png" alt=""><figcaption></figcaption></figure>

Imagine you're a developer architecting an LLM-enabled app for Amazon. You're aiming to support shoppers as they comb through Amazon for the latest deals on sneakers. Naturally, you want to furnish them with the most current offers available. After all, nobody wants to rely on outdated information, and the same holds true for data queried from your LLM.

This is where Retrieval-Augmented Generation, commonly known as RAG, significantly improves the capabilities of LLMs.&#x20;

In a way that might resemble a resourceful friend in an exam setting or during a speech who—figuratively speaking, of course—swiftly passes you **the most relevant** "cue card" out of a ton of information to help you understand what you should be writing or saying next.&#x20;

<figure><img src="../.gitbook/assets/maxresdefault-min.jpeg" alt=""><figcaption><p><mark style="color:blue;"><strong>Alright, perhaps that wasn't the perfect example, but you get the point.</strong></mark> <span data-gb-custom-inline data-tag="emoji" data-code="1f604">😄</span></p></figcaption></figure>

With RAG, efficient retrieval of the most relevant data for your use case ensures the text generated is both current and substantiated. RAG operates through a three-fold process:

* **Retrieval:** It sources pertinent information.&#x20;
* **Augmentation:** This information is then added to the model's initial input.&#x20;
* **Generation:** Finally, the LLM utilizes this augmented input to create an informed output.&#x20;

To put it simply, RAG empowers LLMs to include real-time, reliable data from external databases in their generated text.&#x20;

For a video explanation, check out this video by IBM Research

{% embed url="https://youtu.be/T-D1OfcDW1M" %}

_(Credits: IBM Technology)_

Knowing about RAG is essential, particularly if you're considering implementing Enterprise LLM Architecture for your organization or even a personal project. The efficacy of this architecture depends largely on the strength and utility of RAG.&#x20;

By now, you should have a basic understanding of RAG and its importance. As we progress through this module, our aim is for you to gain a comprehensive grasp of how in-context learning and RAG collectively contribute to making LLMs more effective, current, and enterprise-ready.

\
