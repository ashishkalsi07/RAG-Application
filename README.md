# RAG-Application

### Introduction
This Repo  contains all the steps you need to know while working on a RAG application.The technology stack is 
- Python
- Langchain
- Azure
- Azure Cognitive Services (AI Services)

### Architecture
![](https://miro.medium.com/v2/resize:fit:1200/1*fJR078bkFerolF0ji8BmUg.jpeg)

**``We start our project by first uploading all the documents to the Azure Blob storage.``** 
``You can create a container in Blob Storage and do upload your documents.``
``Get the connection string and write a python script which help in data ingestion.``

**Data Ingestion**
Data ingestion is the process of collecting, importing, and processing data from various sources into a storage or processing system where it can be accessed, analyzed, and utilized effectively. In the context of a Retrieval-Augmented Generation (RAG) architecture using Microsoft Azure, data ingestion involves several steps to ensure that raw data from documents is prepared for further processing, analysis, and querying.

``Write a python script to fetch the documents stored in blob storage and lets first extract the data using Document Intelligence.``
 
**Document Intelligence**
``Azure Document Intelligence Service - Microsoft has Document Intelligence earlier[Form Recoginizer] and it has various Document analysis Models[OCR Models], prebuilt models and custom model available for users.``

- **Document Analysis Models**
``There were three models available earlier but now microsoft has finalized two models for now ``**``Read Moded``** and **``Layout Moded.``**
Both Models work on the phenomenon of Optical Character Recognition.For documents like PDF,Docx you can choose layout model and starting extracting out your data. Ideally you will get a JSON object in response from the layout model (depends on the api_version you are using)

``If your JSON file is too large it is recomended to Chunked the JSON file using any of the Chunking strategies, with any framework. Now getting small chunks will increase the quality of data index while querying the Azure indexes.``

![](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/rag/_images/rag-high-level-architecture.png)

``For chunking the json file to get small chunks, please use either``
**``langchain's text splitter``**
**``text_chunker from semantci kernel``**

``Both the frameworks has their own benefits, pros and cons.Select carefully
``

**Embeddings**
Azure Machine Learning Service - Vector embeddings in Azure Index refer to the representation of data objects (such as text, images, or other multimedia content) as vectors in a continuous vector space. Azure Cognitive Search, a service provided by Microsoft Azure, incorporates vector embeddings to enhance search capabilities, particularly in scenarios involving natural language processing (NLP) and semantic search. 

``To create embeddings you can use openAI models like if text embeddings is the use case then`` **``text-embeddings-ada-002``**


- **Indexing**

Azure AI Search Service - Since you have obtained the Chunks with embeded vectors, its time to define a index schema and push your all chunks into blob storage and connect it with index.``
Now here comes the Indexer that we can use to connect the json chunks to index.Run an indexer by following all the steps and you will ended up getting a index where all your chunks are uploaded. Now to verify here, you can ask queries directly to the indexes and observe the response.

If response are as per expectataion, like indexer is referring to the chunks that contain the data regards to your query you can Go ahead

- **Chains**

``Stuff and map_reduce two chains are available for training your LLM with your data.``

- **Application-Frontend/Backend** 
``Create an endpoint and use Flask for handling the backend response.You can choose any framework like DJango, NodeJs.For frontend very easy way will be to you streamlit but if you wants to create a really interactive window then you can choose either REACT, Angular.``

**Conclusion**
**``This documentation provide a way you to start with your RAG application. It does not cover every aspect of application in detail. By following all the steps you can create a plan as per your use case and start working on it.``**

**``For more you can Connect with me.``**
