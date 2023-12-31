# Step-by-Step Process

In this example, we'll dive a bit deeper to show you how this application was made so you can make one of your own.

### Link to the Project

* The repository being referred to can be found [here on GitHub](https://github.com/Boburmirzo/chatgpt-api-python-sales).&#x20;
* If you have a good experience with open source, visiting the above link should enable you to build a similar project seamlessly.&#x20;

### Step-by-Step Process to Build the Application

A good way to understand the code here would be to read the Streamlit (a Snowflake product) blog below which features the open-source application developed by Bobur.&#x20;

It's a friendly and easy-to-understand blog showing how the application interacts with users via an HTTP REST API. It works in real-time, offering support for various data types like JSON Lines and Rainforest Product API.

{% embed url="https://blog.streamlit.io/build-a-real-time-llm-app-without-vector-databases-using-pathway/" fullWidth="false" %}

### Video Tutorial

Once you've read the blog above, check out this video tutorial by Bobur Umurzakov (Developer Advocate at Pathway). He gives a quick walkthrough of the code and the open-source repository.

{% embed url="https://youtu.be/IxdeW_Ndi_8" %}

### Key things to note

* This app is modular; you can add new data sources or interfaces.
* You could scale it up to include more advanced features like additional data formats or APIs.
* Streamlit and Pathway's LLM App communicate over HTTP REST API, but they can also be integrated in other ways, such as file sharing or inter-process communication.

By following this guide, you'll create a versatile application capable of real-time interactions with users, providing them with valuable insights into Amazon discounts.
