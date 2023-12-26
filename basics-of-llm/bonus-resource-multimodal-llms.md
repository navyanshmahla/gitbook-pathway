# Bonus Resource: Multimodal LLMs

At this point, you're likely familiar with large language models (LLMs) and generative AI. Now, let's delve into the exciting world of Google Gemini via this short explainer by Mudit Srivastava. :smile:

Google Deepmind introduced Gemini in December 2023, showcasing its potential to revolutionize the capabilities of LLMs. This launch, however, didn't come without its [share of critique](https://www.cnbc.com/2023/12/08/google-faces-controversy-over-edited-gemini-ai-demo-video.html), especially regarding Google's approach to refining Gemini's initial release for a more polished presentation. This practice, quite prevalent among developers and innovators, often stirs up a vital discussion on ethics. But setting that aside, one thing is clear: Google's video offers an intriguing peek into the possibilities of multimodal LLMs. It's an exciting hint at what the future holds for enthusiasts like us in the world of generative AI. Let's dive into the video and see what's in store!

{% embed url="https://youtu.be/UIZAiXYceBI" %}

DeepMind's release comprised three models: Gemini Pro, which matches the abilities of GPT-3.5, and the more advanced Gemini Ultra, surpassing GPT-4. The Nano versions, optimized for mobile use, add an extra layer of innovation.&#x20;

* Interested in their applications for Android? [Explore here](https://android-developers.googleblog.com/2023/12/leverage-generative-ai-in-your-android-apps.html).&#x20;
* And for those of you who are developers, the Gemini API is now accessible on Kaggle. Explore [it here](https://www.kaggle.com/models/google/gemini-api).&#x20;

But have you ever wondered what sets multimodal LLMs apart? Unlike the conventional text-only models, these models are unique in their ability to process diverse data types. Let's dive into this intriguing world!

### What are Multimodal Models?&#x20;

Envision an AI that perceives the world not only through text but also through visuals, audio, and beyond. This is the essence of multimodal models. A notable illustration is found in Google DeepMind's research on Google Gemini.

In this example, Gemini showcases its capability for inverse graphics, where it deduces the underlying code that could have produced specific plots. This process involves reconstructing the visual elements into code and applying necessary mathematical transformations to generate the corresponding code accurately.

<figure><img src="../.gitbook/assets/Untitled design-8.png" alt=""><figcaption></figcaption></figure>

### Exploring various data modalities

This section draws upon the valuable insights from an informative [write-up on MLLMs by Chip Huyen](https://huyenchip.com/2023/10/10/multimodal.html). In Multimodal Large Language Models (MLLMs), we explore the fascinating world where different data types are translated and interchanged, opening up a realm of possibilities. Let's take a closer look:

* **Audio as Visuals:** Imagine audio waves transformed into visual spectrums like mel spectrograms. This conversion offers a new perspective, making audio data visually interpretable.
* **Speech into Text:** When we transcribe speech, we're capturing words but also losing out on nuances like the speaker's tone, volume, and pauses. It's a trade-off between capturing the literal and missing the emotional cues.
* **Images in Textual Form:** Here's where it gets interesting. An image, in essence, can be broken down into a vector format and then represented as a sequence of text tokens. It's like translating a visual story into a textual narrative.
* **Videos – Beyond Moving Images:** While it's common to see videos as sequences of images, this overlooks the rich layer of audio that accompanies them. Remember, in platforms like TikTok, sound is not just an add-on; it's a vital part of the experience for most users.
* **Text as Images:** Something as simple as photographing text turns it into an image. This is a straightforward but effective way of changing data modalities.
* **Data Tables to Visual Charts:** Converting tabular data into charts or graphs transforms dry numbers into engaging visuals, enhancing understanding and insight.

Beyond these, think about the potential of other data types. The possibilities would be endless if we could effectively teach models to learn from bitstrings, the foundational elements of digital data. Imagine a model that could seamlessly learn from any data type!

What about data types like graphs, 3D assets, or even sensory data like smell and touch (haptics)? While we haven't delved deeply into these areas yet, the future of MLLMs in these uncharted territories is both exciting and promising!

### Bonus Resource: Recommended if you're already aware of the Encoder-Decoder Architecture

To delve deeper into the workings of Google Gemini, it's essential to understand its architecture, rooted in the encoder-decoder model. Though not elaborated in detail in their publications so far, Gemini's design appears to draw from DeepMind's Flamingo, which features separate text and vision encoders.

<figure><img src="../.gitbook/assets/multimodal llm.png" alt=""><figcaption><p>Source: Gemini Team, Google (2023). Gemini: A Family of Highly Capable Multimodal Models</p></figcaption></figure>



Following our [module on Transformers](../word-vectors-simplified/transforming-vectors-into-llm-responses.md) in this bootcamp, we've also included a Bonus Resource – a live session on Pathway led by Dr Vijay Srinivas Agneeswaran (Sr. Director, ML Research at Microsoft). This session is ideal for those interested in delving deeper into the role of computer vision in LLMs and exploring Microsoft's advancements in vision transformers.

### Papers for Further Reading

* [Wu, S., Fei, H., Qu, L., Ji, W., & Chua, T.-S. (2023). NExT-GPT: Any-to-Any Multimodal LLM. NExT++, School of Computing, National University of Singapore](https://arxiv.org/abs/2309.05519)
* [Gemini Team. (2023). Gemini: A Family of Highly Capable Multimodal Models. Google](https://assets.bwbx.io/documents/users/iqjWHBFdfxIU/r7G7RrtT6rnM/v0)
* [Yin, S., Fu, C., Zhao, S., Li, K., Sun, X., Xu, T., & Chen, E. (2023). A Survey on Multimodal Large Language Models. USTC & Tencent YouTu Lab](https://arxiv.org/abs/2306.13549)

