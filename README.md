# Listening Learning App

A Python application for processing and analyzing JLPT listening comprehension questions, with features for YouTube transcript handling and semantic search capabilities.

## Features

- Extract and process JLPT listening comprehension questions
- Download and save YouTube video transcripts
- Vector-based semantic search for similar questions
- Support for JLPT sections 2 and 3 question types
- Embeddings using Ollama's DeepSeek model
- Persistent vector storage using ChromaDB

## Prerequisites

- Python 3.12 or higher
- Ollama with DeepSeek model installed
- Internet connection for YouTube transcript downloads

## Installation

1. Clone the repository:
```bash
git clone [your-repo-url]
cd listening-learning-app
```

2. Create and activate a virtual environment:
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install .
```

## Project Structure

- `vector_store.py`: Handles vector storage and retrieval of questions using ChromaDB
- `chat.py`: Implements chat functionality using the DeepSeek model
- `transcriber.py`: Manages YouTube transcript downloads and processing
- `structured_data.py`: Processes and structures Japanese language learning content

## Usage

### Working with YouTube Transcripts

```python
from transcriber import YoutubeTranscriptService

service = YoutubeTranscriptService()
video_url = "https://www.youtube.com/watch?v=your_video_id"
service.download_video(video_url)
```

### Using the Vector Store

```python
from vector_store import QuestionVectorStore

# Initialize the vector store
store = QuestionVectorStore()

# Search for similar questions
results = store.search_similar_questions(
    section_num=2,
    query="your search query",
    n_results=5
)
```

### Chat Functionality

```python
from chat import DeepSeekChat

chat = DeepSeekChat()
response = chat.generate_response("your message")
```

## Dependencies

- boto3 >= 1.36.24
- chromadb >= 0.6.3
- ollama >= 0.4.7
- streamlit >= 1.42.1
- youtube-transcript-api >= 0.6.3

## Project Structure

```
listening-learning-app/
├── README.md
├── pyproject.toml
├── vector_store.py
├── chat.py
├── transcriber.py
├── structured_data.py
└── .gitignore
```
