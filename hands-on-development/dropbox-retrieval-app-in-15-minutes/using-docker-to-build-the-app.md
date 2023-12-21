# Using Docker to Build the App

Welcome to this module on how to use **Docker** to set up and run the Dropbox AI Chat application. Before we begin, it's essential to ensure that you meet the prerequisites and understand each step thoroughly.

**Basic Prerequisites:**

* Ensure you have **Docker** installed on your machine.
* **Dropbox** must also be installed.

### Step 1: Cloning the Repository

Open your terminal and run:

{% code overflow="wrap" %}
```bash
git clone https://github.com/pathway-labs/dropbox-ai-chat 
cd dropbox-ai-chat
```
{% endcode %}

If you have previously cloned an older version of the repository, ensure you're in the correct repository directory and update it using:

```bash
git pull https://github.com/pathway-labs/dropbox-ai-chat
```

**What this does:**The git pull command will update your local repository with the latest changes from the remote repository.

### Step 2: Setting the Environment Variables

\
**Overview**:

* The `.env` file sets crucial environment variables for your application.&#x20;
* If you're using macOS, the `.env` file might be hidden by default when viewed through Finder but is visible via Terminal. This being said, regardless of the OS, it's important to note that this file plays a pivotal role.
* The primary change you'll make in this entire implementation is to the `{PATH_TO_DROPBOX}` variable, which the  `.env` file uses.

**Understanding `DROPBOX_LOCAL_FOLDER_PATH`** **variable used here:**

* This variable defines the **relative path** from your project to your Dropbox folder.
* If you want to quickly understand how relative path works in the context of Linux, you can check this quick [video by Udacity](https://youtu.be/ephId3mYu9o) or read these comprehensive explanations by [RedHat](https://www.redhat.com/sysadmin/linux-path-absolute-relative) or [Coding Rooms](https://www.codingrooms.com/blog/file-paths).&#x20;

**Setting the environment variables in MacOS or Linux**

1.  Create an `.env` file in the project's root directory using `touch`.

    ```bash
    touch .env
    ```
2.  Edit the `.env` file using a text editor like `nano` or `vim`.

    ```bash
    nano .env
    ```
3. Populate the `.env` file with the following content, replacing placeholders with actual values:\
   \
   **Note:** Replace the following while using the environment variables from below:&#x20;
   1. &#x20;`{OPENAI_API_KEY}` with your OpenAI API key. You can get from [here](https://platform.openai.com/account/api-keys) once you've logged in)&#x20;
   2.  `{REPLACE_WITH_DROPBOX_RELATIVE_PATH}` with the relative path where Dropbox folder is located\


       ```
       OPENAI_API_TOKEN={OPENAI_API_KEY}
       EMBEDDER_LOCATOR=text-embedding-ada-002
       EMBEDDING_DIMENSION=1536
       MODEL_LOCATOR=gpt-3.5-turbo
       MAX_TOKENS=200
       TEMPERATURE=0.0
       DROPBOX_LOCAL_FOLDER_PATH={REPLACE_WITH_DROPBOX_RELATIVE_PATH}
       ```
   3.  **Alternative to using `export`**: If `.env` doesn't work for you, you can set these variables directly in your shell using the command below. However, it is important to note that variables set with `export` (Linux/macOS) or `set` (Windows, as seen below) last only for the current session. If you want them to persist, you'll need to add them to shell configuration files like add to `.bashrc` or `.bash_profile` for Linux/macOS, or use System Properties on Windows.\


       <pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><strong>export OPENAI_API_TOKEN={OPENAI_API_KEY}
       </strong>export EMBEDDER_LOCATOR=text-embedding-ada-002
       export EMBEDDING_DIMENSION=1536
       export MODEL_LOCATOR=gpt-3.5-turbo
       export MAX_TOKENS=200
       export TEMPERATURE=0.0
       export DROPBOX_LOCAL_FOLDER_PATH={REPLACE_WITH_DROPBOX_RELATIVE_PATH}
       </code></pre>

**Setting the environment variables in Windows:**

1. Create an `.env` file using a text editor of your choice.
2. Populate the `.env` file as shown above.
3.  **Alternative**: Use the `set` command in Command Prompt to set environment variables.\
    \
    **Note:** Replace `{OPENAI_API_KEY}` with your OpenAI API key and `{REPLACE_WITH_DROPBOX_RELATIVE_PATH}` with your local Dropbox path.\


    {% code overflow="wrap" %}
    ```cmd
    set OPENAI_API_TOKEN={OPENAI_API_KEY}
    set EMBEDDER_LOCATOR=text-embedding-ada-002
    set EMBEDDING_DIMENSION=1536
    set MODEL_LOCATOR=gpt-3.5-turbo
    set MAX_TOKENS=200
    set TEMPERATURE=0.0
    set DROPBOX_LOCAL_FOLDER_PATH={REPLACE_WITH_DROPBOX_RELATIVE_PATH}
    ```
    {% endcode %}

### Step 3: Building and Starting Containers

Now we will build the Docker image and start the containers.&#x20;

Navigate to the cloned directory`dropbox-ai-chat`. Then run these commands.

```bash
docker-compose build 
docker-compose up
```

**Behind the Scenes with Docker:**

* **Dockerfile**: This file contains a set of instructions that Docker follows to build an image. It's like a blueprint for your application. Docker reads these instructions and creates a Docker image based on them. This image contains everything your app needs to run.
* **docker-compose**: It's a tool for defining and running multi-container Docker applications. In our context, `docker-compose` uses the `docker-compose.yml` file to understand how to set up and run the app's services.&#x20;
* When you run `docker-compose up`, it starts the services as defined.

### Step 4: Accessing Applications

**What it does**: Opens access to your API and Streamlit UI.

* **Access Points for your application**:
  * API: [`http://localhost:8080/`](http://localhost:8080/)
  * Streamlit UI: [`http://localhost:8501/`](http://localhost:8501/)

### Step 5: Stopping Containers

To stop the services and remove the containers, execute:

```bash
docker-compose down
```

By following these steps, you should be able to get both the main application and the Streamlit UI up and running using Docker Compose.

### :bulb: An interesting thing to notice&#x20;

Interestingly if you quickly revisit the [LLM Architecture diagram](https://ai-community-iitb-organization.gitbook.io/10-days-llm-bootcamp/retrieval-augmented-generation-and-llm-architecture/llm-architecture-diagram-and-various-steps) we saw earlier, there was a prompt from a Customer Support Executive trying to understand the product release notes made by the development team. With something like the Dropbox app, that problem can be easily addressed.&#x20;

Now let's look at another example where we use an API as a data source.

