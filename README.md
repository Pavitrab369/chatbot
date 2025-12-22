# Streamlit Groq Chatbot

A minimal Streamlit chat app that talks to Groq's hosted Llama models. It keeps a running conversation history and replies using `llama-3.3-70b-versatile` with a helpful-assistant system prompt.

## Features

- Streamlit chat UI with message history
- Groq LLM backend via `langchain-groq`
- Environment-driven credentials with `.env`
- Lightweight dependency set for quick starts

## Requirements

- Python 3.10+ recommended
- Groq API key (`GROQ_API_KEY`)

## Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Copy the sample environment file and add your key:
   ```bash
   cp sample.env .env
   # edit .env to set GROQ_API_KEY
   ```
3. (Optional) Use a virtual environment before installing packages.

## Run the app

```bash
streamlit run chatbot.py
```

Then open the URL that Streamlit prints (usually http://localhost:8501).

## How it works

- [`chatbot.py`](chatbot.py) builds the Streamlit page, keeps `st.session_state.chat_history`, and renders past messages.
- `ChatGroq` is initialized with the `llama-3.3-70b-versatile` model and temperature `0.0`.
- On each prompt, the chat history (plus a system message) is sent to the model, the reply is appended to history, and both sides are rendered.

## Project layout

- [`chatbot.py`](chatbot.py): Streamlit app entrypoint
- [`requirements.txt`](requirements.txt): Python dependencies
- [`sample.env`](sample.env): Example environment variables
- [`flow.txt`](flow.txt): High-level interaction flow notes
- `langchain_chatbot.ipynb`, `llamaindex_chatbot.ipynb`: Experiment notebooks

## Notes

- Keep your `.env` out of version control.
- The sample `main.py` is PyCharm starter code and not used by the Streamlit app.
- Adjust the `model` or temperature in `chatbot.py` if you want a different Groq model or style.
