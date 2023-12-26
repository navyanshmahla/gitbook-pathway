# Understanding Docker

This module will help you build the previous file if you're new to Docker and are struggling to install dependencies on your machine.&#x20;

**First off, a quick recap.**&#x20;

Think of Docker as a shipping container for your app. Just as a shipping container can hold all sorts of goods (clothes, electronics, etc.) and be transported anywhere in the world, Docker bundles your app and everything it needs to run into a '**container**.' This makes it easy to share and run your app on any computer.

Given the complexities and manual effort involved in resolving dependency issues in your system, Docker can be a beneficial tool to standardize the development environment among all students.

\
**Why Use Docker?**

* **Standardized Environment**: Everyone gets the same set of dependencies, reducing "it works on my machine" issues.
* **Isolated**: Doesn't interfere with other projects or system-wide settings.
* **Ease of Use**: Running the project becomes much simpler once set up.

### Understanding Key Docker Terminologies

* **Docker Image**: Consider this a blueprint or a container snapshot, including the application and its dependencies. You build an image once and use it to create multiple containers.
* **Docker Container**: A container is a running instance of an image. It's a lightweight, stand-alone, executable software package with everything needed to run the code.
* **CMD**: In Docker, the `CMD` instruction specifies the command to execute when the container starts up.
* **Docker Compose:** A tool for defining and running multi-container Docker applications. Using a YAML file (`docker-compose.yml`), it allows you to specify how different containers interact with each other, making it easier to manage multiple containers as a single service.

### Resources to Understand Docker Better

* Basic Tutorial on Dockerfile: [Here](https://youtu.be/0eMU23VyzR8)
* Basic Tutorials on Docker Compose: [Part 1 using (Single Container)](https://youtu.be/600SC33F6Ag), [Part 2 (using 2 Containers)](https://youtu.be/WBqHr2kPc\_A)
* Blog on using ChatGPT to build an optimized Docker Image: [3-Minute Read](https://collabnix.com/when-chatgpt-meet-docker-for-the-first-time/)

Now let's see the step-by-step implementation.
