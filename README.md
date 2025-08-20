# AI-Powered PDF Document Analysis System

A comprehensive web application that enables intelligent document analysis and Q&A using AI embeddings and retrieval-augmented generation (RAG).

## Features

### Core Functionality
- **PDF Upload & Processing**: Drag-and-drop interface with intelligent text extraction
- **Smart Text Chunking**: Documents are intelligently segmented for optimal retrieval
- **Vector Embeddings**: Uses OpenAI's text-embedding-3-small model for semantic understanding
- **RAG-based Q&A**: Combines document retrieval with GPT-3.5-turbo for accurate answers
- **Source References**: Every answer includes source citations with similarity scores

### User Interface
- **ChatGPT-style Interface**: Modern, intuitive chat experience
- **Document Management**: Sidebar for viewing and managing uploaded documents
- **Real-time Processing**: Live feedback during upload and query processing
- **Responsive Design**: Works seamlessly on desktop and mobile devices

### Technical Features
- **Persistent Storage**: Documents and embeddings are stored for ongoing sessions
- **Error Handling**: Comprehensive error handling with user-friendly messages
- **Multiple Document Support**: Upload and query across multiple PDF documents
- **Similarity Search**: Advanced cosine similarity matching for relevant content retrieval

## Tech Stack

### Frontend
- **React 18** with TypeScript
- **Tailwind CSS** for styling
- **Lucide React** for icons
- **Axios** for API communication

### Backend
- **Node.js** with Express
- **OpenAI API** for embeddings and chat completions
- **pdf-parse** for PDF text extraction
- **Multer** for file upload handling
- **In-memory vector storage** with cosine similarity search

## Setup Instructions

### Prerequisites
- Node.js (v18 or higher)
- OpenAI API key

### Installation

1. **Clone and install dependencies:**
```bash
npm install
```

2. **Configure OpenAI API:**
   - Open the `.env` file
   - Replace `your-openai-api-key-here` with your actual OpenAI API key
   - Get your API key from: https://platform.openai.com/api-keys

3. **Start the application:**
```bash
npm run dev
```

This will start both the React frontend (port 5173) and Node.js backend (port 3001).

### Usage

1. **Upload Documents**: 
   - Drag and drop PDF files or click to browse
   - Wait for processing completion (text extraction + embedding generation)

2. **Ask Questions**:
   - Type natural language questions about your documents
   - Receive AI-generated answers with source references
   - View similarity scores and excerpts from relevant sections

3. **Manage Documents**:
   - View all uploaded documents in the sidebar
   - Delete documents as needed
   - Clear chat history

## API Endpoints

- `POST /api/upload` - Upload and process PDF documents
- `GET /api/documents` - Retrieve list of uploaded documents
- `POST /api/query` - Query documents with natural language
- `DELETE /api/documents/:id` - Delete specific document

## Architecture

### Document Processing Pipeline
1. **PDF Upload** → Text extraction using pdf-parse
2. **Text Chunking** → Intelligent segmentation with overlap
3. **Embedding Generation** → OpenAI text-embedding-3-small
4. **Vector Storage** → In-memory storage with metadata

### Query Processing Pipeline
1. **Query Embedding** → Convert question to vector
2. **Similarity Search** → Find relevant document chunks
3. **Context Assembly** → Compile top matches
4. **Answer Generation** → GPT-3.5-turbo with context
5. **Source Attribution** → Include references and scores

## Limitations & Considerations

- **Memory Storage**: Current implementation uses in-memory storage (data lost on restart)
- **Single Instance**: Not designed for multi-user scenarios
- **File Size**: Recommended PDF size limit of 50MB
- **OpenAI Dependency**: Requires valid OpenAI API key and credits

## Production Enhancements

For production deployment, consider:
- **Persistent Vector Database**: Pinecone, ChromaDB, or FAISS with file storage
- **User Authentication**: Multi-user support with isolated document spaces
- **Database Integration**: PostgreSQL with vector extension (pgvector)
- **Caching Layer**: Redis for faster embedding retrieval
- **File Storage**: AWS S3 or similar for PDF storage
- **Rate Limiting**: API rate limiting and user quotas
- **Monitoring**: Logging and analytics for usage tracking

## Contributing

This is a demonstration project showcasing RAG implementation with modern web technologies. The codebase is well-structured for extensions and improvements.

## License

MIT License - See LICENSE file for details