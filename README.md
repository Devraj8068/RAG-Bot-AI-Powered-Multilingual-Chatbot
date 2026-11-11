# RAG-Bot – AI-Powered Multilingual Chatbot
RAG-Bot is an advanced AI-powered conversational assistant built with a focus on accuracy, multilingual accessibility, and seamless user experience. Unlike generic chatbots, RAG-Bot leverages Retrieval-Augmented Generation (RAG) techniques to ensure company-specific responses, preventing irrelevant or hallucinated answers. Below is a glimpse of its clean and interactive user interface:
<img width="645" height="767" alt="Screenshot 2025-08-24 113851" src="https://github.com/user-attachments/assets/8d880edf-8b86-43a5-b544-341bf8047661" />

Key Features:

🌍 Multilingual Support – Communicates fluently in multiple languages, making it accessible to a diverse global audience.

🎙 Audio Input & Output – Users can interact using voice commands and receive spoken responses, enabling hands-free conversations.

🎨 Beautiful & Sleek UI – Designed with a modern, user-friendly interface for smooth and engaging interactions.

🧠 Powerful LLM Backbone – Utilizes Mistral AI 7B Instruct v0.3 for natural and context-aware responses.

🔍 Context-Aware Retrieval (RAG) – Enhanced with LangChain and All-MiniLM-v6 Sentence Transformer for semantic search, ensuring responses are grounded in company-specific knowledge.

🧭 Easy Navigation – Built-in navigation buttons simplify user flow and improve accessibility.

🏢 Enterprise-Focused – Custom-tuned to handle internal knowledge bases, ensuring secure, reliable, and domain-specific support.

Tech Stack:

LLM: Mistral AI 7B Instruct v0.3

Embeddings: All-MiniLM-v6 Sentence Transformer

Frameworks: LangChain, Retrieval-Augmented Generation (RAG)

UI/UX: Sleek, modern interface with navigation controls

Audio Processing: Speech-to-Text & Text-to-Speech integration

Impact:
RAG-Bot provides organizations with a smart, multilingual, and voice-enabled assistant that not only improves user engagement but also ensures knowledge-grounded, accurate, and company-specific responses. It bridges the gap between AI automation and real-world enterprise usability.

## 🚀 Run locally

```bash
git clone https://github.com/Devraj8068/RAG-Bot-AI-Powered-Multilingual-Chatbot.git
cd RAG-Bot-AI-Powered-Multilingual-Chatbot

python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt

cp .env.example .env            # then add your DeepInfra API key to .env
```

Start the two backend services in separate terminals:

```bash
python app.py               # RAG backend (retrieval + Mistral 7B via DeepInfra)
python language_bridge.py   # translation + text-to-speech bridge
```

Then open `index.html` with a local static server (for example the VS Code **Live Server** extension) to use the chatbot.

The DeepInfra key is read from the `DEEPINFRA_API_KEY` environment variable — never commit it. Get one from [DeepInfra](https://deepinfra.com/dash/api_keys).

### Docker

```bash
docker build -t rag-bot .
docker run -p 5000:5000 --env-file .env rag-bot
```

## 📁 Project structure

| File | Purpose |
| --- | --- |
| `app.py` | Flask RAG backend: chunks and embeds the knowledge base (FAISS), retrieves context, calls the LLM |
| `language_bridge.py` | Flask service for translation (deep-translator) and speech (gTTS) |
| `output1.json` | Knowledge base indexed by the RAG backend |
| `about.json`, `chatbot.json`, `services.json` | Content used by the UI and bridge |
| `index.html`, `script.js`, `style.css` | Chat interface |
