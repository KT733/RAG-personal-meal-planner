# RAG Personal Meal Planner

A recipe-aware meal planning assistant built with **Retrieval-Augmented Generation (RAG)**.  
Instead of relying only on a general-purpose LLM, this project retrieves relevant recipes from a recipe dataset and uses them to generate grounded meal recommendations, answer recipe questions, and improve personalization.

## Why this project

Large language models are fluent, but they often invent recipe details or answer using generic world knowledge instead of the actual dataset. This project explores how **RAG** can make meal planning more reliable by grounding responses in retrieved recipes.

The notebook compares three approaches:

1. **LLM only** – generates answers directly from model knowledge  
2. **Basic RAG** – retrieves recipe documents before generation  
3. **Advanced RAG** – improves retrieval with:
   - **LLM-based recipe labeling** (for cuisine type and estimated cook time)
   - **HyDE query rewriting** to make user prompts easier to retrieve against

The goal is to produce responses that are more **accurate, dataset-specific, and personalized**.

---

## What it does

- Retrieves recipes from a vector database using semantic search
- Answers recipe-specific questions grounded in the dataset
- Generates meal suggestions from retrieved recipes
- Reduces hallucinations for recipes that do not exist in the dataset
- Improves retrieval for vague requests such as cuisine preference or meal intent
- Compares baseline LLM, standard RAG, and advanced RAG behavior

---

## System design

### 1. Recipe embedding and indexing
Recipes are embedded using a domain-specific embedding model:

- **Embedding model:** `DivyaMereddy007/RecipeBert_v5`
- **Vector store:** Pinecone

This allows semantic search over recipe documents rather than relying on exact keyword matching.

### 2. Custom retriever
A custom retriever queries Pinecone and returns the top matching recipe texts.

### 3. Basic RAG pipeline
The standard RAG flow is:

**User query → retrieve relevant recipes → inject context into prompt → generate answer with LLM**

This grounds the model’s output in the recipe dataset.

### 4. Advanced RAG enhancements
The advanced version adds two retrieval improvements:

#### A. Recipe labeling with an LLM
Retrieved recipes are labeled with:
- **Cuisine type**
- **Estimated cook time**

This helps the system better reason over ambiguous prompts like:
- “Give me spicy Asian food for dinner”
- “Recommend something easy and quick”

#### B. HyDE-based query rewriting
The system uses **HyDE (Hypothetical Document Embeddings)** to rewrite the user query into a form that is more retrieval-friendly.

Flow:
- Generate a hypothetical ideal document for the query
- Rewrite the original query using that hypothetical content
- Run RAG using the rewritten prompt

This improves retrieval quality when user prompts are short, vague, or stylistic.

---

## Tech stack

- **Python**
- **LangChain**
- **OpenAI / ChatOpenAI**
- **Pinecone**
- **RecipeBERT** (`DivyaMereddy007/RecipeBert_v5`)
- **dotenv** for API key management
- **Jupyter Notebook** for experimentation

---

## Repository contents

This project is currently implemented as a notebook-based prototype.

```bash
.
├── rag.ipynb        # Main notebook containing the end-to-end RAG pipeline
├── README.md        # Project documentation
└── .env             # API keys (not committed)
