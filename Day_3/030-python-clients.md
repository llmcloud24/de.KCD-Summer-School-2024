# Connecting to LLMs from software: Python clients

The second level of accessing an LLM from third-party software beyond the
command line is using dedicated clients, for example from JavaScript or Python.
Most LLM vendors provide Python clients, which includes proprietary (
[OpenAI](https://github.com/openai/openai-python),
[Anthropic](https://github.com/anthropics/anthropic-sdk-python)) and open-source
models ([Ollama](https://github.com/ollama/ollama-python), [Xorbits
Inference](https://inference.readthedocs.io/en/latest/index.html)). These
clients allow you to interact with the models from any Python program, including
web applications; often, they also allow you to deploy models straight from
Python.

Ultimately, this connectivity allows you to build your own applications that
allow users to interact with the LLMs you have deployed, or to use the LLMs
behind the scenes to enhance the functionality of your software, such as
performing Retrieval-Augmented Generation (RAG) on a Knowledge Graph you created
(compare Day 2). We have created examples of LLM-driven applications using the
BioChatter framework:

- Generic prototyping framework in pure Python: [BioChatter
Light](https://light.biochatter.org)

- More elaborate frontend with REST API: [BioChatter
Next](https://next.biochatter.org)

- Cancer genetics use case, Light version: [DECIDER
Light](https://decider-light.biochatter.org)

- Cancer genetics use case, Next version: [DECIDER
Next](https://decider-next.biochatter.org)

- [Project management from GitHub boards](https://project.biochatter.org)

However, before we dive into the complexity of building web applications, we
will first explore the basic steps of connecting to an LLM from Python.

## Connecting to Ollama via the Ollama Python client

### Installation

We will start by creating a Conda environment and installing the Ollama Python
library. If you went through the [advanced deployment](020-advanced.md) section,
you already have an environment for Xorbits Inference. You can activate this one
and simply install Ollama in it, as it uses lots of the same dependencies.

```bash
conda activate xinference
pip install ollama
```

If you have not yet created an environment, you can do so now:

```bash
conda create -n ollama python=3.11
conda activate ollama
pip install ollama
```

### Running the client

We can now enter the Python REPL (Read-Eval-Print Loop) and interact with the
Ollama client. From the bash shell, type `python` to enter the Python REPL. You
know you're in the Python REPL when you see the `>>>` prompt. You can now import
the Ollama client.

```python
import ollama
```

> [!TIP]
> If you are faced with a `ModuleNotFoundError`, you might need to check if you
> successfully installed the package, and if you are in the correct Conda
> environment.

Next, we can prepare a message to send to the LLM. This is the first distinction
to the chat-like command interface: we need to prepare the input as a list of
dictionaries with the keys 'role' and 'content'. The 'role' is 'user' for the
user input; the list of dictionaries is used to allow for a string of messages
to be passed (usually, a back-and-forth between 'user' and 'assistant'
messages; some models also have the 'system' role for passing instructions).

```python
messages = [{'role': 'user', 'content': 'Hi!'}]
```

Now we can call the `chat` method of the ollama class (we don't need to
instantiate anything, the imported module is already a class instance). We
specify the model and the messages to send, and save the response in a variable.

```python
response = ollama.chat(model='mapler/gpt2', messages=messages)
```

Finally, we can print the response to see what the model has to say.

```python
print(response['message']['content'])
```

### Exercises

1. Inspect the complete response object. What is in there, what is the purpose?

2. Try to get a response from a different model, such as llama3.1; which line(s)
of code do you need to change?

3. Run a model that you have not run from the CLI yet. What happens? How can you
fix it?

> [!TIP]
> Ollama docs can be found [here](https://github.com/ollama/ollama-python).

4. If you did the advanced deployment: What is the difference between the Python
APIs for Ollama and Xorbits Inference? What are the advantages and disadvantages
of each?

## Connecting via the BioChatter Python client

### Installation

Into the same environment as before, install the BioChatter Python library.

```bash
pip install biochatter
```

### Running the client

We can now enter the Python REPL and interact with the BioChatter client.

```python
from biochatter.llm_connect import OllamaConversation

conversation = OllamaConversation(
    base_url="http://localhost:11434",
    prompts={},
    model_name='llama3.1',
)
response, token_usage, correction = conversation.query("Hi!")
```

### Exercises

1. Inspect the tuple `response, token_usage, correction` that the `query` method
returns. What are the three elements?

2. How does the BioChatter client differ from the Ollama client? What are the
advantages and disadvantages of each?

> [!TIP]
> More information on the BioChatter chat functionality can be found
> [here](https://biochatter.org/features/chat/) and
> [here](https://biochatter.org/features/open-llm/).

## Conclusion

We have seen how to connect to an LLM from Python using the Ollama and
BioChatter clients. Clients such as these are the backbone of any application
that interfaces with an LLM, allowing you to build applications of any
complexity and purpose. Lastly, we will explore how these clients fit into the
bigger framework of backend components, middleware, and frontends that make up
a modern web application in [Section 4](040-web-app-pole.md).