# RAG Pipeline for Document Retrieval

I built this to understand how RAG actually works under the hood, not just call a library. I used financial and legal PDFs as test documents because they are dense and hard to parse, which made it a good real test.

## What I built

The core pipeline uses LlamaIndex to index PDFs and Gemini 2.0 Flash to answer questions from them. I kept improving it from there.

I added query expansion where the LLM rewrites your question in a few different ways before searching. This made a big difference on vague or domain-specific queries that would otherwise miss relevant content.

I also built a hybrid retriever that combines dense vector search with BM25 keyword search, then merges results using Reciprocal Rank Fusion. A cross-encoder reranker runs after that to score and reorder the top results before anything goes to the LLM.

## Other things in this folder

- Experiments comparing different retrieval setups at different top-K values
- A Gradio chatbot that wraps the full pipeline so you can interact with it

## Run the notebooks directly

Click any badge below to open that notebook in Google Colab and run it right away.

| Notebook | Open |
|----------|------|
| Build and Optimize a RAG Pipeline | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/prijal21/RAG_PipeLine/blob/main/Build%20and%20Optimize%20a%20RAG%20Pipeline%20for%20Document%20Retrieval.ipynb) |
| Different RAG Pipeline | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/prijal21/RAG_PipeLine/blob/main/Different%20RAG%20PipeLine.ipynb) |
| Query Expansion and Retrieval | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/prijal21/RAG_PipeLine/blob/main/Query%20Expansion%20%26%20Retrieval%20Methods%20for%20Query.ipynb) |
| Advanced PDF Retrieval with LlamaIndex | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/prijal21/RAG_PipeLine/blob/main/Experimenting%20Advanced%20PDF%20Retrieval%20%26%20Optimization%20with%20LlamaIndex.ipynb) |
| Chatbot | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/prijal21/RAG_PipeLine/blob/main/Chatbot.ipynb) |

## How to run

1. Click any badge above to open it in Colab
2. In Colab, click the key icon on the left sidebar and add a secret named `GOOGLE_API_KEY` with your Gemini API key
3. Run all cells from top to bottom

You can get a free Gemini API key at [aistudio.google.com](https://aistudio.google.com).

Start with `Build and Optimize a RAG Pipeline` to see the full pipeline, or open `Chatbot.ipynb` if you just want to try the chat interface directly.

## Stack
Python, LlamaIndex, PyMuPDF, Gemini 2.0 Flash, BM25, HuggingFace Sentence Transformers, Gradio
