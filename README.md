# PoC_DocNavigator
A tool to streamline developer workflows by providing efficient navigation and retrieval of documentation, reducing time spent searching and improving productivity.

## Project Overview
**Company X** has identified a significant inefficiency in their development process: developers spend considerable time searching through documentation or asking simple questions that are already documented. This issue disrupts experienced team members and can lead to the propagation of outdated information. To address this, **Loka** is collaborating with **Company X** to develop a Proof of Concept (POC) for a tool aimed at reducing the time developers spend searching through documentation.

The POC will focus on a subset of data, initially applying to one team, and will use public AWS documentation for testing. The tool's main goal is to assist developers with unfamiliar documentation and guide them to further reading as needed.

## Project Structure
The project structure is inside the folder `Loka Assessment`. It contains the following:
- **Notebooks:** 
  - `01: Preprocessing and Embeddings.ipynb`
  - `02 - Langchain for Retrieval Augmentation.ipynb`
- **Folders:**
  - `/CuratedData`: This folder contains the embedding dataframe.
  - `/RawData`: This folder contains the zip file and the unzipped files.


## Notebook Summaries:
### Notebook 01: Preprocessing and Embeddings
This notebook outlines the process of loading, preprocessing, and embedding text documents using OpenAI's GPT-4 model. Below are the key sections and activities:
1. **Document Loading**
    - Overview of the document loading process.
    - **Code**: Import necessary libraries (zipfile, os), unzip the folder containing raw data, and identify the unzipped folder.

2. **Pre-processing and Data Exploration**
    - Description of preprocessing steps and data exploration.
    - **Code**: Import libraries (os, pandas, BeautifulSoup), read markdown files, extract content, and preprocess content using BeautifulSoup. Clean markdown content by removing headers, lists, images, and links. Tokenize documents using tiktoken and analyze token counts.

3. **Splitting and Chunking Content**
    - Explanation of the need for chunking text documents.
    - **Code**: Use langchain.text_splitter to split content into manageable chunks. Apply the split and chunk function to the dataset, and merge split datasets with original data.

4. **Embeddings Using OpenAI**
    - Introduction to generating embeddings using OpenAI's model.
    - **Code**: Combine title and content into a single column, use OpenAI API to generate text embeddings, structure the combined data into JSON format, reorder and rename columns for clarity, and save the final DataFrame to a CSV file.

This notebook provides a comprehensive guide to preparing text data for embedding, from initial loading and preprocessing to chunking and generating embeddings using OpenAI's GPT-4 model.

### Notebook 02: Langchain for Retrieval Augmentation

This notebook demonstrates the use of Langchain for retrieval augmentation by integrating it with Pinecone for efficient data indexing and querying. Key sections and activities include:

1. **Introduction**
    - Overview of the notebook's aim to demonstrate Langchain for retrieval augmentation.

2. **Setup and Configuration**
    - Libraries and API Keys: Import necessary libraries (Pinecone, Pandas, OpenAI) and configure API keys and Pinecone index settings.
    - Initialize Pinecone: Establish connection to Pinecone and create an index if it doesn't already exist.

3. **Data Preparation and Indexing**
    - Load Pre-embedded Data: Load a dataset containing pre-embedded vectors from a CSV file, format the dataframe for upserting into Pinecone.
    - Upsert Data: Upsert the pre-embedded vectors into the Pinecone index and verify the index statistics.

4. **Query Processing and Retrieval**
    - Function Definitions: Define functions for querying Pinecone and retrieving relevant data based on input questions. Implement a QA (Question-Answering) function to handle user queries and fetch answers from Pinecone.
    - Testing Queries: Test the retrieval function with various sample questions (e.g., checking KMS encryption status, SageMaker capabilities).

5. **Retrieval Augmented Generation (RAG)**
    - Integration with OpenAI: Set up OpenAI client for generating responses using chat completions. Define a function to integrate Pinecone retrievals with OpenAI’s chat completion model.
    - Testing RAG: Test the RAG function with sample questions to evaluate the effectiveness of combining retrievals with generative responses.

6. **Conclusion**
    - Summarize the effectiveness of using Langchain and Pinecone for retrieval augmentation, highlighting improvements in query response accuracy and efficiency.

## Getting Started

### Prerequisites

Ensure you have the following installed:
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/CharlieArreola/PoC_DocNavigator/
    cd dev-doc-assist
    ```
2. Install the required Python packages:
   ```bash
   pip install -r requirements.txt

   ```
## Usage

1. **Preprocess and Embed Documentation:**
    - Follow the steps in the `01 - Preprocessing and Embeddings.ipynb` notebook to load, preprocess, chunk, and generate embeddings for your documentation.

2. **Index and Retrieve Documentation:**
    - Follow the steps in the `02 - Langchain for Retrieval Augmentation.ipynb` notebook to index the preprocessed data using Pinecone and perform retrieval-augmented queries using Langchain and OpenAI.

## Contact
For any questions or suggestions, please contact us at carlos.arreola.dev@protonmail.com

