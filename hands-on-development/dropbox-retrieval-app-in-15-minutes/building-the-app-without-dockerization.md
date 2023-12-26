# Building the app without Dockerization

Here, you can explore a video tutorial by Richard Pelgrim, a Developer Advocate in the stream data processing space, demonstrating how they harnessed the Dropbox document sync application to create a RAG app.&#x20;

**Link to the Project**

* The repository being referred to can be found here **-** [**https://github.com/pathway-labs/dropbox-ai-chat**](https://github.com/pathway-labs/dropbox-ai-chat)**.** Make sure to star it. :star:
* If you struggle to build the application with the help of README on the GitHub repo above, the video and the description below should help you.&#x20;

Navigating the maze of new regulations, like the EU AI Act, can be a complex challenge for founders and data practitioners. This app which leverages the Dropbox example, aims to make understanding these regulations more straightforward. Imagine a tool that helps you dissect and comprehend these intricate policies, easing compliance and being informed.&#x20;

As you explore this application, think of the diverse scenarios you can open just with the Dropbox AI Chat example that we're seeing here.

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

Create a `.env` file in the root directory and populate it with your configurations. Make sure to replace `{OPENAI_API_KEY}` it with your actual OpenAI API key.

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

Make sure to replace **DROPBOX\_LOCAL\_FOLDER\_PATH** with your local Dropbox folder path; optionally, you can customize other values.

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

If you look closely at the repo and visit [`api.py`](https://github.com/pathway-labs/dropbox-ai-chat/blob/main/api.py) , you'll be able to connect the dots from what we've learned. Here:

* The prompt is processed as embeddings and used as embedded\_query.
* The data we're getting from our data source, (i.e., Dropbox) is converted into smaller chunks with the help of Pathway (pw) and then converted to embeddings and stored in index.&#x20;
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

Following these steps, you can get the Dropbox AI Chat tool up and running.

However, suppose you're **facing issues** downloading the dependencies or running the application **on your machine**. In that case, it might be worthwhile to check the next module, which provides a comprehensive guide for implementing this through Docker.



