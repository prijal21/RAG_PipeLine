# RAG Pipeline for Document Retrieval

This project is about building a RAG pipeline that can answer questions from financial and legal PDF documents. I started with a basic setup and kept improving it by trying different retrieval methods.

## What I built

The core pipeline uses LlamaIndex to index PDF documents and Gemini 2.0 Flash to generate answers. From there I experimented with a few things to improve retrieval quality.

One thing I tried was query expansion, where the LLM generates a few different versions of the same question before searching. This helped a lot with vague or domain-specific queries that would otherwise miss relevant chunks.

I also built a hybrid retriever that combines dense vector search with BM25 keyword search, then merges the results using Reciprocal Rank Fusion. On top of that I added a cross-encoder reranker to score and reorder the top results before passing them to the LLM.

## Other things in this folder

- Experiments comparing different retrieval setups at various top-K values
- A small Gradio chatbot that wraps the pipeline for interactive use

## Notebooks

- `Build and Optimize a RAG Pipeline for Document Retrieval.ipynb`
- `Different RAG PipeLine.ipynb`
- `Query Expansion & Retrieval Methods for Query.ipynb`
- `Experimenting Advanced PDF Retrieval & Optimization with LlamaIndex.ipynb`
- `Chatbot.ipynb`

## Stack
Python, LlamaIndex, PyMuPDF, Gemini 2.0 Flash, BM25, HuggingFace Sentence Transformers, Gradio
