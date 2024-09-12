# Deploying an LLM - Advanced

## Installing Xorbits Inference

For deploying custom models, we can use Xorbits Inference. Since this is a
Python library, we would like to install it in a Conda environment. We can do
this by creating a new environment and installing the package:

```bash
conda create -n xinference python=3.11
conda activate xinference
pip install xinference[all]
```

Xinference allows accessing multiple deployment avenues (libraries), such as
Transformers (Hugging Face), vLLM, and Llama.cpp (more info
[here](https://inference.readthedocs.io/en/latest/getting_started/installation.html#installation)).
Using the flag `[all]` installs all of them, but you can also install them
individually. Using a model in Xinference, you need to specify which backend to
use using the `Model Engine` parameter.

## Starting the XInference CLI

We are now ready to start the xinference CLI application that allows model
deployment. We add an ampersand to the command to run it in the background:

```bash
xinference-local &
```

The CLI will start a web server on port 9997 (by default), which can be accessed
in various ways, including via their GUI, from the command line, and via Python.
We will use the latter for this exercise.

## Deploying a builtin model from Python

Once the service is running, we can deploy a model using the Xinference Python
client. The following code snippet deploys the llama-3.1-instruct model:

```python
from xinference.client import RESTfulClient
client = RESTfulClient("http://127.0.0.1:9997")
model_uid = client.launch_model(
    model_name="llama-3.1-instruct",
    model_engine="llama.cpp",
    model_size_in_billions=8,
    model_format="ggufv2",
    quantization="Q4_K_M",
)
print(model_uid)                # this is the model we just deployed
print(client.list_models())     # this returns all running models
```

You can also stop any deployed model using the following command:

```python
client.terminate_model(model_uid)
```

Most importantly, we can send requests to any running model using the following
syntax:

```python
model = client.get_model(model_uid)
response = model.chat(
    messages=[
        {"role": "user", "content": "Who am I talking to?"}
    ]
)
print(response)
```

Naturally, this is not a very convenient way of having a conversation, but it is
a substantially more powerful way of programmatically interacting with the
model. 

> [!TIP]
> As an exercise, inspect the `response` object. What does it contain? How would
> you use it in a real-world application?

## Xinference Models

Xinference provides a long list of builtin models, which are not just
conversational model, but also embedding, multimodal, and other types of models.
The full list can be found
[here](https://inference.readthedocs.io/en/latest/models/builtin/index.html).

Using the backends included in the library, we can also deploy custom models
using a simple configuration, which is described
[here](https://inference.readthedocs.io/en/latest/models/custom.html).

## Exercise

Experiment with the Xinference library and deploy a model of your choice
(builtin, custom, embedding, multimodal, audio, etc.). How does the deployment
process differ from Ollama? What are the advantages and disadvantages of using
Xinference over Ollama?