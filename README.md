# 🔍 RAG Pipeline for Document Retrieval

So this project started because I wanted to actually understand how RAG works, not just use a library that does it for me. I picked financial and legal PDFs as the test documents because they're dense and tricky — good stress test.

## 🛠️ What I built

The core is a pipeline using LlamaIndex + Gemini 2.0 Flash that reads PDFs and answers questions from them. But I kept pushing it further.

One thing I tried was **query expansion** — basically asking the LLM to rewrite your question in 3-4 different ways before searching. It sounds simple but it made a huge difference for vague or domain-heavy questions.

Then I built a **hybrid retriever** that combines two search methods: dense vector search (semantic) and BM25 (keyword). The results get merged using Reciprocal Rank Fusion. After that, a cross-encoder reranks the top results before anything goes to the LLM. More steps, but better answers.

## 📂 Notebooks

- `Build and Optimize a RAG Pipeline for Document Retrieval.ipynb` — start here
- `Different RAG PipeLine.ipynb` — comparing different approaches side by side
- `Query Expansion & Retrieval Methods for Query.ipynb` — the query expansion experiments
- `Experimenting Advanced PDF Retrieval & Optimization with LlamaIndex.ipynb` — hybrid retrieval + reranking
- `Chatbot.ipynb` — a Gradio chatbot that wraps the whole pipeline

## 🚀 Try it yourself

Everything runs on Google Colab, nothing to install.

1. Open any notebook in Colab
2. Click the 🔑 key icon on the left sidebar → add a secret called `GOOGLE_API_KEY`
3. Paste your Gemini API key there
4. Run all cells top to bottom

> Get a free Gemini API key at [aistudio.google.com](https://aistudio.google.com)

Start with `Build and Optimize...` for the full pipeline or jump straight to `Chatbot.ipynb` if you just want to try the chat interface.

## ⚙️ Stack
Python · LlamaIndex · PyMuPDF · Gemini 2.0 Flash · BM25 · HuggingFace · Gradio
