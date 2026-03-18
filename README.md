# Semantic AI Customer Support Chatbot

> An NLP-powered chatbot that understands customer queries using semantic similarity — no predefined intent labels required.

**Course:** Applied Natural Language Processing  
**Team:** Charan Reddy Boojala · Sampath Sai Srinivas Earli · Shriya Reddy Kolan · Nandhakumar Sivakumar

---

##  Overview

Traditional customer support chatbots rely on rigid, rule-based intent classification. This project replaces that approach with a fully semantic pipeline that:

- Understands user queries using **contextual embeddings (Sentence-BERT)**
- Detects **real-time sentiment** to adapt tone
- Generates **natural, human-like responses** using GPT-4o-Mini
- Delivers a smooth **iMessage-style chat UI** built with Streamlit

No predefined labels. No rigid rules. Just semantics.

---

##  Objectives

-  Eliminate dependence on predefined intent labels
-  Use **Sentence-BERT (all-mpnet-base-v2)** for semantic understanding
-  Retrieve similar queries using **cosine similarity**
-  Detect sentiment (positive/negative) using **DistilBERT SST-2**
-  Generate context-aware replies using **GPT-4o-Mini**
-  Build a clean, interactive UI for real-time user interaction
-  Ensure scalability, modularity, and academic clarity

---

##  System Architecture

The system consists of four main components:

```
User Query
    │
    ▼
┌─────────────────────────┐
│  Sentence-BERT (SBERT)  │  → Encodes query into dense vector
└─────────────────────────┘
    │
    ▼
┌─────────────────────────┐
│   Semantic Search Engine │  → Cosine similarity against dataset
│   (Cosine Similarity)   │  → Top matches → "Semantic Intent"
└─────────────────────────┘
    │
    ▼
┌─────────────────────────┐
│   Sentiment Analysis    │  → DistilBERT SST-2
│   (DistilBERT SST-2)    │  → Positive / Negative
└─────────────────────────┘
    │
    ▼
┌─────────────────────────┐
│   GPT Response Generator│  → Uses query + examples + sentiment
│   (GPT-4o-Mini)         │  → Natural, emotionally appropriate reply
└─────────────────────────┘
    │
    ▼
Streamlit Chat UI
```

---

##  Project Structure

```
semantic-ai-chatbot/
│
├── app.py                  # Main Streamlit application
├── semantic_search.py      # SBERT embedding + cosine similarity logic
├── sentiment_analysis.py   # DistilBERT SST-2 sentiment detection
├── response_generator.py   # GPT-4o-Mini response generation
├── data/
│   └── customer_support_dataset.csv   # Preprocessed dataset
├── requirements.txt        # Python dependencies
├── README.md               # Project documentation
└── assets/
    └── screenshots/        # UI screenshots
```

---

## ⚙️ Installation & Setup

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/semantic-ai-chatbot.git
cd semantic-ai-chatbot
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up your OpenAI API Key
Create a `.env` file in the root directory:
```
OPENAI_API_KEY=your_openai_api_key_here
```

### 4. Run the app
```bash
streamlit run app.py
```

---

##  Dataset

The dataset contains real-world customer service interactions including:

- User utterances (customer queries)
- Categories and tags (used for semantic grouping)
- Real-world phrasing variations

**Example queries:**
> *"Would it be possible to cancel the order I made?"*  
> *"I need assistance with canceling my last order"*

Intent labels were intentionally removed — the model infers intent purely through semantic similarity.

---

## 🔍 How It Works

### 1. Semantic Search (SBERT)
All dataset utterances are encoded using `all-mpnet-base-v2`. When a user sends a message, SBERT generates an embedding for it, and cosine similarity identifies the closest matching queries from the dataset.

### 2. Sentiment Analysis
DistilBERT SST-2 detects whether the user's tone is **positive** or **negative**. This influences GPT's response:
- **Negative** → empathetic, reassuring tone
- **Positive** → friendly and direct tone

### 3. Response Generation (GPT-4o-Mini)
GPT receives:
- The user's message
- Retrieved similar examples
- Detected sentiment
- Inferred semantic intent

It returns a natural, grammatically correct, emotionally appropriate reply.

### 4. Streamlit UI
-  Blue iMessage-style bubbles for user messages
-  Grey bubbles for bot responses
-  Intent + sentiment badges on each message
-  Timestamps for every exchange

---

##  Results

| Capability | Status |
|---|---|
| Understands queries without intent labels  |
| Real-time sentiment detection |
| Contextually accurate response generation |
| Handles multiple categories (refunds, delivery, account, etc.) |
| Clean and professional chat interface |

---

## Future Enhancements

-  Multi-turn conversation memory
-  Emotion classification (joy, frustration, anger)
-  Topic clustering
-  Domain-specific fine-tuning
-  RAG-based knowledge grounding

---

##  References

1. **Sentence-BERT** — Reimers & Gurevych (2019). [arxiv.org/abs/1908.10084](https://arxiv.org/abs/1908.10084)
2. **Attention Is All You Need** — Vaswani et al. (2017). [arxiv.org/abs/1706.03762](https://arxiv.org/abs/1706.03762)
3. **DistilBERT** — Sanh et al. (2019). [arxiv.org/abs/1910.01108](https://arxiv.org/abs/1910.01108)
4. **GPT-4o** — OpenAI (2024). [platform.openai.com/docs](https://platform.openai.com/docs/)
5. **Cosine Similarity** — Singhal, A. (2001). IEEE Data Engineering Bulletin.
6. **Hugging Face Transformers** — Wolf et al. (2020). [arxiv.org/abs/1910.03771](https://arxiv.org/abs/1910.03771)
7. **Streamlit** — Streamlit Inc. (2023). [docs.streamlit.io](https://docs.streamlit.io/)

---

##  Team Members

| Name |
|------|
| Charan Reddy Boojala |
| Sampath Sai Srinivas Earli |
| Shriya Reddy Kolan |
| Nandhakumar Sivakumar |

---

> *Built for Applied Natural Language Processing — 2025*
