

## Project overview

## Usage :
- Go on my space : https://huggingface.co/spaces/Benfou21/Mutli_vector_RAG
- On the first page, you can upload several PDF documents to create the retriever. Once this is done, you can proceed to the second page.

- The second page allows you to ask questions about the documents that were loaded earlier.

## Detailled 

### Documents loading 

For each document, I separately extract the text, tables, and images.
For the text and tables, I directly generate a summary.

For the images, I use Llava to generate a detailed description and then a summary of the image.
The prompt used is: "Give a detailed technical description of what's in the image, including the colors of the primary elements." The maximum number of tokens for generating the description is set to 400.

### Retriver creation

I used ChromaDb along with LangChain to create the multi-vector retriever.

Each summary is embedded and passed into the retriever as the document for searching. Then, I link the original documents with their IDs to the embedded summaries.

### Qurey 

The query is embedded in the same way as the summaries. We retrieve the relevant documents using similarity search and then chunk each document to respect the 512-token limit of the reader.

I used Zephyr as the LLM to answer the questions. For each query, I pass the chunked relevant document as context.

The prompt used is : "En utilisant les informations contenues dans le contexte,fournissez une réponse complète à la question. La réponse est en français si la question est en français. Répondez uniquement à la question posée ; la réponse doit être concise, structurée et pertinente par rapport à la question. "

### Limitations 

- The system takes some time to create the retriever due to the generation of the descriptions.

- Answer generation can be slow due to the size of the LLM used.

- Answers are limited by the image descriptions generated in the retriever, so it may not be able to respond to all detailed image-related questions.


Fourreau Benjamin
