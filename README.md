# Medical Information Retrieval System

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![FAISS](https://img.shields.io/badge/FAISS-Vector%20Search-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

A sophisticated medical information retrieval system that leverages vector similarity search to provide accurate and contextual responses to medical queries. This system uses FAISS (Facebook AI Similarity Search) for efficient similarity search and retrieval of medical information.

## 🚀 Features

- **Intelligent Medical Query Processing**: Advanced natural language processing for medical queries
- **Vector-based Similarity Search**: Lightning-fast retrieval using FAISS indexing
- **Contextual Response Generation**: Provides relevant and contextual medical information
- **Scalable Architecture**: Handles large medical datasets efficiently
- **User-friendly Interface**: Intuitive design for healthcare professionals and researchers

## 📋 Table of Contents

- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)

## 🛠️ Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/medical-retrieval-system.git
cd medical-retrieval-system
```

2. **Create a virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Download required model files**
```bash
# The system requires pre-processed medical data files:
# - medical_faiss_index.bin: FAISS vector index for similarity search
# - medical_text_chunks.pkl: Processed medical text chunks

# Download these files from [provide download link or instructions]
# Place them in the project root directory
```

## ⚡ Quick Start

```python
from medical_retrieval import MedicalRetriever

# Initialize the retrieval system
retriever = MedicalRetriever()

# Load pre-built index and text chunks
retriever.load_index("medical_faiss_index.bin")
retriever.load_text_chunks("medical_text_chunks.pkl")

# Query the system
query = "What are the symptoms of diabetes?"
results = retriever.search(query, k=5)

# Display results
for i, result in enumerate(results):
    print(f"Result {i+1}: {result['text']}")
    print(f"Relevance Score: {result['score']:.4f}\n")
```

## 💻 Usage

### Basic Query Processing

```python
# Initialize the system
retriever = MedicalRetriever()
retriever.setup()

# Single query
response = retriever.query("treatment options for hypertension")
print(response)

# Batch queries
queries = [
    "side effects of aspirin",
    "diagnosis of pneumonia",
    "prevention of heart disease"
]
responses = retriever.batch_query(queries)
```

### Advanced Configuration

```python
# Custom configuration
config = {
    'similarity_threshold': 0.7,
    'max_results': 10,
    'response_length': 'detailed'
}

retriever = MedicalRetriever(config=config)
```

## 📁 Project Structure

```
medical-retrieval-system/
├── src/
│   ├── __init__.py
│   ├── medical_retrieval.py      # Main retrieval logic
│   ├── data_processor.py         # Data preprocessing utilities
│   ├── vector_store.py           # FAISS vector store management
│   └── utils.py                  # Helper functions
├── data/
│   ├── raw/                      # Raw medical datasets
│   └── processed/                # Processed data files
├── models/
│   ├── medical_faiss_index.bin   # Pre-built FAISS index
│   └── medical_text_chunks.pkl   # Processed text chunks
├── tests/
│   ├── test_retrieval.py
│   └── test_processor.py
├── examples/
│   ├── basic_usage.py
│   └── advanced_usage.py
├── requirements.txt
├── setup.py
├── config.yaml
└── README.md
```

## 🔧 Configuration

### Environment Setup

Create a `.env` file in the root directory:

```env
# Model Configuration
MODEL_PATH=./models/
FAISS_INDEX_PATH=./models/medical_faiss_index.bin
TEXT_CHUNKS_PATH=./models/medical_text_chunks.pkl

# Search Configuration
DEFAULT_K=5
SIMILARITY_THRESHOLD=0.6
MAX_RESPONSE_LENGTH=500
```

### YAML Configuration

```yaml
# config.yaml
model:
  embedding_model: "sentence-transformers/all-MiniLM-L6-v2"
  index_path: "./models/medical_faiss_index.bin"
  chunks_path: "./models/medical_text_chunks.pkl"

search:
  default_k: 5
  similarity_threshold: 0.6
  max_results: 20

preprocessing:
  chunk_size: 512
  chunk_overlap: 50
  min_chunk_length: 100
```

## 📊 Data Files Explanation

### FAISS Index (`medical_faiss_index.bin`)
- **Purpose**: High-performance vector similarity search index
- **Content**: Pre-computed embeddings of medical text corpus
- **Size**: Optimized for fast retrieval across large datasets
- **Generation**: Built from processed medical literature and knowledge bases

### Text Chunks (`medical_text_chunks.pkl`)
- **Purpose**: Stores the original text segments corresponding to vector embeddings
- **Content**: Preprocessed and cleaned medical text chunks
- **Format**: Pickled Python object containing structured medical information
- **Usage**: Retrieved during similarity search to provide contextual responses

## 🔍 API Reference

### Core Classes

#### `MedicalRetriever`

Main class for medical information retrieval.

**Methods:**

- `__init__(config=None)`: Initialize retriever with optional configuration
- `load_index(index_path)`: Load pre-built FAISS index
- `load_text_chunks(chunks_path)`: Load preprocessed text chunks
- `search(query, k=5)`: Perform similarity search
- `query(question)`: Get formatted response to medical query

#### `DataProcessor`

Utility class for data preprocessing.

**Methods:**

- `process_medical_texts(texts)`: Process raw medical texts
- `create_embeddings(texts)`: Generate vector embeddings
- `build_index(embeddings)`: Create FAISS search index

## 🧪 Testing

Run the test suite:

```bash
# Run all tests
python -m pytest tests/

# Run specific test file
python -m pytest tests/test_retrieval.py

# Run with coverage
python -m pytest tests/ --cov=src/
```

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 style guidelines
- Add tests for new functionality
- Update documentation for any API changes
- Ensure all tests pass before submitting


## ⚠️ Disclaimer

This system is designed for informational and research purposes only. It should not be used as a substitute for professional medical advice, diagnosis, or treatment. Always consult with qualified healthcare providers for medical decisions.

## 🙏 Acknowledgments

- FAISS team for the efficient similarity search library
- Medical research community for open-access literature
- Contributors and maintainers of this project

## 📞 Support

For questions, issues, or support:

- 📧 Email: lilhaharsh@gmail.com
- 🐛 Issues: [GitHub Issues](https://github.com/Harshlilha/medical-retrieval-system/issues)
- 💬 Discussions: [GitHub Discussions](https://github.com/Harshlilha/medical-retrieval-system/discussions)

---

**Made with ❤️ for the medical research community**
