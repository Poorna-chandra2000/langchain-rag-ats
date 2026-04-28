````markdown
# AI Resume Matcher using RAG + Hybrid Search

## Overview

This project is an **AI-powered Resume Screening System** that matches resumes against a job description using **RAG (Retrieval-Augmented Generation)** and **Hybrid Search**.

It helps recruiters or hiring teams automatically rank candidates based on:

- Skills match
- Experience relevance
- Education fit
- Project relevance
- Overall suitability score

---

## Features

✅ Upload multiple resumes (`PDF`, `DOCX`, `TXT`)  
✅ Extract text from resumes automatically  
✅ Smart chunking for long resumes  
✅ Semantic search using embeddings  
✅ Keyword search using BM25  
✅ Hybrid ranking (semantic + keyword)  
✅ LLM candidate evaluation using Groq Llama 3.3 70B  
✅ JSON structured output  
✅ Candidate ranking with scores  

---

## Tech Stack

| Technology | Purpose |
|----------|---------|
| Python | Core programming |
| LangChain | LLM pipelines |
| Groq API | Fast LLM inference |
| ChromaDB | Vector database |
| HuggingFace Embeddings | Resume embeddings |
| BM25 | Keyword ranking |
| PyPDF | PDF reading |
| python-docx | DOCX reading |

---

## Project Flow

```text
Upload Resumes
      ↓
Read Resume Content
      ↓
Split into Chunks
      ↓
Create Embeddings
      ↓
Store in ChromaDB
      ↓
Create BM25 Index
      ↓
Enter Job Description
      ↓
Hybrid Retrieval
      ↓
Send Top Candidates to LLM
      ↓
Return Ranked Candidates
````

---

## Installation

## 1. Install Dependencies

```bash
pip install -U langchain langchain-core langchain-community \
langchain-groq langchain-huggingface langchain-chroma chromadb \
transformers sentence-transformers pypdf python-docx rank-bm25 tqdm pandas requests
```

---

## 2. Add Groq API Key

```python
os.environ["GROQ_API_KEY"] = "your_api_key"
```

Get key from:

[https://console.groq.com/](https://console.groq.com/)

---

## Folder Structure

```text
project/
│── resumes/
│    ├── candidate1.pdf
│    ├── candidate2.docx
│    └── candidate3.txt
│
│── chroma_db/
│── matching_results.json
│── Rag.ipynb
```

---

## Supported Resume Formats

* `.pdf`
* `.docx`
* `.txt`

---

## How It Works

## Resume Parsing

The system extracts plain text from resumes.

## Chunking

Large resumes are split into chunks:

```python
chunk_size = 1200
chunk_overlap = 200
```

---

## Embeddings Used

```python
BAAI/bge-large-en-v1.5
```

Used for semantic similarity.

---

## Hybrid Search Logic

Final ranking combines:

```text
Final Score =
(Embedding Similarity Score) +
(BM25 Keyword Score)
```

This improves accuracy.

---

## Example Job Description

```text
Need Python Machine Learning Engineer with 5+ years experience.
Must know NLP, Deep Learning, AWS, Docker, SQL.
```

---

## Example Output

```json
[
  {
    "candidate_name": "John Doe",
    "match_score": 92,
    "skills_match": "Excellent",
    "experience_match": "Strong",
    "reason": "Strong ML + NLP + Docker experience"
  },
  {
    "candidate_name": "Jane Smith",
    "match_score": 84
  }
]
```

---

## Output File

Results are saved as:

```text
matching_results.json
```

---

## Use Cases

### HR Teams

Shortlist top candidates quickly.

### Recruitment Agencies

Automate resume screening.

### Job Portals

Smart candidate-job matching.

### Enterprises

Internal hiring automation.

---

## Future Improvements

* Web UI with Streamlit / React
* Resume skill graph
* JD keyword extraction
* Email shortlisted candidates
* Multi-language resumes
* ATS score checker
* Interview question generator

---

## Performance Tips

Use:

```python
llama-3.3-70b-versatile
```

For fastest Groq inference.

---

## Author

Built with ❤️ using RAG + LLM + Hybrid Retrieval

---

## License

MIT License

```
```
