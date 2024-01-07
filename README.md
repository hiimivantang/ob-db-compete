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

