# Chat with PDF Using RAG Pipeline

## Overview

This project develops a **Retrieval-Augmented Generation (RAG)** pipeline meant to interact with semi-structured data in multiple PDF files. The system enables natural language queries from users while providing accurate, context-sensitive responses or comparisons through data extraction, embedding, and storage for efficient retrieval.

---

## Key Features

### 1. **Data Ingestion**

- **Input**: PDF files with semi-structured data.
- **Process**:
- Extract text and structured information from PDFs.
  - Divide the extracted data into meaningful chunks for granularity.
  - Produce vector embeddings for chunks by using a pre-trained embedding model.
  - Store embeddings in a vector database to enable efficient similarity-based retrieval.

### 2. **Query Handling**
- **Input**: User's natural language question.
- **Process**:
  - Convert the user query into vector embeddings using the same embedding model.
- Issue similarity queries into the vector database to find the most relevant chunks
  - Use the relevant chunks along with a prompt for creating a more detailed response based on an LLM.
 

### 3. Comparison Queries
- **Input**: User queries that query about comparing information across PDFs
- **Process**:  
  Identify relevant terms/fields to compare.
- Gather and collect chunks that have corresponding vectors in the database.
  Output structured answers in the format of, for example, tabular or list formats for ease of comprehension.

### 4. **Response Generation**
- **Input**: information retrieved and user's question.
- **Process**:
  Input an LLM to generate responses that are both factual as well as contextual using a retrieval-augmented prompt.
  Verify the output by using retrieved data while generating responses

---

## Key Technologies

### 1. **LangChain
Used to orchestrate retrieval-augmented generation workflow-which includes prompt engineering, retrieval integration, and response generation.
 
### 2. **GPT-based LLMs**
Leans heavily on a pre-trained huge language model for natural understanding and response generation.
 
### 3. **Vector Databases**
Stores and retrieves embeddings extremely efficiently for similarity-based search. Examples include Pinecone, Weaviate, or FAISS.
 
### 4. **PDF Parsing Tools**
Allows extracting text and metadata from the PDF file. Examples of these tools include PyPDF2, pdfplumber, or Apache PDFBox.

---
 
## Installation

1. Clone the repository:
```bash
   git clone https://github.com/your-username/chat-with-pdf-rag.git
   cd chat-with-pdf-rag
   ```

2. **Install Dependencies**:
   Install Python 3.8 or later.
   ```bash
   pip install -r requirements.txt
   ```

3. **Setup API Keys**:
   Obtain the API keys for the LLM provider you've chosen (e.g. OpenAI, Anthropic).
   Set up a vector database (e.g. Pinecone API key).

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

2. **Ask a Query** :
Use the interface to ask questions about the data in the PDFs. For instance:
    - "What is the revenue for Q1?"
    - "Compare the marketing budgets for 2022 and 2023."

3. **Receive Responses**:
   Get accurate and context-rich answers in natural language or structured formats.

Contributions are welcome! Open an issue or submit a pull request. Make sure your code follows the style of the project.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- **LangChain** for making it easy to seamlessly integrate retrieval and generation workflows.
- **OpenAI** and other LLM providers for their strong language models.
- **PDF parsing libraries** for making data extraction so easy.
