# AI Document Question-Answering System (RAG)

A document question-answering system built using **Retrieval-Augmented Generation (RAG)**. It extracts text from a PDF, retrieves relevant information using semantic similarity, and generates answers using a Hugging Face instruction-tuned language model.

## Project Overview

This project demonstrates how to build a basic RAG pipeline that allows users to ask questions about a PDF document.

Instead of relying only on the language model's existing knowledge, the system retrieves relevant text from the supplied document and uses that information as context when generating an answer.

## Technologies Used

- **Python** – Main programming language
- **PyPDF** – PDF text extraction
- **NumPy** – Similarity calculations
- **Sentence Transformers** – Text embeddings
- **all-MiniLM-L6-v2** – Embedding model
- **Hugging Face Transformers** – Language model integration
- **Qwen2.5-0.5B-Instruct** – Answer generation
- **PyTorch** – Model inference
- **Kaggle Notebooks** – Development environment

## How the System Works

The project follows these steps:

1. **PDF Text Extraction:** Extracts text from the supplied PDF using PyPDF.
2. **Text Chunking:** Splits the extracted text into smaller, overlapping chunks to preserve context.
3. **Embedding Generation:** Converts each text chunk into a vector representation using `all-MiniLM-L6-v2`.
4. **Semantic Retrieval:** Converts the user's question into an embedding and calculates similarity against document embeddings.
5. **Context Retrieval:** Selects the top 3 most relevant chunks.
6. **Answer Generation:** Passes the retrieved context and question to Qwen2.5-0.5B-Instruct to generate an answer.

## RAG Architecture

```text
       PDF Document
             |
             v
      Text Extraction
             |
             v
        Text Chunking
             |
             v
    Embedding Generation
             |
             v
      Document Embeddings
             |
             |
User Question
      |
      v
Question Embedding
      |
      v
Semantic Similarity Search
      |
      v
 Retrieve Top 3 Chunks
      |
      v
  Retrieved Context
      |
      v
 Qwen2.5-0.5B-Instruct
      |
      v
   Generated Answer
```

## Evaluation

The system was evaluated using 10 questions covering topics contained in the PDF document.

The evaluation considered four criteria:

| Evaluation criterion | Result |
|---|---:|
| Retrieval correctness | 10/10 |
| Answer correctness | 10/10 |
| Answer completeness | 10/10 |
| Unsupported information | 0/10 cases |

These results are based on manual evaluation of the generated answers and retrieved context, rather than automated benchmark metrics.

The evaluation report is included in this repository.

## Running the Project

The notebook was developed using Kaggle Notebooks.

### 1. Clone the repository

```bash
git clone https://github.com/feyisa-habtamu/ai-document-qa-rag.git
```

### 2. Install the required libraries

```bash
pip install numpy torch pypdf sentence-transformers transformers
```

### 3. Open the notebook

Open `ai-document-q-a-system-cleaned.ipynb` using Kaggle or Jupyter Notebook.

### 4. Provide a PDF document

In Kaggle, add your PDF through the **Add Input** option.

Update the `pdf_path` variable in the notebook to match the actual path of your PDF file.

### 5. Run the notebook

Execute the notebook cells in order to extract the document text, create embeddings, retrieve relevant chunks, and generate answers.

The first run may take additional time because the pretrained models need to be downloaded.

## Project Structure

```text
ai-document-qa-rag/
│
├── ai-document-q-a-system-cleaned.ipynb
├── Evaluation.pdf
└── README.md
```

## Limitations

- The current implementation processes one supplied PDF document at a time.
- PDF text extraction may not work correctly with scanned documents that require OCR.
- Retrieval quality depends on document content, chunking, embedding quality, and the selected number of chunks.
- Answer generation depends on the retrieved context and the language model's capabilities.
- The project currently uses a small language model to keep experimentation manageable with limited computing resources.

## Future Improvements

- Build an API using FastAPI.
- Develop a simple user interface for document uploads and questions.
- Experiment with different embedding models and retrieval strategies.
- Explore conversation history and multi-document retrieval.
- Improve evaluation using automated evaluation metrics.

## Author

**Feyisa Habtamu**

AI Engineer | Machine Learning & Generative AI

GitHub: [@feyisahabtamu](https://github.com/feyisahabtamu)

---

*This project was developed as a hands-on learning project to understand and implement the fundamental components of Retrieval-Augmented Generation systems.*
