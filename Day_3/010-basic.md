# Deploying an LLM - Basic

In the shell of the VM, we start by installing Ollama as instructed in the
[Ollama Documentation](https://ollama.com/download/linux).

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

We are now already set to deploy an LLM using Ollama. A list of models can be
found [here](https://ollama.com/library). For instance, we may want to deploy
the GPT-2 model for historic reasons. It only has a size of 328 MB, and
interacting with it is fast, but quite different from the commercial models
available today. Give it a try:

```bash
ollama run mapler/gpt2
```

See if you can get the model to explain to you what the key messages of the 2017
paper "Attention is all you need" are. Or how it responds to you saying "Hi!".

> [!TIP]
> For understanding the difference between legacy models like GPT-2 and the
> conversational style of current models, we can look into advances in
> *instruction fine-tuning* and *reinforcement learning from human feedback*;
> see for example this [IBM blog post](https://www.ibm.com/topics/instruction-tuning).

If we want to deploy a current state-of-the-art model, we can use the llama-3.1
model instead. You can find it at the top of the model page, as it is currently
by far the most popular model.

```bash
ollama run llama3.1
```

Without specifying the exact model variant, Ollama will deploy the default for
this model. I encourage you to try the same queries as with the GPT-2 model and
see how the responses differ.

When you're done chatting, you can type `/bye` to exit from the running chat session.

> [!TIP]
> As an exercise, find out which exact model variant is deployed by default
> (size, quantisation, etc.).

## Exercise

Deploy the larger (70B) variant of the llama3.1 model, or a different model from
the Ollama library. Which differences do you notice between the models?

Further questions to consider:

- What are the effects of model size on model behaviour, deployment time, and
inference speed?

- What are the effects of model quantisation on model behaviour, deployment
time, and inference speed?

- What is the behavioural difference between completion models like GPT-2 and
instruct-tuned models like llama3.1?

Feel free to experiment with different models and see how they behave; or, if
you are interested in other deployment options, proceed to the [next
section](020-advanced.md).
