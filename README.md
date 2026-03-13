# RAGCore
### RAG Pipeline Module for Document Intelligence

A fully local Retrieval Augmented Generation pipeline built to 
power intelligent document querying, meeting summarisation, 
and research retrieval.

---

## How to integrate into main project

Step 1 — Install dependencies:
pip install -r requirements.txt

Step 2 — Import and use in your backend:

from engine import RAGPipeline

pipeline = RAGPipeline()

# Index a document
pipeline.index("meeting_notes.pdf")

# Query it
result = pipeline.query("What was decided about the budget?")
print(result.answer)
print(result.confidence)

---

## What it does
- Accepts any PDF, TXT or Markdown document
- Breaks it into smart chunks
- Stores chunks in a local ChromaDB vector database
- When queried, finds the most relevant chunks
- Returns an answer with a confidence score

---

## API Response format
Every query returns:
- answer — the extracted answer
- confidence — how confident the model is (0 to 1)
- passages — the source text it used
- sources — which document it came from
- latency_ms — how fast it responded

---

## Models used
- Embedding — all-mpnet-base-v2
- Reranking — ms-marco-MiniLM-L-6-v2
- QA — roberta-base-squad2
- Summarisation — facebook/bart-large-cnn

---

## Run independently
python main.py index document.pdf
python main.py query "What was discussed?"
python main.py summarise meeting_notes.pdf
python main.py chat 
