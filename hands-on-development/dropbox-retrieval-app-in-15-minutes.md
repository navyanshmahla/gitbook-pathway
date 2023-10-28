# Dropbox Retrieval App in 15 Minutes

Let's dive into the setup and operation of the Dropbox AI Chat tool, an innovative solution enabling you to efficiently search through extensive, unstructured documents stored in your Dropbox using advanced AI capabilities.&#x20;

What you'll be building can be seen below. In this particular showcase we'll be cloning [this particular repository](https://github.com/pathway-labs/dropbox-ai-chat) to enable you to quickly build a similar application.&#x20;

<figure><img src="../.gitbook/assets/dropbox-ai-search-tool.gif" alt=""><figcaption></figcaption></figure>

To get started, ensure that you have Dropbox installed on your machine, as it is an obvious prerequisite for using this tool.

Next, you can explore a video tutorial by Richard Pelgrim, a Developer Advocate in the stream data processing space, demonstrating how they harnessed the Dropbox document sync application to create an RAG app.&#x20;

### Link to the Project

* The repository being referred to, can be found here **-** [**https://github.com/pathway-labs/dropbox-ai-chat**](https://github.com/pathway-labs/dropbox-ai-chat)**.** Make sure to star it. :star:
* If you struggle to build the application with the help of README on the GitHub repo above, the video and the description below should help you with it.&#x20;

This app proves invaluable in simplifying the comprehension of the recently released EU AI Act. Feel free to let your creative juices flow to imagine possibilities that you can open with such an application.

{% embed url="https://youtu.be/PbSAYHi5gnM" %}

Let's analyze a few elements from this video.

### Step 1: Cloning the Repository

{% code overflow="wrap" %}
```bash
git clone https://github.com/pathway-labs/dropbox-ai-chat 
cd dropbox-ai-chat
```
{% endcode %}

### Step 2: Setting up Environment Variables

Create a `.env` file in the root directory and populate it with your configurations. Make sure to replace `{OPENAI_API_KEY}` with your actual OpenAI API key.

```markdown
OPENAI_API_TOKEN={OPENAI_API_KEY}
HOST=0.0.0.0
PORT=8080
EMBEDDER_LOCATOR=text-embedding-ada-002
EMBEDDING_DIMENSION=1536
MODEL_LOCATOR=gpt-3.5-turbo
MAX_TOKENS=200
TEMPERATURE=0.0
DROPBOX_LOCAL_FOLDER_PATH="../../../mnt/c/Users/bumur/Dropbox/documents"
```

Make sure to replace **DROPBOX\_LOCAL\_FOLDER\_PATH** with your local Dropbox folder path and optionally, you customize other values.

### Step 3 - Optional: Creating a Virtual Environment

In this case, Richard has used Conda so it's not necessary.\
To create an isolated environment, execute:

{% code overflow="wrap" %}
```python
# Setting Up a Virtual Environment

# On macOS and Linux:
# Create and activate a virtual environment
python -m venv pw-env && source pw-env/bin/activate

# On Windows:
# Step 1: Create a new virtual environment in a folder named 'pw-env'
python -m venv pw-env

# Step 2: Activate the virtual environment
pw-env\Scripts\activate

```
{% endcode %}

### Step 4 - Installing the Dependencies

```python
pip install --upgrade -r requirements.txt
```

### Step 5 - Running the App

Navigate to the root directory and execute `main.py`.

```bash
python main.py
```

### Step 6 - Launching UI with Streamlit

Run the Streamlit app using the following command:

```python
streamlit run ui.py
```

Access the UI at `http://localhost:8501/` on your browser.

With this, your app should be up and running. :smile:

### Connecting the Dots

If you look closely at the repo and visit [`api.py`](https://github.com/pathway-labs/dropbox-ai-chat/blob/main/api.py) , you'll be able to connect the dots from what we've learned so far. Here:

* The prompt is processed as embeddings and used as embedded\_query.
* The data we're getting from our data source, (i.e. Dropbox) is converted into smaller chunks with the help of Pathway (pw) and then converted to embeddings and stored in index.&#x20;
* Using these, we're creating the augmented prompt with the help of retrieved information and feeding that into GPT-3.5 turbo.&#x20;

{% code overflow="wrap" %}
```python
# Real-time data coming from external unstructured data sources like a PDF file
input_data = pw.io.fs.read(
    dropbox_folder_path,
    mode="streaming",
    format="binary",
    autocommit_duration_ms=50,
)

# Chunk input data into smaller documents
documents = input_data.select(texts=extract_texts(pw.this.data))
documents = documents.select(chunks=chunk_texts(pw.this.texts))
documents = documents.flatten(pw.this.chunks).rename_columns(chunk=pw.this.chunks)

# Compute embeddings for each document using the OpenAI Embeddings API
embedded_data = embeddings(context=documents, data_to_embed=pw.this.chunk)

# Construct an index on the generated embeddings in real-time
index = index_embeddings(embedded_data)

# Generate embeddings for the query from the OpenAI Embeddings API
embedded_query = embeddings(context=query, data_to_embed=pw.this.query)

# Build prompt using indexed data
responses = prompt(index, embedded_query, pw.this.query)

# Feed the prompt to ChatGPT and obtain the generated answer.
response_writer(responses)

# Run the pipeline
pw.run()
```
{% endcode %}

By following these steps, you should be able to get the Dropbox AI Chat tool up and running.&#x20;

Interestingly if you quickly revisit the [LLM Architecture diagram](https://ai-community-iitb-organization.gitbook.io/10-days-llm-bootcamp/retrieval-augmented-generation-and-llm-architecture/llm-architecture-diagram-and-various-steps) we saw earlier, there was a prompt from a Customer Support Executive trying to understand the product release notes made by the development team.&#x20;

With something like the Dropbox app, that problem can be easily addressed. Now let's look at another example where we use an API as a data source.