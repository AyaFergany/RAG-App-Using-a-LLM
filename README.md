# RAG-App-Using-a-LLM

In this project, we leverage Weaviate, a vector database, to power our retrieval-augmented generation (RAG) application. Weaviate enables efficient vector similarity search, which is crucial for building effective RAG systems. Additionally, we use local language model (LLM) and embedding models to ensure privacy and confidentiality of sensitive information.

Here are the key components of our project:

## Weaviate Integration
- Weaviate serves as our vector database. It allows us to ingest and retrieve documents efficiently.
- To connect to Weaviate, you’ll need the Weaviate API key and endpoint. You can find these details in the Weaviate dashboard or configure them programmatically.
  https://orkes.io/content/integrations/vector-databases/weaviate

## Local Embedding and LLM Models
- I’ve chosen the sentence\_transformers/all-mpnet-base-v2 embedding model and the zephyr-7b-alpha LLM from Hugging Face.
- These models are open source and well-suited for our use case.

## Ingesting HubermanLabs Podcasts into Weaviate
- YouTube channels have RSS feeds that provide links to the latest videos.
- I can extract these links using a simple Python script.
- After obtaining the video links, we use the YoutubeLoader from LangChain to retrieve captions.
- The text is then chunked into smaller pieces using the text splitter functionality in LangChain.

## Creating a Simple Chatbot with Gradio
- Gradio is an excellent library for building interactive interfaces for LLMs, including chatbots.
- I’ve created a basic chatbot using Gradio, which allows users to interact with the model through a user-friendly interface.
- The chatbot responds to user input and displays the conversation history.
