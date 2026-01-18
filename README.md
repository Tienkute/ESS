# ESS - Embeddings Semantic Search 🔍

A semantic search system using **AI and Machine Learning** to retrieve documents based on meaning rather than just keywords.

## 📋 Project Description

This project provides tools to:

- **Semantic Search**: Search based on the meaning of your query, not just keywords
- **Text Encoding**: Convert text into numerical vectors using AI
- **Similarity Comparison**: Use cosine similarity to find the most relevant results
- **API Server**: Provide a REST API for other applications
- **Smart Chat System**: Support natural conversation with query history

## 🎯 Key Features

✅ **Multilingual Support** - Supports Vietnamese and 50+ languages  
✅ **Fast Search** - Uses vector embeddings for speed  
✅ **RESTful API** - Easy to integrate into applications  
✅ **Modular Design** - Clean, maintainable code  
✅ **Interactive Chat** - User-friendly command-line interface

## 📁 Project Structure

```
semantic_search_project/
├── api.py           # FastAPI server for search
├── demo.py          # Basic embedding example
├── search.py        # Semantic search module
├── system.py        # Smart chat system with memory
├── requirements.txt # Required libraries
└── README.md        # This file
```

## 🚀 How to Use

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

**Main Libraries:**
- `fastapi` - Web framework
- `sentence-transformers` - AI model for embeddings
- `scikit-learn` - Cosine similarity calculation
- `numpy` - Numerical computing
- `uvicorn` - ASGI server

### 2. Run Basic Example

```bash
python demo.py
```

Expected output:
```
--- Loading AI model... ---
Success!
Converted 2 sentences into vectors with shape: (2, 384)
Vector of the first sentence (truncated): [-0.05... 0.12... ...]
```

### 3. Run Semantic Search

```bash
python search.py
```

Example:
```
Your question: How do I learn programming?
--> Result found: "How to install Python on Windows"
--> Accuracy: 0.6234 (Higher is better)
```

### 4. Run Smart Chat System

```bash
python system.py
```

The system will:
- Save query history
- Automatically classify queries
- Find relevant documents

Example:
```
You (Enter question): How to cook pho?
[Memory] Saved 1 question in this session.
--> Result: "Traditional Vietnamese Pho recipe"
--> Confidence: 0.7891

You (Enter question): exit
```

### 5. Run API Server

```bash
python -m uvicorn api:app --reload
```

Access:
- **Swagger UI**: http://localhost:8000/docs
- **API Endpoint**: POST http://localhost:8000/search

Example request:
```bash
curl -X POST "http://localhost:8000/search" \
  -H "Content-Type: application/json" \
  -d '{"text": "How to install Python"}'
```

Response:
```json
{
  "status": "success",
  "question": "How to install Python",
  "best_match": "Python installation guide",
  "score": 0.8654
}
```

## 🤖 How It Works

### Embedding (Text Encoding)
```
Question: "How to cook pho?"
         ↓
  Sentence Transformer
         ↓
Vector: [0.12, -0.45, 0.67, ...] (384 dimensions)
```

### Search Process
```
Query Vector → Cosine Similarity → Compare with all documents
              ↓
          Find document with highest score
              ↓
          Return best result
```

## 📊 AI Models Used

- **`paraphrase-multilingual-MiniLM-L12-v2`**: Supports 50+ languages, lightweight
- **`all-MiniLM-L6-v2`**: Optimized for English

## 🔧 Technologies

- **Python 3.8+**
- **Sentence Transformers** (BERT-based)
- **Scikit-learn** (Cosine Similarity)
- **FastAPI** (REST API)
- **NumPy** (Numerical computing)

## 📈 Future Improvements

- [ ] Store documents in a database
- [ ] Support file uploads (PDF, TXT)
- [ ] Fine-tune model for specific domains
- [ ] Cache results for performance
- [ ] Add API authentication
- [ ] Create web frontend

## 📝 License

MIT License - Free for personal and commercial use.

## 👤 Author

**Tienkute** - [GitHub Profile](https://github.com/Tienkute)

## 📞 Contact & Support

- 📧 Email: [Contact via GitHub]
- 🐛 Issues: [GitHub Issues](https://github.com/Tienkute/ESS/issues)

---

**Happy Searching! 🚀**

If you find this project useful, please give it a ⭐ on GitHub!
