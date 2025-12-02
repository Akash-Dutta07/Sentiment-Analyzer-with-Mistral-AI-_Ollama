# 🧠 Sentiment Analyzer with Mistral AI
<img width="1024" height="400" alt="Image" src="https://github.com/user-attachments/assets/112d7fc6-4de6-4182-b722-459348eea44d" />

A modern sentiment analysis application built with **FastAPI**, **Ollama**, and **Streamlit** that analyzes text sentiment using the Mistral AI model running locally.

## 🌟 Features

- **🔐 No API Keys Required**: Completely local AI processing with Ollama (no `.env` files needed!)
- **🏠 100% Local Processing**: Uses Ollama to run Mistral AI model locally on your machine
- **⚡ Real-time Analysis**: Instant sentiment analysis with color-coded results
- **🎨 Modern UI**: Clean, responsive Streamlit interface with custom styling
- **🔌 REST API**: FastAPI backend with automatic documentation
- **🛡️ Privacy First**: Zero external API calls - all data stays on your machine

## 🏗️ Architecture

```
┌─────────────────┐    HTTP    ┌─────────────────┐    API     ┌─────────────────┐
│   Streamlit     │   ────→    │    FastAPI      │   ────→    │     Ollama      │
│   Frontend      │            │    Backend      │            │   (Mistral AI)  │
│  (Port 8501)    │            │  (Port 8000)    │            │  (Port 11434)   │
└─────────────────┘            └─────────────────┘            └─────────────────┘
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- [Ollama](https://ollama.ai/) installed
- [UV](https://docs.astral.sh/uv/) package manager (recommended) or pip

> **🔑 No API Keys Needed!** This project uses only local LLM processing via Ollama - no `.env` file, no external API keys, no internet required for inference!

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd mistral-sentiments
   ```

2. **Install dependencies**
   ```bash
   uv sync
   ```
   *Or with pip:*
   ```bash
   pip install -r requirements.txt
   ```

3. **Install and setup Ollama**
   - Download and install [Ollama](https://ollama.ai/)
   - Pull the Mistral model:
   ```bash
   ollama pull mistral
   ```

### Running the Application

1. **Start Ollama** (if not running as service):
   ```bash
   ollama serve
   ```

2. **Start the FastAPI backend** (Terminal 1):
   ```bash
   cd backend
   uvicorn main:app --reload --host 0.0.0.0 --port 8000
   ```

3. **Start the Streamlit frontend** (Terminal 2):
   ```bash
   cd frontend
   streamlit run app.py
   ```

4. **Access the application**:
   - Frontend: http://localhost:8501
   - API Documentation: http://localhost:8000/docs

## 📖 Usage

1. Open the Streamlit app in your browser
2. Enter any text in the input field
3. Click "Analyze" to get sentiment analysis
4. Results are color-coded:
   - 🟢 **Green**: Positive sentiment
   - 🔴 **Red**: Negative sentiment  
   - 🟡 **Yellow**: Neutral sentiment

## 🛠️ API Endpoints

### POST `/analyze/`
Analyze sentiment of provided text.

**Request:**
```bash
curl -X POST "http://localhost:8000/analyze/" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "text=I love this project!"
```

**Response:**
```json
{
  "sentiment": "Positive"
}
```

## 📁 Project Structure

```
mistral-sentiments/
├── README.md
├── pyproject.toml
├── requirements.txt
├── main.py                 # Root entry point
├── backend/
│   ├── main.py            # FastAPI application
│   └── __pycache__/
├── frontend/
│   ├── app.py             # Streamlit application
│   └── __pycache__/
└── __pycache__/
```

## 🔧 Configuration

### Backend Configuration
- **Host**: `0.0.0.0` (configurable)
- **Port**: `8000` (configurable)
- **Ollama URL**: `http://localhost:11434`

### Frontend Configuration
- **Backend URL**: `http://localhost:8000`
- **Theme**: Dark mode with custom styling

## 🐛 Troubleshooting

### Common Issues

1. **Ollama Connection Error**
   - Ensure Ollama is running: `ollama serve`
   - Check if Mistral model is installed: `ollama list`
   - Install if missing: `ollama pull mistral`

2. **Backend Connection Error**
   - Verify FastAPI is running on port 8000
   - Check if port is already in use
   - Try different port: `uvicorn main:app --port 8001`

3. **Module Import Errors**
   - Run from correct directory
   - Use: `uvicorn backend.main:app --reload` (from root)
   - Or: `cd backend && uvicorn main:app --reload`

## 📊 Performance

- **Model**: Mistral 7B (locally hosted)
- **Response Time**: ~2-5 seconds per analysis
- **Memory Usage**: ~4-8GB RAM (depending on model)
- **Concurrent Requests**: Supports multiple simultaneous analyses

## 🔒 Privacy & Security

- **🏠 Fully Offline**: No external API calls or internet connectivity required
- **🔐 No Credentials**: Zero API keys, tokens, or `.env` configuration files needed
- **🛡️ Data Privacy**: Your text never leaves your local machine
- **💰 Cost-Free**: No per-request charges or usage limits

**Built with using FastAPI, Ollama, and Streamlit**
