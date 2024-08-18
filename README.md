# LangChain-NLP-CS-Chatbot
This repository implements a chatbot for NLP and Computer Science queries using LangChain. It integrates document retrieval, relevance checking, and decision routing to provide precise, context-aware responses. The project covers embedding creation, search engine integration, and fallback mechanisms.


## Table of Contents

- [Introduction](#introduction)
- [Assignment Overview](#assignment-overview)
- [Dataset](#dataset)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Architecture](#architecture)
- [Results and Analysis](#results-and-analysis)
- [Report](#report)
- [License](#license)

## Introduction

This project involves building an advanced chatbot capable of understanding and processing queries related to NLP and Computer Science. The chatbot is built using the LangChain library and integrates multiple retrieval methods, a relevance checker, and fallback mechanisms to ensure comprehensive and accurate responses.

## Assignment Overview

### Part 1: Data Collection and Preparation

1. **Collecting Content from Jurafsky's Book:**
   - Extract all URLs and chapter content from Jurafsky’s book using the provided link: [Jurafsky's Book](https://stanford.edu/~jurafsky/slp3/).
   - Format the content using PDFLoader and chunk it using `RecursiveCharacterTextSplitter`.

### Part 2: Embeddings and Vector Database

2. **Creating CacheBackedEmbeddings:**
   - Embed the documents from Jurafsky’s book into a vector database to facilitate efficient retrieval.

### Part 3: Retrieval and Routing

3. **Implementing Semantic and Lexical Retrievers:**
   - Combine a `BM25Retriever` for lexical retrieval and `FAISS` for semantic retrieval using an `EnsembleRetriever` to enhance document retrieval accuracy.
4. **Router Chain with LLaMA-3-70B-chat-hf:**
   - Implement a router chain using `LLaMA-3-70B-chat-hf` to determine whether a given prompt is related to NLP or Computer Science to decide the appropriate processing route.

### Part 4: Search Engine and Relevance Checking

5. **Implementing Search Engine:**
   - Retrieve the top 5 relevant documents using the Tavliy API.
6. **Relevancy Checker with LLaMA-3-70B-chat-hf:**
   - Implement a relevancy checker to determine whether the documents from the vector database (chunks from Jurafsky’s book) or the documents from the search engine are relevant to the user’s query.

### Part 5: Fallback Mechanism and Visualization

7. **Fallback Chain with LLaMA-3-70B-chat-hf:**
   - Implement a fallback chain to handle prompts that do not match the content in the vector store or search engine, informing the user of the chatbot's limitations.
8. **Graph Visualization:**
   - Prepare and visualize the workflow graph using `LANGGRAPH` for better understanding and debugging.

## Dataset

- **Source:** The content for the chatbot is sourced from Jurafsky's book chapters, which is publicly available [here](https://stanford.edu/~jurafsky/slp3/).

## Prerequisites

Before you begin, ensure you have the following installed:
- Libraries: `LangChain`, `FAISS`, `BM25`, `torch`, `tavliy`, `LANGGRAPH`
- Basic understanding of NLP, embeddings, and chatbot development.

## Installation

Clone this repository and install the required dependencies:
```sh
git clone https://github.com/PouyaGohari/LangChain-NLP-CS-Chatbot.git
cd LangChain-NLP-CS-Chatbot

!pip install -qU langchain\
    langchain-community\
    langchain-together\
    langchain-core\
    faiss-cpu\
    faiss-gpu\
    langgraph\
    sentence-transformers\
    gradio\
    pypdf\
    unstructured\
    pdfminer\
    rank_bm25
```

## Usage

This project is implemented in a single Jupyter notebook:

- **Notebook:** [`CA_FINAL.ipynb`](FINAL_CA.ipynb)

To run the project:

1. Open the `CA_FINAL.ipynb` notebook.
2. Follow the instructions to:
   - Extract and chunk content from Jurafsky’s book.
   - Create embeddings and set up the vector database.
   - Implement and test the semantic and lexical retrievers.
   - Set up the router chain, search engine, and relevancy checker.
   - Implement the fallback mechanism.
   - Visualize the chatbot’s workflow using LANGGRAPH.

## Architecture

The chatbot’s architecture involves several key components:

- **VectorStore:** Stores and retrieves embedded document chunks.
- **Search Engine:** Retrieves documents using the Tavliy API.
- **Relevancy Checker:** Determines the relevance of documents from both the vector store and search engine.
- **Router Chain:** Uses `LLaMA-3-70B-chat-hf` to route queries based on their content.
- **Fallback Chain:** Handles prompts that are outside the scope of the available content.


## Results and Analysis

- **Retrieval Performance:** Analysis of the effectiveness of combining semantic and lexical retrieval methods.
- **Relevancy Checking:** Evaluation of the accuracy of the relevancy checker in distinguishing between relevant and non-relevant documents.
- **Fallback Handling:** Insights into how effectively the fallback chain manages out-of-scope queries.

## Report

A comprehensive report detailing the research, methodology, implementation, results, and analysis for each part of the assignment is available [here](FINAL_CA_NLP.pdf).


## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
