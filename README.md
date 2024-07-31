# LLM Chatbot

## Project Overview

This project demonstrates how to use Amazon Bedrock for embedding and LLM services, along with Amazon S3 for storage, to process PDF documents and create a chat interface that allows users to ask questions about the content of those documents. The application is built using Streamlit for the web interface.

## Amazon Services Used

### Amazon S3

**Purpose:** Used for storing the FAISS index files (`my_faiss.faiss` and `my_faiss.pkl`) which are necessary for retrieving embedded document vectors.

**Service:** `s3_client` from the boto3 library.

### Amazon Bedrock

**Purpose:** Provides embeddings and language models for processing and querying the text.

**Embeddings Model:** `amazon.titan-embed-text-v1`

**LLM Model:** `amazon.titan-text-lite-v1`

**Service:** `bedrock_client` from the boto3 library.

## Project Components

### File Upload and Processing (`admin.py`)

- Users can upload a PDF file.
- The PDF file is split into chunks for better processing.
- The chunks are embedded using Amazon Bedrock and stored in a FAISS index.
- The FAISS index is saved locally and uploaded to Amazon S3 for persistence.

### Chat Interface (`user.py`)

- Loads the FAISS index from Amazon S3.
- Allows users to ask questions about the content of the uploaded PDF.
- Retrieves relevant document chunks using FAISS and generates answers using Amazon Bedrock.

