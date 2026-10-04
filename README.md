# Moroccan Macroeconomic RAG Pipeline (`rag_macro_maroc`)

An end-to-end conversational Retrieval-Augmented Generation (RAG) system built to parse, index, and query structured and unstructured institutional economic data from Morocco (Bank Al-Maghrib, High Commission for Planning / HCP, DEPF, and academic economic literature).

---

## Technical Overview

- **Multi-Format Data Ingestion**: Extracts text page-by-page from PDFs (`BAM`, `HCP`, `PAPERS`) while preserving page-level metadata. Converts multi-sheet Excel files (`DEPF`) into clean Markdown tables to maintain tabular semantics.
- **Contextual Query Rewriting**: Utilizes a dialogue-history-aware rewriter to reformulate ambiguous follow-up questions into standalone retrieval queries.
- **Strict Anti-Hallucination Grounding**: Enforces constrained system prompts restricting `llama3.2` to respond strictly from retrieved context or explicitly state missing information.
- **Privacy-Preserving & Fully Local**: Operates entirely on local infrastructure using Ollama and FAISS—ensuring complete privacy for financial data.

---

## Technical Stack

- **Framework**: LangChain (LCEL)
- **LLM Engine**: Local `llama3.2` (via ChatOllama)
- **Embeddings**: Local `nomic-embed-text`
- **Vector Store**: FAISS
- **Document Parsing**: PyMuPDF, Pandas

---

## Quickstart & Execution Guide

1. Model Setup (Ollama):
   ollama pull llama3.2
   ollama pull nomic-embed-text

2. Repository & Environment Setup:
   git clone https://github.com/votre-nom-utilisateur/rag_macro_maroc.git
   cd rag_macro_maroc
   python3 -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt

3. Pipeline Execution:
   Place source documents in the corresponding data/ subdirectories (BAM, DEPF, HCP, PAPERS), then run:
   jupyter notebook notebooks/code.ipynb

---

## Author

**Doha Harrar**  
Applied Economics, Statistics & Big Data Engineering  
*Institut National de Statistique et d'Économie Appliquée (INSEA)*, Rabat
