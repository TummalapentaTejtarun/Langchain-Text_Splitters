# Text Splitter Project

This project demonstrates **text splitting techniques** using LangChain, including both **Recursive Character Text Splitter** and **Semantic Chunker**. Text splitting is an essential step in natural language processing pipelines, allowing long documents to be broken into smaller, semantically coherent chunks for embedding, search, or generation tasks.

---

## Features

* **RecursiveCharacterTextSplitter**

  * Splits text based on characters, words, or custom separators.
  * Supports chunk size and overlap for context retention.
  * Ideal for simple splitting based on length.

* **SemanticChunker**

  * Splits text based on **semantic meaning** using OpenAI embeddings.
  * Detects topic shifts automatically to create coherent chunks.
  * Adjustable threshold to control granularity of chunks.

---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
```

2. Install dependencies:

```bash
pip install langchain openai python-dotenv
```

3. Set up your OpenAI API key in a `.env` file:

```
OPENAI_API_KEY=your_openai_api_key
```

---

## Usage

### Recursive Character Text Splitter

```python
from langchain.text_splitter import RecursiveCharacterTextSplitter

text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=500,
    chunk_overlap=50
)

docs = text_splitter.split_text("Your long text here...")
print(docs)
```

### Semantic Chunker

```python
from langchain_experimental.text_splitter import SemanticChunker
from langchain_openai.embeddings import OpenAIEmbeddings
from dotenv import load_dotenv

load_dotenv()

text_splitter = SemanticChunker(
    OpenAIEmbeddings(),
    breakpoint_threshold_type="standard_deviation",
    breakpoint_threshold_amount=3
)

sample_text = "Your long text with multiple topics..."
docs = text_splitter.create_documents([sample_text])
print(len(docs))
print(docs)
```

---

## Key Concepts

* **Embeddings:** Represent sentences as high-dimensional vectors to capture meaning.
* **Semantic Distance:** Measures how different consecutive sentences are.
* **Chunking Threshold:** Determines when a semantic jump is big enough to create a new chunk.
* **Chunk Overlap:** Optional feature to maintain context between chunks.

---

## Applications

* Text preprocessing for **RAG (Retrieval-Augmented Generation)**
* Document summarization
* Semantic search engines
* Topic detection and segmentation

---


