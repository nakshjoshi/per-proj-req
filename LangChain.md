- powering the already made LLM
- Supports js and python(more detailed doc available)
- it is a framework not library

### LangChain
- give context to LLMs

issue: you cant send question and document/image/anything to question on everytime to the LLM(token limits)

soln: take the whole text out of it ,  break it into chunks, find most relative chunk to user query, send the question plus most relative chunk to llm

these chunking, embedding and retrieval is already automated in langchain; but before langchain we did it separately write our own chunkkng fashion code, embedding it to vector dB and queryinh the vector DB code


what is langchain : Framework to build LLM apps easily

ChatGPT is just an Application internally it calls the OpenAI API, which uses an LLM like GPT-3.5 or GPT-4. ChatGPT is NOT the LLM — it's an application that uses LLMs, GPT-3.5 or GPT-4 are the actual Large Language Models

businesses want to build LLM-based applications that, **Use their own data, Can be customized to their needs and services or department based, Are cheaper to use with input and output in any possibel format, Can integrate multiple LLMs (not just OpenAI)


LangChain is a framework that, Lets you plug in OpenAI, Gemini, HuggingFace models, or any other LLM, Supports integrations with Google Search, Youtube Search, Wikipedia, custom/local/private databases queries, makes your code modular and reusable

#### LLM Chains: 
    Chain = LLM + Prompt

Using OpenAI with LangChain, importing LLM
```from langchain.llms import OpenAI```
Temp. Settings: 
    0 → conservative, safe, 
    1 → creative, risky

#### Embedding
Embeddings: We can convert each paragraph into an embedding — a numeric vector. This vector captures the meaning of the paragraph.
Libraries:  Word2Vec, Doc2Vec, BERT — anything that gives semantic vectors.


### System Design of Sample App using Langchain

1. Upload PDF: Store it in cloud like AWS S3 Bucket

2. Load the document: Use a document loader to bring it into the system
3. Chunk the PDF or any doc you upload

4. Generate Embeddings: Send each chunk to an embedding model
5. Store Embeddings: Store them in a special type of database called Vector DC like FAISS, Chroma, Pinecone
6. User Asks a Query: Convert query into embedding then -->

7. Find Matching Chunks: Compare query vector with all vectorsand Pick up top N/K similar vectors (closest distance, cosine similarity)

8. Final Processing: Combine the user query + these pages --> system query



## About Chains in LangChain
They allow you to combine LLMs and prompts in a sequence. An LLMChain is the simplest type of chain. It takes a prompt, formats it with user input, and sends it to the LLM.

    Sequential Chains:
    Used to perform a sequence of tasks where the output of one step becomes the input for the next.

