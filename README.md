# Hog RAGger

This project is a web-based application that processes user queries to retrieve relevant documents from the corpus, generate concise answers, classify question types, and provide evidence for the answer. The application integrates a pre-trained LLaMA model for generating answers and FAISS for document retrieval. The app is built using **Gradio** for the user interface.

## Features

- **Query Input**: Accepts user queries related to research topics.
- **Answer Generation**: Provides a concise answer based on retrieved documents using the LLaMA model.
- **Question Type Classification**: Classifies the query type (e.g., factual, theoretical).
- **Evidence Retrieval**: Lists evidence from the retrieved documents, including title, author, source, and relevant facts extracted from each document.

## How It Works

1. **Document Retrieval**: 
    - The query is encoded using **SentenceTransformer** for semantic similarity and passed to FAISS for vector-based document retrieval.
    - The system retrieves the top `k` relevant documents and their metadata (title, author, URL, etc.).
   
2. **Summarization**: 
    - The retrieved documents are combined, and a summary is generated to provide concise context for answer generation.
   
3. **Answer Generation**: 
    - The summarized content is passed to the **LLaMA** model to generate a response to the user's query.
    - The model is being accessed through local tunneling at the port where local host is running the model on local machine through flask
   
4. **Classification and Evidence**: 
    - The generated answer is classified based on question type.
    - Evidence is compiled from the retrieved documents, including key facts from each document.

## Installation

### Prerequisites

- Python 3.x
- Required Python libraries:
  - `gradio`
  - `sentence-transformers`
  - `faiss`
  - `numpy`

### Setup

1. Clone this repository:
    ```bash
    git clone <repository-url>
    ```

2. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Run the Flask app
    ```bash
    python app.py
    ```
    Note: The app.py file is not provided as it contains our confidential API-key.
   
4. Access the app locally:
    - The app will be available at `http://localhost:7860`.

## Usage

- Enter a query in the text box (e.g., "What are the benefits of AI in healthcare?").
- Click on the **Submit Query** button.
- The app will generate:
    - A concise **Answer** based on the retrieved documents.
    - A **Question Type** classification (e.g., factual, analytical).
    - An **Evidence** list with detailed metadata and extracted facts from the sources.


## Technologies Used

- **FAISS**: Efficient similarity search and clustering of dense vectors.
- **LLaMA**: Large language model used for natural language understanding and answer generation.
- **SentenceTransformer**: Used for encoding queries and documents to vectors for semantic similarity.
- **Gradio**: Simplified web interface for machine learning applications.
- **Flask**: Hosting the Llama model on local host from local machine



