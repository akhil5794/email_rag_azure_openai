# LLM-based Question Answering given Email Data

The provided dataset contains email communication from the senior management of Enron company. The emails are divided across 45 plain text files, containing 96,107 messages. The corpus contains 2,205,910 lines and 13,810,266 words.

The task here is to build a solution pipeline (**preferably using LLMs**) to answer `30` questions, based on the provided email corpus. 

# RAG application on Email Data with Azure Open AI & Azure Cognitive Search

<img src="https://github.com/retkowsky/images/blob/master/azure_openai_logo.png?raw=true" width=400>

### Objective
Let's build an application that will analyse **Email documents using a RAG application.**

**Retrieval-Augmented Generation (RAG)** can exhibit variability in its implementation, but at a fundamental level, employing RAG within an AI-driven application involves the following sequential steps:


### Step 1: Read the email corpus from `data/email_data`

### Step 2: Read the Simple QA corpus from `data/qa_pairs/question_answer.jsonl`

### Step 3: Implement a solution approach (preferably LLM-based) to answer the questions from Simple QA corpus

- 3.1. **Data Preparation**
    - **Document Collection**: Read the emails and preprocess the email data.
    - **Chunking/Splitting**: Split documents into chunks for efficient retrieval.

- 3.2. **Indexer Training**
    - Train an indexer to create a dense vector representation of each passage.
        - **Embeddings**: Used a pre-trained model (OpenAI - text-ada-002) to generate embeddings for each passage.
        - **Index Creation**: Store these embeddings in a searchable index (Azure Search).
        
- 3.3. **Retriever Setup**
    - Implement a retriever to fetch the most relevant passages based on a query.
        - **Query Encoding**: Encode the user query into the same vector space.
        - **Similarity Search**: Use the index to find similar passages.
        
- 3.4. **Generative Model Integration** (GPT-3.5 or GPT-4) to use the retrieved passages as context.
    - **Contextual Prompting**: Format the retrieved passages and query as input for the model.
    - Use Azure OpenAI to generate responses using the retrieved passages as context. Make sure you have an Azure account and the OpenAI service configured.

- 3.5. **Inference Pipeline** :
    - Develop a pipeline to handle the entire process from user query to final answer.
        - **Input Handling**: Accept user queries.
        - **Retrieval**: Retrieve relevant passages using the retriever.
        - **Generation**: Generate the final answer using the generative model.
        
### Step 4: Implement one (or more) quantitative evaluation metrics to measure the performance of the generated answers 


### Steps
- Uploading embedded chunk documents into an Azure Cognitive Search Index
- Use of some Azure Cognitive Search queries to get relevant answers
- Use a GPT model to analyse the answer (summary, keywords generation)
- Get the text from the document and the reference to validate the proposed answer
- Chatbot experience using Azure Open AI to ask questions and get results provided by AI with references

### Process
<img src="https://github.com/retkowsky/images/blob/master/rag.png?raw=true" width=800>


### The results can be referenced here:

![image](https://github.com/user-attachments/assets/92d4bae6-19b6-47c7-beaa-2c2c09a2d56e)
