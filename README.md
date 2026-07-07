# 🤖 Semantic FAQ Bot

A lightweight, embedding-based FAQ chatbot built with **Sentence Transformers** and **cosine similarity**. Unlike a keyword-matching bot, it understands the *meaning* of a question — so it can correctly match abbreviations, paraphrases, and casually-worded queries to the right FAQ entry.

| User asks | Bot matches |
|---|---|
| `"ML"` | *What is Machine Learning?* |
| `"NLP Stands for?"` | *What is NLP?* |
| `"What is RAG in Computer Science?"` | *What is RAG?* |

##  Features

- **Semantic search** — matches questions by meaning, not just exact keywords, using the `all-MiniLM-L6-v2` Sentence Transformer.
- **Confidence scoring** — every answer is returned with a similarity score; low-confidence matches are flagged instead of returning a wrong answer.
- **Pre-computed embeddings** — the FAQ knowledge base is encoded once and cached, keeping lookups fast.
- **~90 built-in FAQ entries** covering Python fundamentals, data science, machine learning, and popular AI/ML tools.
- **Easily extensible** — swap the in-memory list for a CSV/JSON file, a database, or a vector store like FAISS.

##  How it works

1. Every FAQ question is converted into a 384-dimensional vector embedding.
2. The user's query is embedded using the same model.
3. Cosine similarity is computed between the query and every FAQ question.
4. The answer linked to the highest-scoring question is returned, along with a confidence score.

##  Tech Stack

- [`sentence-transformers`](https://www.sbert.net/) (`all-MiniLM-L6-v2`)
- `scikit-learn` (cosine similarity)
- `numpy`



### Usage

Open `semantic_faq_bot.ipynb` in Jupyter or VS Code and run all cells. The last cell starts an
interactive loop where you can type your own questions:

```
You: ML
Question       : ML
Matched Question: What is Machine Learning?
Match Score     : 0.306
Answer          : Machine Learning is a field of AI where computers learn patterns from data.

You: what's the weather today?
Question       : what's the weather today?
Matched Question: -
Match Score     : 0.104
Answer          : Sorry, I don't have an answer for that. Could you rephrase your question?
```

Type `exit` or `quit` to stop the chat loop.

## 📂 Project Structure

```
semantic-faq-bot/
├── semantic_faq_bot.ipynb   # Main notebook: model, FAQ data, bot class, demo
├── requirements.txt         # Python dependencies
└── priject.md
```

## 🔭 Roadmap / Ideas for Extension

- Load the FAQ dataset from a CSV/JSON file or database instead of hard-coding it.
- Swap brute-force cosine similarity for **FAISS** or a vector database (Pinecone, Chroma, Weaviate) for large-scale search.
- Wrap the bot in a **Flask**/**FastAPI** API or a **Streamlit**/**Gradio** UI.
- Combine with an LLM in a Retrieval-Augmented Generation (RAG) pipeline for more natural, conversational answers.

 If you found this useful, consider starring the repo!
