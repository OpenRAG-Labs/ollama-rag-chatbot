<p align="center">
  <img src="https://img.shields.io/badge/Architecture-RAG-blue" alt="RAG Architecture"/>
  <img src="https://img.shields.io/badge/Open%20Source-Yes-brightgreen" alt="Open Source"/>
  <img src="https://img.shields.io/badge/Docker-Ready-blue" alt="Docker Ready"/>
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue" alt="Python 3.8+"/>
  <img src="https://img.shields.io/badge/FastAPI-0.100%2B-green" alt="FastAPI"/>
  <img src="https://img.shields.io/badge/License-MIT-green" alt="MIT License"/>
</p>

<h1 align="center">RAG with Open Source Models</h1>

<p align="center">
  A production-ready Retrieval-Augmented Generation (RAG) system built entirely with open-source technologies
</p>

## 🚀 Features

- 🔓 **100% Open Source** - No proprietary APIs or services required
- 🤖 **Local LLM Integration** - Powered by Ollama with Gemma embeddings and Granite models  
- 🗄️ **Vector Database** - Qdrant for efficient similarity search and retrieval
- 🐳 **Production Ready** - Dockerized setup with proper environment configuration
- 🌐 **RESTful API** - FastAPI with automatic Swagger documentation
- ⚙️ **Configurable** - Easy-to-modify similarity thresholds and document paths
- 📈 **Scalable** - Modular architecture allowing easy extensions
- 🔍 **Semantic Search** - Advanced retrieval with configurable similarity thresholds
- 📄 **Multi-format Support** - Process PDF, DOCX, TXT documents
- 🚀 **High Performance** - Optimized for speed and resource efficiency
# 🏗️ Architecture
```bash
User Query → Embedding Generation → Vector Search → Context Augmentation → LLM Generation → Response
```
# 📋 Prerequisites
Docker and Docker Compose (for containerized setup)

or Python 3.8+ and Ollama (for local development)
# 🛠️ Quick Start

## Docker Setup (Recommended)
1. Clone the repository
```bash
git clone https://github.com/porag188/rag-open-source.git
cd rag-open-source
```
3. Start services
```bash
docker-compose up -d
```
4. Access the application

- **API:** http://localhost:8000
 - **Interactive Documentation:** http://localhost:8000/docs
- **Health Check:** http://localhost:8000/health

# Local Development Setup
1. Install dependencies
```bash
pip install -r requirements.txt
```
2. Set up Ollama
```bash
# Start Ollama service
ollama serve

# Download required models
ollama pull embeddinggemma:latest
ollaya pull granite3.1-moe:1b
```
3. Configure environment
```bash
cp .env.example .env
# Edit .env with your configuration
```
4. Vector Store Ingestion
```bash
# To update the vector store with the latest data, run the following command
python /scripts/vector_store_ingestion.py
```
5. Run the application
```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

# ⚙️ Configuration
Environment Variables
Variable	Description	Default
DOC_CONFIG_PATH	Path to your document	./data/document.pdf
SIMILARITY_THRESHOLD	Minimum similarity score for retrieval	0.3
QDRANT_URL	Qdrant database URL	-
QDRANT_API_KEY	Qdrant API key

# Document Support
Currently supports PDF documents. Place your documents in the ```data/``` directory and update ``` DOC_CONFIG_PATH``` in your environment variables.

# 📚 API Documentation

Once running, access the interactive Swagger documentation at http://localhost:8000/docs

## Key Endpoints
- **POST /query** - Submit questions and get AI-powered answers
- **GET /health** - System health check
- **POST /ingest** - Ingest new documents (coming soon)

# 🧩 How It Works
- **Document Processing:** PDFs are chunked and embedded using Gemma embeddings
- **Vector Storage:** Embeddings are stored in Qdrant for efficient similarity search
- **Query Processing:** User questions are embedded and matched against document chunks
- **Context Retrieval:** Most relevant chunks are retrieved based on similarity threshold
- **Response Generation:** Granite model generates answers using retrieved context

# 🔧 Customization
Adjusting Similarity Threshold
Modify SIMILARITY_THRESHOLD in your environment variables:

- **Lower values (0.1-0.3):** More comprehensive but potentially less relevant results
- **Higher values (0.4-0.7):** More precise but potentially missing relevant context

Adding New Models
Update the model names in your Ollama setup and modify the configuration in the application.

# 🤝 Contributing
We welcome contributions! Please see our Contributing Guidelines for details.

- Development Setup
- Fork the repository
- Create a feature branch
- Make your changes
- Add tests
- Submit a pull request

# 📊 Performance
- **Embedding:** Gemma (optimized for retrieval)
- **Generation:** Granite 3.1 MoE 1B (efficient and capable)
- **Vector Search:** Qdrant (high-performance)

# 🚧 Roadmap
- Support for multiple document formats (DOCX, TXT, HTML)
- Web interface for easier interaction
- Batch processing capabilities
- Advanced chunking strategies
- Hybrid search (keyword + semantic)
- Multiple LLM provider support

# 🐛 Troubleshooting
Common Issues
Ollama models not loading
- **Ensure Ollama service is running:** ollama serve
- **Verify model names:** ollama list
Qdrant connection issues
- Check Qdrant service status
- Verify API keys and URLs in environment variables
Memory issues
- Consider using smaller models
- Adjust chunk sizes in configuration

# 📄 License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for full details.

# 🙏 Acknowledgments
Ollama for easy local LLM management

- Qdrant for the open-source vector database
- FastAPI for the modern web framework
- IBM for the Granite models
- Google for the Gemma models

# 📞 Support

- 🐛 **Report Bugs**: [Create an Issue](https://github.com/OpenRAG-Labs/ollama-rag-chatbot/issues)
- 💡 **Request Features**: [Open Feature Request](https://github.com/OpenRAG-Labs/ollama-rag-chatbot/issues)
- 💬 **Get Help**: [Join Discussions](https://github.com/OpenRAG-Labs/ollama-rag-chatbot/discussions)
- ❓ **FAQ**: Check our [Discussions Q&A](https://github.com/OpenRAG-Labs/ollama-rag-chatbot/discussions/categories/q-a)



