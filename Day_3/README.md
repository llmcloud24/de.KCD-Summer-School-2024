# Day 3 - Deploying LLMs in the Cloud

Table of Contents:

- [0 Background (this README)](#background)

- [1 Basic deployment - Ollama](010-basic.md)

- [2 Advanced deployment - Xorbits Inference](020-advanced.md)

- [3 Connecting from Python clients](030-python-clients.md)

- [4 Web application composition and deployment](040-web-app-pole.md)

## Prerequisites

>[!NOTE]
>Please create a GPU VM using the `de.NBI GPU T4 medium` flavour and `Ubuntu-24.04-20240913-gpu` image for your VM.

You should be able to connect to your assigned VM from your machine, using an
SSH client. The machine should run Ubuntu and have access to the internet, as
well as Conda, Python, and Docker.

If Conda is not installed, we can install
[Miniforge](https://github.com/conda-forge/miniforge), a minimal version of
Anaconda, by running the following commands:

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
bash Miniforge3-$(uname)-$(uname -m).sh
```

>[!TIP]
>If you're using the `Ubuntu-24.04-20240913-gpu` image for your VM, the Conda installer is already included in the `ubuntu` user's home folder: `/home/ubuntu/Miniforge3-Linux-x86_64.sh`.

## Background

In this session, we will talk about LLMs and how to deploy them in the cloud.
A defining characteristic of working on cloud-based VMs is that you will do most
of your work in the terminal. This is because cloud-based VMs are usually
headless, meaning they do not have a graphical user interface. We will connect
to the VM using SSH and interact with the LLM using the command line and Python
REPL.

Ultimately, we aim to deploy a web application for our users, as shown in the
examples below. However, we will not be able to see this web application on our
VMs before setting up a reverse proxy, which we will do on [Day 4](../Day_4).
The remainder of the webinar, including days 4 and 5, consists of the following
components:

- The LLM: A collection of model weights from a public repository that allows
deployment of the model using specific software.

- The LLM deployment tool: A Python package that allows you to deploy a range of
LLMs on a GPU-enabled machine, such as the cloud-based VMs you have created on
Day 1.

    - Ollama: A simple deployment tool with focus on ease of use. Covered in [Lection 1](010-basic.md)

    - Xorbits Inference: A more advanced deployment tool that allows you to
    deploy custom models. Covered in [Lection 2](020-advanced.md)

- Software for interfacing with the LLM: A Python package and more elaborate
frontends that allow interfacing with the user to enable tasks that use the LLM.

    - [Ollama API](https://github.com/ollama/ollama-python): Ollama comes with its own command-line interface that allows
    quickly deploying and interacting with its models. It also provides a Python
    interface. Covered in [Lection 3](030-python-clients.md)

    - [BioChatter](https://biochatter.org): A Python package that allows you to
    interface with the LLM using a Python shell. Covered in [Lection 3](030-python-clients.md)

    - [BioChatter Light](https://light.biochatter.org): A Python-based frontend (made using
    [Streamlit](https://streamlit.io/)) that allows fast prototyping of web
    applications. Covered in [Lection 4](040-web-app-pole.md)

    - [BioChatter Next](https://next.biochatter.org): A more elaborate frontend solution that uses a REST API
    based on [FastAPI](https://fastapi.tiangolo.com/) and a frontend based on
    [Next.js](https://nextjs.org/). Not covered in this session.

> [!NOTE]
> BioChatter is our own work, designed to make the process of deploying LLMs
> easier. Naturally, you can use frontend solutions of your choice, such as
> [Streamlit](https://streamlit.io/), [Dash](https://dash.plotly.com/),
> [FastAPI](https://fastapi.tiangolo.com/), or 
> [OpenWebUI](https://openwebui.com). These all have different
> levels of expressiveness and complexity, and you can choose the one that fits
> your needs best.

- Authentication and deployment layer (Day 4): A software layer that allows you
to deploy your application to the internet and authenticate users. Briefly, this
involves setting up a reverse proxy using Nginx, domain specification, and
SSL certificates.

Here are diagrams for the basic and advanced deployments:

### Basic Deployment

```mermaid
sequenceDiagram
    participant User
    participant LLM as LLM (Model Weights)
    participant Ollama as Ollama (Simple Deployment)
    participant CLI as Ollama CLI
    participant BioChatter as BioChatter (Python Shell)
    participant Light as BioChatter Light (Streamlit Frontend)
    participant Next as BioChatter Next (FastAPI + Next.js Frontend)
    participant Auth as Authentication and Deployment (Nginx, Domain, SSL)

    User->>LLM: Requests to deploy LLM
    LLM->>Ollama: Deploy with simple tool
    Ollama->>CLI: Use Ollama CLI to interact with model
    Ollama->>BioChatter: Use BioChatter for Python interface
    Ollama->>Light: Use BioChatter Light for Streamlit frontend
    Ollama->>Next: Use BioChatter Next for FastAPI and Next.js frontend
    Light->>Auth: Deploy app with Nginx, domain, and SSL
    Next->>Auth: Deploy app with Nginx, domain, and SSL
    Auth->>User: Provide user access to deployed app
```

### Advanced Deployment

```mermaid
sequenceDiagram
    participant User
    participant LLM as LLM (Model Weights)
    participant Xorbits as Xorbits Inference (Advanced Deployment)
    participant BioChatter as BioChatter (Python Shell)
    participant Light as BioChatter Light (Streamlit Frontend)
    participant Next as BioChatter Next (FastAPI + Next.js Frontend)
    participant Auth as Authentication and Deployment (Nginx, Domain, SSL)

    User->>LLM: Requests to deploy LLM
    LLM->>Xorbits: Deploy custom model
    Xorbits->>BioChatter: Use BioChatter for Python interface
    Xorbits->>Light: Use BioChatter Light for Streamlit frontend
    Xorbits->>Next: Use BioChatter Next for FastAPI and Next.js frontend
    Light->>Auth: Deploy app with Nginx, domain, and SSL
    Next->>Auth: Deploy app with Nginx, domain, and SSL
    Auth->>User: Provide user access to deployed app
```

We will start with [basic deployment](010-basic.md) in the first session, using
[Ollama](https://ollama.com). If you're done with basic deployment before the
break, you can proceed to the [advanced deployment](020-advanced.md) session,
which introduces [Xorbits
Inference](https://inference.readthedocs.io/en/latest/index.html). After the
break, we will continue to [connecting to LLMs from Python
clients](030-python-clients.md) and finally have a brief look at [web
application composition and deployment](040-web-app-pole.md) in preparation for
[Day 4](../Day_4).
