# Prerequisites

Before we dive in, let's ensure you have all the necessary prerequisites installed on your computer. Not only are these essential for what we're about to embark on, but they'll also be invaluable tools if you decide to contribute to open-source projects in the future.

### Git, Python, and Pip

* Python 3.10 or above should be installed on your machine. If not, [Download Python](https://www.python.org/downloads/).
*   Pip: Comes pre-installed with Python 3.4+. It is the standard package manager for Python. You can check if it's downloaded by typing the below command in your terminal/command prompt.



    ```
    pip --version
    ```


* If Pip is not installed, you'll get an error. In that case, you must download and install [Pip](https://pip.pypa.io/en/stable/installation/) to manage project packages.&#x20;
* Git should be installed on your machine. If you've installed XCode (or its Command Line Tools), Git may already be installed. To find out, open a Terminal or Command Prompt, and enter `git --version`. If it's not installed, refer to [this documentation](https://www.atlassian.com/git/tutorials/install-git) and install it.&#x20;

### OpenAI API Key (Recommended)

This key is required if you plan to use OpenAI models for embedding and generation.&#x20;

This is a good starting point if you are less confident with using open-source alternatives. If you want to use open-source models, you can find examples like [the one here](https://github.com/pathwaycom/llm-app/blob/main/examples/pipelines/local/app.py). &#x20;

By default, OpenAI currently offers $5 in free credits for new accounts – i.e., the ones with a new phone number and email ID. Alternatively, you can sign up for free credits on platforms like [Eden AI](https://www.edenai.co/eden-ai-for/developers). These free credits should suffice for building your project.&#x20;

As we advance, we will use`text-embedding-ada-002` in this coursework for generating the vector embeddings ([OpenAI documentation](https://openai.com/blog/new-and-improved-embedding-model)) and `gpt-3.5-turbo` for text generation.

**To create a new OpenAI API Key:**

* [Log in](https://platform.openai.com/login?launch) to the OpenAI website.
* Navigate to the [API Key Management](https://platform.openai.com/account/api-keys) page to generate your key.

### Note: If you're using Windows OS

The example ahead only supports Unix-like systems (such as Linux, macOS, and BSD).&#x20;

But the good news is that you have an easy fix. If you are a Windows user, you can use [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install) or Dockerize the app to run as a container.

### What is Docker and how do you install it?

Think of Docker as a shipping container for your app. Just as a shipping container can hold all sorts of goods (clothes, electronics, etc.) and be transported anywhere, Docker bundles your app and everything it needs to run into a '**container**.' This makes it easy to share and run your app on any computer.

Like Docker, there is a tool called **Conda**, which is showcased in one of the videos above. Conda lets you create separate environments to manage different sets of Python packages, ensuring your code runs the same way on any computer.&#x20;

Conda and Docker aim to solve the problem of "it works on my machine" by isolating your project and its dependencies.

* You can download Docker [from here](https://www.docker.com/products/docker-desktop/).
* You can download Conda [from here](https://docs.conda.io/projects/conda/en/stable/user-guide/install/download.html).

Now that we have the prerequisites, let's proceed. :smile:
