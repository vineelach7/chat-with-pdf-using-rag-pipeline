# Chat with PDF Using RAG Pipeline

## Overview

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline designed to interact with semi-structured data contained in multiple PDF files. The system allows users to ask natural language queries and receive accurate, context-aware responses or comparisons by extracting, embedding, and storing data for efficient retrieval. 

---

## Key Features

### 1. **Data Ingestion**
- **Input**: PDF files containing semi-structured data.
- **Process**:
  - Extract text and structured information from PDFs.
  - Segment extracted data into logical chunks for granularity.
  - Generate vector embeddings for chunks using a pre-trained embedding model.
  - Store embeddings in a vector database for efficient similarity-based retrieval.

### 2. **Query Handling**
- **Input**: User’s natural language question.
- **Process**:
  - Convert the user query into vector embeddings using the same embedding model.
  - Perform a similarity search in the vector database to retrieve the most relevant chunks.
  - Use the retrieved chunks along with a prompt to generate a detailed response using an LLM.

### 3. **Comparison Queries**
- **Input**: User queries that request a comparison of information across PDF files.
- **Process**:
  - Identify relevant terms or fields to compare.
  - Retrieve and aggregate corresponding chunks from the vector database.
  - Generate structured responses (e.g., tabular or bullet-point formats) for clarity.

### 4. **Response Generation**
- **Input**: Retrieved information and user query.
- **Process**:
  - Use an LLM with retrieval-augmented prompts to generate factual and context-aware responses.
  - Ensure accuracy by incorporating retrieved data directly into the generated responses.

---

## Key Technologies

### 1. **LangChain**
Used to orchestrate the retrieval-augmented generation workflow, including prompt engineering, retrieval integration, and response generation.

### 2. **GPT-based LLMs**
Leverages a pre-trained large language model for natural language understanding and response generation.

### 3. **Vector Databases**
Efficiently stores and retrieves embeddings for similarity-based searches. Examples include Pinecone, Weaviate, or FAISS.

### 4. **PDF Parsing Tools**
Extracts text and metadata from PDF files. Examples include PyPDF2, pdfplumber, or Apache PDFBox.

---

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/chat-with-pdf-rag.git
   cd chat-with-pdf-rag
   ```

2. **Install Dependencies**:
   Ensure you have Python 3.8 or higher.
   ```bash
   pip install -r requirements.txt
   ```

3. **Set Up API Keys**:
   - Obtain API keys for your chosen LLM provider (e.g., OpenAI, Anthropic).
   - Configure a vector database (e.g., Pinecone API key).

   Add the keys to your environment variables or a `.env` file:
   ```env
   OPENAI_API_KEY=your_openai_api_key
   PINECONE_API_KEY=your_pinecone_api_key
   ```

4. **Run the Application**:
   ```bash
   python app.py
   ```

---

## Usage

1. **Add PDF Files**:
   Place the PDF files you wish to query in the `data/pdf` folder.

2. **Ask a Query**:
   Use the interface to ask questions about the data in the PDFs. For example:
   - “What is the revenue for Q1?”
   - “Compare the marketing budgets for 2022 and 2023.”

3. **Receive Responses**:
   Get accurate and context-rich answers in natural language or structured formats.

---

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request. Ensure your code adheres to the project’s style guidelines.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- **LangChain** for enabling seamless integration of retrieval and generation workflows.
- **OpenAI** and other LLM providers for their robust language models.
- **PDF parsing libraries** for making data extraction straightforward.
