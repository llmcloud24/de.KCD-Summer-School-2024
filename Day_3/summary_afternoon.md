Below is a summary generated by Zoom's AI meeting assistant, for the record.

# Meeting Summary for deKCD afternoon

Sep 18, 2024 11:59 AM Amsterdam, Berlin, Rome, Stockholm, Vienna ID: 835 7395 8835

Quick recap

Sebastian led a discussion on deploying Large Language Models (LLMs) using software on a Virtual Machine (VM) and programmatic access to LLM responses through Python clients. The team also explored the deployment of custom models, the use of Olama poll command, and the potential benefits and limitations of fine-tuning models. Lastly, they discussed the integration of AI into research environments, the potential of integrating AI into research environments, and the importance of keeping these tools open-source and under the control of the scientific community.

Next steps

Participants to install and set up Olama on their local machines if they haven't already.
Participants to try running the Bio Chatter Light application locally using Docker Compose.
Participants to experiment with different queries on the deployed knowledge graph application.
Participants to compare the performance of open-source models (like Llama) with closed-source models (like GPT) in text-to-query tasks.
Participants to explore the Bio Chatter documentation and vignettes for more detailed information on knowledge graph RAG implementations.
Interested participants to get in touch with Sebastian for potential collaborations on LLM integration projects.
Participants to prepare for tomorrow's session on making applications available outside the VM and implementing authentication.
Tauseef to follow up with Sebastian regarding potential LLM integration in their BMVF project related to gender.
Jay to meet with Sebastian in Heidelberg to discuss further.
Participants to review the Bio Chatter preprint and documentation for more information on text-to-query approaches.
Lena to explore the Bio Chatter framework for potential use in their own text-to-query system.
Participants to consider strategic approaches for LLM development, focusing on areas not heavily pursued by large tech companies.
Participants to experiment with few-shot learning as an alternative to fine-tuning for specific use cases.

## Summary

Breakout Rooms, Zoom Link, and Lunch Break Discussion

Sebastian created three breakout rooms for participants to choose from. He also sent the Zoom link to Lisa via email and chat. There was a discussion about the lunch break and the need to use RP credentials. Martin checked his microphone, and Lisa confirmed that she could hear everything. The team also discussed the possibility of Peter joining the meeting.

Deploying LLMs and Programmatic Access Discussion

Sebastian explained the process of deploying a Large Language Model (LLM) using software on a Virtual Machine (VM) and discussed programmatic access to LLM responses through Python clients provided by vendors like OpenAI, Anthropic, and open-source initiatives. He highlighted the use case for the Decider project, which aims to improve clinical decisions by providing an LLM-powered tool for geneticists and doctors. Sebastian guided the team through setting up a Conda environment, installing the Python client for Llama, and demonstrated how to use the client. He also addressed an issue Vladimir encountered with Conda not being recognized in the shell. Max suggested that pulling a model should be done outside of the Python command line, which Sebastian confirmed.

Running X Inference With Python and Error Resolution

Sebastian guides Tauseef in running X inference with Python, but Tauseef encounters an error. They discover Tauseef is not in the correct environment and needs to install X inference. After installing it, Tauseef can proceed. Sebastian mentions an exercise to compare clients for different applications. Avihay raises a question at the end.

Custom Model Deployment and Composite Models

Avihay and Sebastian discussed the deployment of custom models as opposed to basic ones. Sebastian explained that any model weight definition can be downloaded from Hugging Face and configured correctly in the YAML file to run any model, not just the built-in ones. Tauseef asked about running composite models, to which Sebastian responded that it's possible to run as many models as capacity allows, but combining outputs from multiple models is difficult. Max asked about training a model by the output of another model, to which Sebastian explained that it's a common practice in open-source models, but it's not always better than training with real data. Vladimir asked about running any model from Hugging Face with Olama, to which Sebastian clarified that X inference has dedicated support for all backends and can be configured for any model. The team also discussed the response object from the model, with Max explaining its various components and Sebastian suggesting its use for managing conversations and limiting input space.

Exploring Olama Poll Command and LLM APIs

Sebastian discussed the use of the Olama poll command in an app that allows users to switch between models, and its application in their benchmark setup. Tauseef confirmed that the Olama poll command worked. The team compared the APIs of Olama and Exemptions, noting that Exemptions is more complex but more powerful, while Olama is simpler and easier to use. Sebastian also discussed the differences between Llama and X Inference, highlighting that Llama is simpler to set up and use, while X Inference is more complex and designed for higher-level use cases. He demonstrated how to connect to Llama using the Bio Chatter library and the Olama conversation, emphasizing the aim of having a unified API for different LLM vendors.

Legacy Fact-Checking Model and Agent-Based Setup

Sebastian discussed the legacy implementation of a fact-checking model in their framework, which was initially designed for contextual conversations in biomedical or bioinformatics contexts. He explained that the model checks the accuracy of responses from the main model and returns a tuple containing the response, correction, and token usage. However, he noted that this implementation is now outdated and they are moving towards a more elaborate agent-based setup. Sebastian also explained the workings of the conversation class, the creation of an application that uses programmatic interaction with LLMs to solve a problem, and the use of the Biocheta framework to specify a purpose-driven application. He concluded by explaining the steps to deploy the web app using Docker and the need to use a specific file for Olama.

Docker Compose, Virtual Machines, and Deployment

Sebastian discussed the benefits of using Docker Compose over running applications individually, highlighting its improved output, reproducibility, and execution speed. He also mentioned the use of virtual machines and commercial cloud vendors for deploying Docker environments, noting some issues with different operating systems. Sebastian demonstrated how to deploy a web application using Docker and Neo4j, explaining the process of building a knowledge graph and configuring the application to connect to the Docker internal network. Tauseef suggested opening the port for external access, but Sebastian noted that this might not be possible. Sebastian ended the conversation by demonstrating the application's functionality, including its ability to generate queries and return sensible responses.

Exploring Olama and Open Source Models for Query Improvement

Sebastian discussed the potential benefits of using Olama and open source models for improving query results, as well as their limitations in handling complex queries. He clarified that the open AI docker container runs locally due to localhost access and offered to further discuss setting up a text generation system. Sebastian shared his experience deploying LLM on a high-performance GPU and recommended using open source frameworks like Open Web UI for local deployment. The team was encouraged to try setting up LLM on their machines.

Fine-Tuning Models and Few-Shot Learning Discussion

Sebastian discussed the limitations and potential of fine-tuning models, particularly in relation to the pace of new model releases. He suggested that fine-tuning might be useful for specific tasks, such as changing the behavior of a model or adhering to specific output formats, but cautioned that it could be time-consuming and not always worth the effort. He also mentioned the potential of few-shot learning as an alternative to fine-tuning. Sebastian further discussed the challenges of controlling model behavior, citing an example of a model that sometimes includes unnecessary text in its output. He also mentioned a publication related to text-to-query approach, which he promised to share in the chat. The conversation ended with plans for Sebastian to provide a closing statement and set up a follow-up meeting.

Docker Compose Integration and AI in Research Environments

Tauseef successfully integrated his key into Docker Compose on his local machine. Sebastian discussed his experience with OpenAI's system, which provided a different interpretation of instructions compared to Lama 3. He speculated that OpenAI might use methods like system instructions or reinforcement learning to address such issues without releasing a new model. Sebastian suggested the potential of integrating AI into research environments, emphasizing the importance of keeping these tools open-source and under the control of the scientific community. He also mentioned ongoing collaborations with other research institutions and encouraged others to reach out for potential collaborations. The conversation ended with plans for a follow-up meeting the next day.