# How to Run the Examples

Congratulations on coming this far! :tada:

Let's say you want to go beyond the Amazon Discounts App and Dropbox Retrieval App. This module is to make it easy for you to build and run your applications using `examples` on the [LLM App](https://github.com/pathwaycom/llm-app).&#x20;

### What are the Examples offered?

The repository offers multiple possible use cases under its [`examples`](https://github.com/pathwaycom/llm-app/tree/main/examples/pipelines) folder to illustrate various areas of application.

Once you've **cloned the LLM App** repository and set up the **environment variables** (per the steps mentioned on [this link](https://github.com/pathwaycom/llm-app#step-1-clone-the-repository)), you're all set to run the examples.&#x20;

Below is a table that shares the types of examples you can explore.&#x20;



| Example Type      | What It Does                                                                                         | What's Special                                      | Good For                                |
| ----------------- | ---------------------------------------------------------------------------------------------------- | --------------------------------------------------- | --------------------------------------- |
| contextless       | Answers your questions without looking at any additional data.                                       | Simplest example to try. Not RAG based.             | Beginners to get started.               |
| contextful        | Uses extra documents in a folder to help answer questions.                                           | Better answers by using more data.                  | More advanced, detailed answers.        |
| contextful\_s3    | Like "Contextful," but stores documents in S3 (a cloud storage service).                             | Good for handling a lot of data.                    | Businesses or advanced projects.        |
| unstructured      | Reads different types of files like PDFs, Word docs, etc.                                            | Can handle many file formats and unstructured data. | Working with various file types.        |
| local             | Runs everything on your own machine without sending data out.                                        | Keeps your data private.                            | Those concerned about data privacy.     |
| unstructuredtosql | Takes data from different files and puts it in a SQL database. Then it uses SQL to answer questions. | Great for complex queries.                          | Advanced data manipulation and queries. |



### Simple Way to Run the Examples on LLM App

Considering you've done the steps before, here's a recommended, step-by-step process to run the examples easily:

**1 -** Open a terminal and navigate to the LLM App repository folder:

```bash
cd llm-app
```

**2 -** Choose Your Example. The examples are located in the [`examples`](https://github.com/pathwaycom/llm-app/tree/main/examples/pipelines) folder. Say you want to run the 'alert' example. You have two options here:

*   **Option 1**: Run the centralized example runner. This allows you to switch between different examples quickly:\


    <pre class="language-bash"><code class="lang-bash"><strong>python run_examples.py alert
    </strong></code></pre>

***

*   **Option 2**: Navigate to the specific pipeline folder and run the example directly. This option is more focused and best if you know exactly which example you're interested in:\


    ```bash
    python examples/pipelines/contextful/app.py
    ```

That's it! :smile:

By following these steps, you're not just running code but actively engaging with the LLM App’s rich feature set, including anything from real-time data syncing to model monitoring.&#x20;

It's a step closer to implementing your LLM application that can have a meaningful impact.
