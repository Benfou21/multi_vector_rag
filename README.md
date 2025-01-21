
## Project Overview
This personal project implements a chatbot using Retrieval-Augmented Generation (RAG) to provide accurate responses based on the content of uploaded PDF documents. It leverages Chroma for vector storage, Hugging Face transformers for language models, and multi-vector retrieval. The chatbot can handle both text and multimodal inputs (text and images), and it integrates summarization, document retrieval, and text generation to offer detailed answers from the uploaded documents.

## Usage 
- Go on my space : https://huggingface.co/spaces/Benfou21/Mutli_vector_RAG (could be paused) 
- On the first page, you can upload several PDF documents to create the retriever. Once this is done, you can proceed to the second page.
- The second page allows you to ask questions about the documents that were loaded earlier.

## Key Components

### Document Processing 

- PDF Extraction: Uses pdfplumber to extract text, tables, and images from the PDF.
- Text Summarization: The extracted text and table data are summarized using a BART-based transformer model.
- Image Description: Images are processed using the Llava multimodal transformer model, which generates detailed captions.

### Retriver 
- Used Chroma-based vector to store these embeddings, enabling fast retrieval of relevant chunks during query time.
- MultiVectorRetriever: This retriever allows for multi-level retrieval. For each document, we create a summary that is stored as a child chunk. These child chunks are used during the search process to improve the efficiency and accuracy of document retrieval. 

### Language Models
- The project uses a quantized Hugging Face language model (Zephyr 7b) for text generation.

### Limitations 

- The system takes some time to create the retriever due to the generation of the descriptions.

- Answer generation can be slow due to the size of the LLM used.

- Answers are limited by the image descriptions generated in the retriever, so it may not be able to respond to all detailed image-related questions.

## Technologies Used
- Gradio: For building the web interface.
- Langchain: For document processing and multi-vector retrieval.
- Chroma: As the vector store for managing document embeddings.
- Hugging Face Transformers: For embeddings, summarization, and text generation.
- Torch: For GPU-accelerated model inference and quantization.
- pdfplumber: For extracting content from PDF documents.
- Pandas: For table data cleaning and management.

## Contact
For inquiries or further information, please contact me at benjamin.fourreau.epm@outlook.fr.
