# n8n Vertex AI RAG Pipeline

This project implements a document processing pipeline using n8n, Google Vertex AI, and Supabase. It processes documents from Google Drive, optimizes them for RAG (Retrieval-Augmented Generation), and stores both the processed documents and their vector embeddings in Supabase.

## Features

- **Document Ingestion**: Pulls documents from Google Drive
- **Document Processing**: Uses Vertex AI to convert documents into RAG-optimized markdown
- **Vector Embeddings**: Generates and stores vector embeddings using Vertex AI's textembedding-gecko model
- **Storage**: Stores both processed documents and embeddings in Supabase

## Prerequisites

1. **Google Cloud Platform (GCP) Account**
   - Enable Vertex AI API
   - Create OAuth 2.0 credentials
   - Add required scopes:
     - `https://www.googleapis.com/auth/cloud-platform`
     - `https://www.googleapis.com/auth/drive.readonly`

2. **Supabase Account**
   - Create a new project
   - Enable the `pgvector` extension
   - Create the required tables (see `supabase/schema.sql`)

3. **n8n**
   - Self-hosted or cloud instance
   - Install required nodes:
     - `n8n-nodes-base.supabase`
     - `n8n-nodes-base.googleDrive`

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/n8n-vertex-rag.git
   cd n8n-vertex-rag
   ```

2. Import the workflow into n8n:
   - Open n8n
   - Go to Workflows > Import from File
   - Select `workflows/document_processing.json`

3. Set up credentials in n8n:
   - Google Drive OAuth2
   - Google Cloud OAuth2 (for Vertex AI)
   - Supabase Service Role Key

## Usage

1. **Configure the workflow**:
   - Update the GCP project ID in the Vertex AI nodes
   - Configure the Google Drive folder to monitor
   - Set up the Supabase connection details

2. **Run the workflow**:
   - Toggle the workflow to active in n8n
   - The workflow will automatically process new documents in the specified Google Drive folder

## Project Structure

```
.
├── README.md              # This file
├── workflows/             # n8n workflow definitions
│   └── document_processing.json  # Main workflow
└── supabase/
    └── schema.sql        # Database schema for Supabase
```

## License

[MIT](LICENSE)
