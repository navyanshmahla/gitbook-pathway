# Best Practices to Follow in Prompt Engineering

Mastering the art of designing a prompt comes with practice, and it can significantly improve your interactions with Large Language Models (LLMs).&#x20;

It's crucial to note that the best practices discussed here are primarily geared towards generating language-based outputs. For more specialized tasks, such as generating code, images, or other types of non-textual data, it's advisable to consult the specific guidelines and documentation related to those tasks.

Let's delve into some best practices that could act as your guiding principles.

### Basic Prompts: The Starting Point

* **Be Concise**&#x20;

Avoid verbosity for succinct and effective prompts.

❌ "What do you think could be a good name for a flower shop that specializes in selling bouquets of dried flowers?"

✅ "Suggest a name for a flower shop that sells bouquets of dried flowers."

* **Be Specific**&#x20;

Narrow your instructions to get the most accurate response.

❌ "Tell me about Earth"

✅ "Generate a list of ways that makes Earth unique compared to other planets."

* **Prompt Structuring**

Ask One Task at a Time: Avoid combining multiple tasks in one prompt.

❌ "What's the best method of boiling water and why is the sky blue?"

✅ "What's the best method of boiling water?"

* **Detailing**: Specify context, outcome, format, length, etc.
* **Example-Driven**: Utilize examples to guide the output.

### Zero-Shot vs. Few-Shot Prompts

When you give more examples to the model, it gets better at understanding what you're asking. This helps it give answers that are more on-point or accurate.

**Zero-Shot Prompting:**

* You ask the model to do something without giving any examples.
* Example:&#x20;

&#x20;    "Is a goldfish a pet or not a pet?"

&#x20;    Output: "Pet"



**One-Shot Prompting:**

* You give the model one example to help it understand your question.
* Example:

&#x20;     "For instance, a dog is a pet. Now, is a goldfish a pet or not a pet?"

&#x20;     Output: "Pet"



**Few-Shot Prompting:**

* You give the model several examples to ensure it understands your question.
* Example:

&#x20;     "A dog is a pet."

&#x20;     "A lion is not a pet."

&#x20;     Now, "Is a goldfish a pet or not a pet?"

&#x20;     Output: "Pet"



In this example, all prompting types resulted in the same answer: "Pet". However, with few-shot prompting, you can be more confident that the model truly understands what you mean by "pet" since it has more examples to learn from. Usually, giving more examples (few shots) helps the model give better answers, especially for more complicated questions.

Thumb rule, Zero-shot, one-shot, and few-shot prompting have distinct advantages and challenges. Zero-shot is more open-ended while few-shot is more controlled.

### Elements of a Prompt: Know the Ingredients

* Instruction: What task do you want the model to perform?
* Context: Additional information that can steer the model.
* Input Data: The question or data of interest.
* Output Indicator: Desired format or type of the output.

You don't always need all these elements; it depends on your needs.

### General Tips: The Do's and Don'ts

* Start Simple: Initial iterations should be straightforward, and you can build complexity as you refine your prompts.&#x20;
* Avoid Redundancy: Use concise, non-redundant language.
* Be Specific: Vague instructions often yield vague results.
* Avoid Negative Instructions: Instead of saying what not to do, focus on what the model should do.

### Bonus Resources:

Curious to learn more? Once you’ve completed this course, you might want to check these resources that will help you dive deeper into the nuances of prompt engineering:

* [LearnPrompting's Comprehensive Guide](https://learnprompting.org/docs/intro)
* [Official Docs by OpenAI](https://platform.openai.com/docs/guides/gpt-best-practices)
* [Concise Article by OpenAI](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api)

Take your time to experiment and iterate, as mastery comes with practice and refinement. And remember, this is a living, evolving field; staying updated with best practices is key to success.
