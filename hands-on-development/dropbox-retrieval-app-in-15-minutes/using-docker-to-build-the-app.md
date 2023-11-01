# Using Docker to Build the App

To get started, ensure that you have Dropbox installed on your machine, as it is an obvious prerequisite for using this tool.

### Step 1: Cloning the Repository

Open your terminal and run:

{% code overflow="wrap" %}
```bash
git clone https://github.com/pathway-labs/dropbox-ai-chat 
cd dropbox-ai-chat
```
{% endcode %}

**What it does**: Downloads your project from GitHub to your local machine.&#x20;

### Step 2: Setting the Environment Variables

This configures essential environment variables needed for your application to function correctly.

**For macOS and Linux:**

1.  Create an `.env` file in the project's root directory using `touch`.

    ```bash
    touch .env
    ```
2.  Edit the `.env` file using a text editor like `nano` or `vim`.

    ```bash
    nano .env
    ```
3.  Populate the `.env` file with the following content, replacing placeholders with actual values:\
    \
    **Note**: Please make sure to replace the {OPENAI\_API\_KEY} and {REPLACE\_WITH\_DROPBOX\_RELATIVE\_PATH} with your openai api key as well as your dropbox local path respectively.

    {% code overflow="wrap" %}
    ```plaintext
    OPENAI_API_TOKEN={OPENAI_API_KEY}
    EMBEDDER_LOCATOR=text-embedding-ada-002
    EMBEDDING_DIMENSION=1536
    MODEL_LOCATOR=gpt-3.5-turbo
    MAX_TOKENS=200
    TEMPERATURE=0.0
    PATH_TO_DROPBOX={REPLACE_WITH_DROPBOX_RELATIVE_PATH}
    ```
    {% endcode %}
4.  **Alternative using `export`**: If `.env` doesn't work, you can set these variables directly in your shell:

    <pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><strong>export OPENAI_API_TOKEN={OPENAI_API_KEY}
    </strong>export EMBEDDER_LOCATOR=text-embedding-ada-002
    export EMBEDDING_DIMENSION=1536
    export MODEL_LOCATOR=gpt-3.5-turbo
    export MAX_TOKENS=200
    export TEMPERATURE=0.0
    export PATH_TO_DROPBOX={REPLACE_WITH_DROPBOX_RELATIVE_PATH}
    </code></pre>

**For Windows:**

1. Create an `.env` file using a text editor of your choice.
2. Populate the `.env` file as shown above.
3.  **Alternative**: Use the `set` command in Command Prompt to set environment variables.

    {% code overflow="wrap" %}
    ```cmd
    set OPENAI_API_TOKEN={OPENAI_API_KEY}
    set EMBEDDER_LOCATOR=text-embedding-ada-002
    set EMBEDDING_DIMENSION=1536
    set MODEL_LOCATOR=gpt-3.5-turbo
    set MAX_TOKENS=200
    set TEMPERATURE=0.0
    set PATH_TO_DROPBOX={REPLACE_WITH_DROPBOX_RELATIVE_PATH}
    ```
    {% endcode %}

### Step 3: Building and Starting Containers

Now we will build the Docker image and start the containers. Navigate to the cloned directory (dropbox-ai-chat). Then run these commands.

```bash
docker-compose build 
docker-compose up
```

### Step 4: Accessing Applications

**What it does**: Opens access to your API and Streamlit UI.

* **Access Points**:
  * API: `http://localhost:8080/`
  * Streamlit UI: `http://localhost:8501/`

### Step 5: Stopping Containers

To stop the services and remove the containers, execute:

```bash
docker-compose down
```

By following these steps, you should be able to get both the main application and the Streamlit UI up and running using Docker Compose.

Interestingly if you quickly revisit the [LLM Architecture diagram](https://ai-community-iitb-organization.gitbook.io/10-days-llm-bootcamp/retrieval-augmented-generation-and-llm-architecture/llm-architecture-diagram-and-various-steps) we saw earlier, there was a prompt from a Customer Support Executive trying to understand the product release notes made by the development team. With something like the Dropbox app, that problem can be easily addressed.&#x20;

Now let's look at another example where we use an API as a data source.

