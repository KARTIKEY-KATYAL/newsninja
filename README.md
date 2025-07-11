<h1 align="center">🥷 NewsNinja</h1>
<p align="center"><b>Stealthy News Aggregator & Audio Briefing Tool</b></p>

---

## Overview

NewsNinja is your personal news ninja: it silently scrapes premium news headlines and live Reddit reactions, then delivers AI-powered audio briefings straight to your ears. No endless scrolling—just the news and sentiment that matter, in seconds.

---

## Features

- 🗞️ Scrape premium news websites (bypassing paywalls)
- 🕵️‍♂️ Extract live Reddit reactions (even from JS-heavy threads)
- 🔊 AI-powered audio summaries (text-to-speech with ElevenLabs)
- ⚡ Real-time updates (Bright Data MCP integration)
- 🧠 LLM-powered summarization (Anthropic Claude, Ollama)
- 🎛️ Streamlit UI for easy topic selection and audio playback

---

## Tech Stack

- **Python 3.11**
- [FastAPI](https://fastapi.tiangolo.com/) (backend API)
- [Streamlit](https://streamlit.io/) (frontend UI)
- [Bright Data MCP](https://brightdata.com/) (browser-based scraping)
- [ElevenLabs](https://elevenlabs.io/) (text-to-speech)
- [Anthropic Claude](https://www.anthropic.com/) (LLM summarization)
- [Ollama](https://ollama.com/) (optional, local LLM summarization)
- [Pydantic](https://docs.pydantic.dev/) (data models)
- [LangChain](https://python.langchain.com/) (LLM orchestration)
- [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/) & [lxml](https://lxml.de/) (HTML parsing)
- [aiolimiter](https://pypi.org/project/aiolimiter/), [tenacity](https://tenacity.readthedocs.io/) (rate limiting, retries)

---

## Setup & Installation

### 1. Clone the Repository
```sh
git clone https://github.com/AIwithhassan/newsninja.git
cd newsninja
```

### 2. Install Dependencies
```sh
pipenv install
pipenv shell
```

### 3. Environment Variables

Copy the example file and fill in your API keys:
```sh
copy .env.example .env  # On Windows
# or
cp .env.example .env    # On Mac/Linux
```

Edit `.env` and add your credentials:
```env
# Bright Data
BRIGHTDATA_MCP_KEY=your_mcp_api_key
BROWSER_AUTH=your_browser_auth_token

# ElevenLabs
ELEVENLABS_API_KEY=your_text_to_speech_key

# Anthropic (Claude)
ANTHROPIC_API_KEY=your_anthropic_api_key

# (Optional) Ollama
OLLAMA_HOST=http://localhost:11434
```

### 4. Bright Data Setup
- Create an MCP zone: https://brightdata.com/cp/zones
- Enable browser authentication
- Copy credentials to your `.env`

---

## Usage

### 1. Start the Backend (API)
```sh
pipenv run python backend.py
```

### 2. Start the Frontend (Streamlit UI)
```sh
pipenv run streamlit run frontend.py
```

### 3. Using the App
- Open the Streamlit UI in your browser (usually at http://localhost:8501)
- Enter a topic (e.g., "Artificial Intelligence")
- Choose data sources (news, Reddit, or both)
- Click "Generate Summary" to get an audio news briefing
- Download or listen to the generated audio

---

## Project Structure

```
.
├── frontend.py          # Streamlit UI
├── backend.py           # FastAPI backend & data processing
├── utils.py             # Utility functions (scraping, summarization, TTS)
├── news_scraper.py      # News scraping logic
├── reddit_scraper.py    # Reddit scraping logic
├── models.py            # Pydantic data models
├── Pipfile              # Dependency management
├── .env.example         # Example environment variables
├── audio/               # Generated audio files
└── README.md            # This file
```

---

## Notes & Tips

- First scrape may take 15-20 seconds (browser emulation is used for Reddit)
- Keep your `.env` file secret—never share your API keys
- For best results, use real API keys for Bright Data, ElevenLabs, and Anthropic
- Ollama is optional for local LLM summarization (see `utils.py`)

---

## Troubleshooting

- **Connection Error:** Ensure both backend and frontend are running, and API keys are correct
- **Bright Data errors:** Check your MCP zone and credentials
- **Audio not playing:** Make sure ElevenLabs API key is valid

---

## Support

- Open an issue: https://github.com/AIwithhassan/newsninja/issues
- Bright Data support: https://brightdata.com/support

---

<p align="center"><i>"In the darkness of information overload, be the ninja."</i> 🌑</p>