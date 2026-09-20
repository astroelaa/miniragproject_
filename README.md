# Mini RAG Project

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/astroelaa/mini-rag-project/blob/main/mini_rag_project.ipynb)

A lightweight Retrieval-Augmented Generation (RAG) pipeline designed to extract knowledge from PDF documents and answer questions using local open-source models. 

## Overview
This notebook demonstrates a complete RAG workflow:
1. **Document Ingestion**: Reads and cleans text from `Savov_Notes.pdf` using `pypdf`[cite: 6].
2. **Text Chunking**: Splits the extracted text into chunks of 900 characters with a 150-character overlap using LangChain's `RecursiveCharacterTextSplitter`[cite: 6].
3. **Embeddings & Vector Storage**: Generates document embeddings with `all-MiniLM-L6-v2` and stores them in an ephemeral ChromaDB collection for fast semantic search[cite: 6].
4. **Contextual Generation**: Retrieves relevant text chunks based on user queries and generates answers using the `google/flan-t5-base` model[cite: 6]. 

## Safety and Hallucination Prevention
The generation model is guided by a strict prompt template that forces it to rely *only* on the retrieved context[cite: 6]. If an off-topic question is asked (e.g., "what's the weather in Cairo today"), the pipeline is designed to safely respond with: *"I don't have enough information in the provided documents."*[cite: 6].

## Requirements
The notebook automatically installs the necessary dependencies in the first cell[cite: 6]:
- `langchain-text-splitters`
- `sentence-transformers`
- `transformers`
- `chromadb`
- `pypdf`

## How to Use
1. Click the **Open in Colab** badge above to launch the notebook.
2. Run the top cells to install dependencies and import libraries.
3. When the upload cell runs, upload your `Savov_Notes.pdf` file[cite: 6].
4. Run the remaining cells to build the vector database and test the generation model against the predefined linear algebra questions[cite: 6].
