# How the Project Works

The project accomplishes its tasks through a series of steps shared below. Make sure you give it a quick read before proceeding to the next step where we explore the repository.

**1 - Realtime Indexing:**

* Sourcing data: A script called [`discounts-data-generator.py`](https://github.com/Boburmirzo/chatgpt-api-python-sales/blob/main/examples/csv/discounts-data-generator.py) mimics real-time data from external sources. It creates or updates a file named `discounts.csv` with random data. Alongside this, a scheduled task (cron job) using [Python Crontab](https://pypi.org/project/python-crontab/) runs every minute to fetch the latest data from Rainforest API. Crontab is a time-based job scheduler.
* Giving the option to choose particular data source(s): With the Streamlit UI provided,  either select Rainforest API as a data source or upload a CSV through the UI file-uploader. It then maps each row into a JSONline schema for better managing large data sets. This format helps in managing large datasets by representing each row as a separate JSON object
* Chunking: The documents are divided into shorter sections for them to be converted into vector embeddings.
* Embedding of data source: These shorter sections are processed through the OpenAI API to generate embeddings.
* Real-time Vector Indexing: An index is created based on these embeddings to facilitate quick searching later on.

**2 - Query (Prompt) Embedding and Retrieval**

* Query Embeddinging: For any question asked by the user, an embedding is generated using the OpenAI API for embeddings, i.e. `text-embedding-ada-002`.
* Retrieving: The system compares the vector embedding of the query/prompt and the vector embedding of the data source to find the most relevant information.

**3 - Prompt Augmentation and Answer Generation**

1. The query/prompt and the most relevant sections of data are packaged into a message within the token limit.
2. Get Answer from GPT: This message is sent to  `gpt-3.5-turbo`, which then provides an answer.

