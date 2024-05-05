# RAG-App-Using-a-LLM


# RAG-App-Using-a-LLM


this is very good resource for Get the Weaviate API key & Endpoint​

https://orkes.io/content/integrations/vector-databases/weaviate


Local embedding and LLM models I am most familiar with the LangChain LLM framework, so we will be using it to ingest documents as well as retrieve them. We will be using sentence_transformers/all-mpnet-base-v2 embedding model and zephyr-7b-alpha llm. Both of these models are open source and available on HuggingFace. The implementation code for these two models in LangChain was kindly borrowed from the following repository:

https://github.com/aigeek0x0/zephyr-7b-alpha-langchain-chatbot


Ingest HubermanLabs podcasts into Weaviate
I have learned that each channel on YouTube has an RSS feed, that can be used to fetch links to the latest 10 videos. As the RSS feed returns a XML, we need to employ a simple Python script to extract the links.

After that we have the links to the videos at hand, we can use the YoutubeLoader from LangChain to retrieve the captions. Next, as with most RAG ingestions pipelines, we have to chunk the text into smaller pieces before ingestion. We can use the text splitter functionality that is built into LangChain.

