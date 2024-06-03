# RAG-App-Using-a-LLM

In this project, we leverage Weaviate, a vector database, to power our retrieval-augmented generation (RAG) application. Weaviate enables efficient vector similarity search, which is crucial for building effective RAG systems. Additionally, we use local language model (LLM) and embedding models to ensure privacy and confidentiality of sensitive information.

Here are the key components of our project:

## Weaviate Integration
- Weaviate serves as our vector database. It allows us to ingest and retrieve documents efficiently.
- To connect to Weaviate, you’ll need the Weaviate API key and endpoint. You can find these details in the Weaviate dashboard or configure them programmatically.
   - this is very good resource for Get the Weaviate API key & Endpoint​ (https://orkes.io/content/integrations/vector-databases/weaviate)

## Local Embedding and LLM Models
- I’ve chosen the sentence\_transformers/all-mpnet-base-v2 embedding model and the zephyr-7b-alpha LLM from Hugging Face.
- These models are open source and well-suited for our use case.
- Intended uses for sentence\_transformers/all-mpnet-base-v2
  - this model is intented to be used as a sentence and short paragraph encoder. Given an input text, it ouptuts a vector which captures the semantic information. The sentence vector may be used for information retrieval, clustering or sentence similarity tasks.
  

By default, input text longer than 384 word pieces is truncated.

## Ingesting HubermanLabs Podcasts into Weaviate
- YouTube channels have RSS feeds that provide links to the latest videos,
- This is very useful for knowing how to get RSS feed URLs for Youtube channel or playlist
   (https://www.bing.com/videos/search?q=How+to+Get+an+RSS+Feed+for+a+YouTube+Channel&view=detail&mid=3C95CB71B90D3F8DB6B53C95CB71B90D3F8DB6B5&FORM=VIRE).
- YouTube RSS Feed URLs:
  -  YouTube Channel RSS Feed URL: https://www.youtube.com/feeds/videos.xml?channel_id=&parentCsn=dLFP4Q
  -  YouTube Playlist RSS Feed URL: https://www.youtube.com/feeds/videos.xml?playlist_id=&parentCsn=dLFP4Q
- I can extract these links using a simple Python script.
- After obtaining the video links, I use the YoutubeLoader from LangChain to retrieve captions.
- The text is then chunked into smaller pieces using the text splitter functionality in LangChain.

## Creating a  Chatbot with Gradio
- Gradio is an excellent library for building interactive interfaces for LLMs, including chatbots.
- I’ve created a chatbot using Gradio, which allows users to interact with the model through a user-friendly interface.
- The chatbot responds to user input and displays the conversation history.
  
![Alt Text] https://private-user-images.githubusercontent.com/133686742/276068044-72a42fe5-3a35-44c1-a971-d5f6de6de11d.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTc0MDk5NDUsIm5iZiI6MTcxNzQwOTY0NSwicGF0aCI6Ii8xMzM2ODY3NDIvMjc2MDY4MDQ0LTcyYTQyZmU1LTNhMzUtNDRjMS1hOTcxLWQ1ZjZkZTZkZTExZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNjAzJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDYwM1QxMDE0MDVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iMWZmNzYyMWY2NjJjNDU1ZTRmNjUxNjU3MGUyNWUxZmY2NzRiNzdhODAwYTgwYjZkNDQxYjRiMmI5MTM5MzgyJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.Vqc9Rok1AkaO7lIz7dQoJ2e9PApiMhospJ7e9uBL-sI
