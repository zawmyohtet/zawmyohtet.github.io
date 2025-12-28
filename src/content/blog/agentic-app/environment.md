---
title: "Agentic App Development Environment with Docker"
description: ''
publishDate: 2025-07-02 00:14:46
language: 'English' 
heroImage: { src: './dependency-cloud.png', alt: 'agentic ai app', color: '#B4C6DA' }
tags: ['LLM', 'ollama', "docker", "jupyter", "langgraph", "langchain", "langgraph-studio"]
comment: false
---
This guide will walk you through setting up a Python development environment, complete with [Jupyter](https://jupyter.org/), [LangChain](https://www.langchain.com/langchain), [LangGraph](https://www.langchain.com/langgraph), and [LangGraph Studio](https://langchain-ai.github.io/langgraph/concepts/langgraph_studio/), all containerized with Docker. It'll also cover how to run a Large Language Model (LLM) locally using [Ollama](https://ollama.com/) and use together from Jupyter.

*(A quick note: This tutorial is based on a macOS environment. While the core concepts apply universally, you might encounter minor differences depending on your operating system.)*

## Prerequisites

Before we begin, ensure you have the following installed:

- **[Docker](https://www.docker.com/):** Essential for containerizing our development environment.
- **[Ollama](https://ollama.com/):** For managing and running local LLMs.

## Docker Environment Setup

Let's start by structuring our project. Create the following directories and files in your chosen project root:

```bash
config/
docker-compose.yml
dockerfiles/
workspace/
```

This structure is a base on my personal preference, but feel free to adapt it to your preferred workflow.

Next, create your **Dockerfile** inside the **dockerfiles** directory. Name it **Jupyter.Dockerfile**:

```docker
# syntax=docker/dockerfile:1

FROM quay.io/jupyter/base-notebook

COPY ./dockerfiles/requirements.txt .

RUN pip install -r requirements.txt
```

In the same dockerfiles directory, create a **requirements.txt** file. This lists the Python packages that may be needed for our environment. It includes common dependencies for LangGraph and Kaggle, but you can customize it as required for your specific projects:

```txt
langgraph
langchain-ollama
transformers
langgraph-prebuilt
langgraph-sdk
langgraph-checkpoint-sqlite
langsmith
langchain-community
langchain-core
langchain-openai
notebook
tavily-python
wikipedia
trustcall
langgraph-cli[inmem]
matplotlib
scikit-learn
pandas
kaggle
kagglehub
scipy
statsmodels
fastcluster
seaborn
```
Now, let's configure your **docker-compose.yml** file in your main project directory:

```yml
services:
  jupyter:
    build:
      context: .
      dockerfile: dockerfiles/Jupyter.Dockerfile
    tty: true
    container_name: jupyter
    ports:
      - 8888:8888 # Jupyter web UI
      - 2024:2024 # LangGraph Studio
    volumes:
      - ./workspace:/home/jovyan/work # Mount your project files
      - ./config:/home/jovyan/.config # For configuration files (e.g., Kaggle)
    command: start-notebook.py --NotebookApp.token='<replace_with_your_token>'
    networks:
      - app-network
volumes:
  jupyter-data:
    name: jupyter-data
  dev-cache:
    driver: local

networks:
  app-network:
    driver: bridge
```

In this configuration, we expose ports **8888** for Jupyter and **2024** for LangGraph Studio. The **volumes** section ensures your project files in **workspace** and any configuration in **config** are accessible within the container.

With the files in place, navigate to your project root in the terminal and start the Docker environment:

```bash
docker compose up -d
```

To check the status:

```bash
docker compose ps
```
To access the command line within your Docker environment:

```bash
docker compose exec jupyter bash
```

You can access the **Jupyter web UI** via [https://127.0.0.1:8888/lab?token=<replace_with_your_token>](https://127.0.0.1:8888/lab?token=<replace_with_your_token>). 

**LangGraph Studio** via [https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024](https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024). 

Note: Before accessing LangGraph Studio, remember to start server from your project directory *within* the Docker environment:

```bash
langgraph dev
```

For more detail about usage and setup, you can follow official [documentation](https://langchain-ai.github.io/langgraph/concepts/langgraph_studio/).

## Ollama for Local LLMs

Now, let's get an LLM running locally with Ollama. If Ollama is correctly installed, you can confirm its functionality:

```bash
ollama -h
```

Visit the [Ollama website](https://ollama.com/) to browse available models. Choose a model that fits your system's resources. For instance, to download and run the **gemma3:1b** model locally:

```bash
ollama run gemma3:1b
```
Once the model is loaded, you're ready to start leveraging your locally hosted LLM through Jupyter, typically by utilizing the langchain_ollama package.

```python
from langchain_ollama import ChatOllama

llm = ChatOllama(
    model="gemma3:1b",
    temperature=0,
    base_url="http://host.docker.internal:11434"
)
```