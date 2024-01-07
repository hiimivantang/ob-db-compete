# ob-db-compete

## Data sources used for grounding RAG-based model

1. https://github.com/cockroachdb/docs/tree/main/src/current/v23.2
2. https://github.com/pingcap/docs/tree/release-7.5
3. https://github.com/yugabyte/yugabyte-db/tree/2.18.1.1-b1/docs
4. https://github.com/oceanbase/oceanbase-doc/tree/V4.1.0/en-US

## Stack

* embedding model: BAAI/bge-small-en
* vector search: FAISS 
* retriever: langchain's RetrievalQA 
* autoregressive model: gpt-35-turbo 
* interface: chainlit 
* reverse tunnel: ngrok 


## How to reuse vector store containing embeddings for our compete info

```py
  model_name = "BAAI/bge-small-en"
  encode_kwargs = {'normalize_embeddings': True} # set True to compute cosine similarity
  embeddings = HuggingFaceBgeEmbeddings(model_name=model_name, encode_kwargs=encode_kwargs)

  #load vector store containing embeddings of Azure AI Services documentation.
  vector_store = FAISS.load_local(embeddings=embeddings, folder_path="./ob_vector_store_v3")
  #vector_store = FAISS.load_local(embeddings=embeddings, folder_path="./papers_vector_store_v2")
  retriever = vector_store.as_retriever(search_kwargs={'k': n_documents})
```
