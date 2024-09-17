#

Compared to GPT-3.5 and above, the llama3.1 questions have to be more modest, or
the multi-stage query generation process will fail. Instead of the questions
given in the [pole README](https://github.com/biocypher/pole), try something
like this:

- return five locations

- count all locations

- how many persons

- return all first names starting with P

- who was PARTY_TO most crimes

You will note that this becomes very "hacky" and cannot be presented to a naive
user. However, for the purpose of this exercise, we are not interested in
performance of the model or prompt engineering questions.

This concludes the LLM deployment part of the summer school. Tomorrow, we will
learn how to expose this web application and others to the internet and how to
authenticate users.