# ⚡ YouTube Transcript Summarizer

---

## 🚀 What It Does

Paste any YouTube URL → get a clean, structured summary in seconds.

The app extracts the video transcript, feeds it to an AI model of your choice, and generates a professional Markdown summary with:

- 📝 **Executive Summary** — 2-3 sentence core message
- 🔑 **Key Takeaways** — bullet-point insights
- 🚀 **Action Items** — what to do next

No manual reading. No scrubbing through videos. Just the information you need.

---

## ✨ Features

| Feature                    | Details                                                            |
| -------------------------- | ------------------------------------------------------------------ |
| 🏠**Local Mode**     | Run 100% offline using Ollama — no data leaves your machine       |
| ☁️**Cloud Mode**   | Use Google Gemini API for blazing-fast summaries (~5-10 seconds)   |
| 📡**Live Streaming** | Watch the summary generate in real time                            |
| 🤖**Multi-Model**    | Switch between Llama, Gemma, Qwen, TinyLlama, Gemini 2.5, and more |
| 📊**Analytics**      | Detailed performance stats — processing time, word count, speed   |
| 💾**Export**         | Download summary as`.md` or transcript as `.txt`               |
| 🎨**Premium UI**     | Dark glassmorphic design with gradient styling                     |

---

## 🖥️ Demo

> Summarize a 15-minute video in seconds with Gemini, or run fully offline with a local model.

**Stats & Diagnostics Tab:**

- Transcript word count
- Summary word count
- Reading time saved %
- Total processing time

### 🖥️ Live Demo: https://youtubetranscriptsummarizer-45ueappeladrsdbcemgwgp.streamlit.app/

---

## 🛠️ Installation

### Prerequisites

- Python 3.10+
- [Git](https://git-scm.com/)
- [Ollama](https://ollama.com) *(for local mode)*
- Google AI Studio API Key *(for Gemini cloud mode)*

### 1. Clone the repository

```bash
git clone https://github.com/MuhammadAsad29/youtube-transcript-summarizer.git
cd youtube-transcript-summarizer
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

**Activate it:**

- Windows: `.venv\Scripts\activate`
- macOS/Linux: `source .venv/bin/activate`

### 3. Install dependencies

```bash
python -m pip install streamlit yt-dlp youtube-transcript-api ollama google-genai
```

### 4. (Local Mode) Pull an Ollama model

```bash
ollama pull llama3.2:1b      # Fastest recommended
ollama pull gemma2:2b        # Best quality/speed balance
ollama pull qwen2.5:0.5b     # Ultra lightweight
```

### 5. Run the app

```bash
python -m streamlit run app.py
```

Or on Windows, double-click **`run.bat`**.

---

## 📖 Usage

### Local Ollama Mode

1. Make sure Ollama is running in the background
2. Open the app → sidebar shows **● Ollama Connected**
3. Select **🏠 Local Ollama** backend
4. Choose your model from the dropdown
5. Paste a YouTube URL → click **⚡ Summarize Video**

### Gemini Cloud Mode *(Recommended for speed)*

1. Get a **free** API key at [aistudio.google.com](https://aistudio.google.com/app/apikey)
2. Open the app → select **✨ Gemini Cloud API** backend
3. Paste your API key in the sidebar
4. The model dropdown will auto-populate with all models on your key
5. Paste a YouTube URL → click **⚡ Summarize Video**

> **Free tier:** 1,500 requests/day — no credit card required.

---

## 🤖 Supported Models

### Local (via Ollama)

| Model            | Size   | Speed               | Quality  |
| ---------------- | ------ | ------------------- | -------- |
| `llama3.2:1b`  | 1.3 GB | ⚡⚡⚡ Very Fast    | ⭐⭐⭐   |
| `gemma2:2b`    | 1.6 GB | ⚡⚡ Fast           | ⭐⭐⭐⭐ |
| `qwen2.5:0.5b` | 400 MB | ⚡⚡⚡⚡ Ultra Fast | ⭐⭐     |
| `tinyllama`    | 638 MB | ⚡⚡⚡ Very Fast    | ⭐⭐     |
| `llama3.2:3b`  | 2.0 GB | ⚡ Slow on CPU      | ⭐⭐⭐⭐ |

### Cloud (via Gemini API)

| Model                     | Speed    | Quality    |
| ------------------------- | -------- | ---------- |
| `gemini-3.5-flash-lite` | ⚡⚡⚡⚡ | ⭐⭐⭐⭐⭐ |
| `gemini-3.1-flash`      | ⚡⚡⚡   | ⭐⭐⭐⭐   |
| `gemini-3.1-flash-lite` | ⚡⚡⚡⚡ | ⭐⭐⭐⭐   |

---

## 📁 Project Structure

```
youtube-transcript-summarizer/
│
├── app.py                  # Main Streamlit UI & pipeline orchestration
├── summarizer.py           # Local Ollama summarization (map-reduce chunking)
├── gemini_summarizer.py    # Google Gemini cloud summarization
├── transcript_extractor.py # YouTube transcript & metadata extraction
├── run.bat                 # One-click launcher for Windows
└── requirements.txt        # Python dependencies
```

---

## ⚙️ How It Works

```
YouTube URL
    │
    ▼
┌─────────────────────────┐
│ Transcript Extraction   │  youtube-transcript-api / yt-dlp fallback
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Backend Selection      │
│  ┌──────────┐           │
│  │  Ollama  │ Local CPU │  map-reduce chunking for long videos
│  └──────────┘           │
│  ┌──────────┐           │
│  │  Gemini  │ Cloud API │  single-pass (handles 1M token context)
│  └──────────┘           │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Structured Summary     │  Executive Summary + Key Takeaways + Action Items
└─────────────────────────┘
```

---

## 🔑 Environment & Privacy

- **Local mode:** Transcript text stays entirely on your machine. Nothing is sent externally.
- **Gemini mode:** Transcript text is sent to Google's Gemini API. Governed by [Google&#39;s privacy policy](https://policies.google.com/privacy).

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<div align="center">
Made with ❤️ using Streamlit, Ollama & Google Gemini
</div>
