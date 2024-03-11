# Talk_with_multiplepdf
Chat with pdf using Gemini
# Chat PDF Application Documentation

This documentation covers the usage and technical details of the Chat PDF Application, a Python program designed to facilitate interactions with text content extracted from PDF documents through a conversational interface. Utilizing a mix of technologies including Streamlit, PyPDF2, Langchain, and Google Generative AI, this application offers an intuitive way to query PDF content.

## Overview

The Chat PDF Application allows users to upload PDF documents and interact with the extracted content by asking questions directly related to the text. The application processes the PDFs to extract text, chunks the text for efficient processing, generates vector embeddings for these chunks, and utilizes a question-answering model to provide responses to user queries.

## Dependencies

The application relies on several third-party libraries and services:
- **Streamlit**: For creating the web interface.
- **PyPDF2**: To handle PDF document reading and text extraction.
- **Langchain**: A toolkit for building language applications, used here for text splitting and chaining conversational models.
- **Langchain Community**: Provides a FAISS vector store implementation.
- **Langchain Google GenAI**: Integrates Google's Generative AI models for embeddings and chat.
- **Dotenv**: Loads environment variables from a `.env` file, including the Google API key required for the Generative AI services.
- **Google Generative AI**: A service used for generating embeddings and handling conversational responses.

## Setup and Configuration

1. **Environment Variables**: Store your Google API key in a `.env` file using the variable `GOOGLE_API_KEY`.
2. **Google API Configuration**: The application configures the Google Generative AI service using the provided API key.
3. **FAISS Vector Store**: A local instance of the FAISS vector store is created and used for similarity searches within the document content.

## Application Components

### Text Extraction (`get_pdf_text`)
This function accepts a list of PDF files uploaded by the user. It iterates through each PDF, extracting all text content and concatenating it into a single string.

### Text Chunking (`get_text_chunks`)
Given the extracted text, this function chunks the text into manageable sizes using a recursive character text splitter, facilitating efficient processing and embedding generation.

### Vector Store Creation (`get_vector_store`)
This function generates embeddings for the text chunks using Google Generative AI Embeddings and stores these embeddings in a local FAISS vector store for quick similarity searches.

### Conversational Chain (`get_conversational_chain`)
Sets up a conversational chain using a specific prompt template and the ChatGoogleGenerativeAI model. This chain is used to generate detailed answers to user queries based on the context provided by the document content.

### User Interaction (`user_input`)
Handles user queries by performing similarity searches against the vector store to find relevant document content and then using the conversational chain to generate a response. The response is displayed to the user via the Streamlit interface.

### Main Application Flow (`main`)
Defines the Streamlit web interface, allowing users to upload PDF documents, submit questions, and interact with the processed content. The application supports multiple file uploads and provides feedback during the processing stages.

## Running the Application

To run the application:
1. Ensure all dependencies are installed.
2. Place your Google API key in a `.env` file.
3. Run the script using a Python interpreter.

The application will start a local web server, and you can interact with it by opening the provided URL in a web browser.

## Security Considerations

- **API Key Security**: Ensure the `.env` file is secured and not exposed in shared environments.
- **FAISS Deserialization**: The application allows dangerous deserialization for the FAISS vector store. Ensure that the application is run in a trusted environment to mitigate risks.

## Conclusion

The Chat PDF Application offers a novel way to interact with PDF content, leveraging modern AI and NLP technologies to provide a conversational interface for querying documents. By following the setup and usage instructions provided in this documentation, users can efficiently extract insights and information from their PDF documents.

