# LLM-Playground
Exploring the capabilities, limitations, and applications of LLMs through real world use cases.


## ChatBot using HuggingFace Transformers
This is a command line ChatBot using pretrained language models from HuggingFace. It continuously takes user input from the terminal, passes it to the language model to generate a response, prints the model's reply and then continues this loop till the user types 'quit', 'exit', or 'bye'. The input string from the user's query is tokenized into a Pytorch tensor. These tokens are fed into the LLM model. The tokens output by the LLM model are decoded back into text and output as response.

## Local Research Assistant with Ollama and LangChain
Using Retrieval Augmented Generation, the research assistant is able to fetch relevant documents and sources based on the user's search query. Note: RAG does not necessaily need to have a vector database. RAG's key idea is that the LLM is given access to external information at inference time to augment its output with that information. A LangGraph state machine is used to implement the research workflow. The key components of this workflow are:
- Generate a Query: The user inputs a research topic and sets the number of research iterations the user wants the model to make. Default set to 3.
- Retriever: Tavily API to do web search and retrieve external knowledge. The information retrieved is processed and formatted. 
- Context Generation: The retrieved information is passed into the chosen LLM model to 'augment' its prompt and update its running summary. Any detected gaps are filled using follow-up queries equal to the user configured research iterations.
- Generator Output: The Ollama hosted model reads the context and generates a final answer.
