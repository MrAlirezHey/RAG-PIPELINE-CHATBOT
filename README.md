
# **RAG Pipeline & Chatbot**

This project demonstrates an automated workflow built using **n8n** that integrates a **RAG pipeline** and **chatbot** functionalities. It uses a combination of **Google Drive triggers**, **OpenAI GPT models**, **Pinecone for vector storage**, and **document processing** to create a sophisticated chatbot that can respond to queries and retrieve information from uploaded documents.

The workflow triggers whenever a new file is uploaded to a Google Drive folder, processes the document, creates embeddings, and uses them for retrieval-augmented generation (RAG) and chatbot interactions.

---

## **Workflow Overview**

### **1. Google Drive Trigger**
- This node monitors a specific Google Drive folder for newly uploaded files. It triggers the workflow when a new file is added to the folder.

### **2. Download File from Google Drive**
- After detecting a new file, the workflow downloads the file from Google Drive for further processing.

### **3. Pinecone Vector Store**
- The downloaded file is processed to generate embeddings using **OpenAI's embeddings API**. These embeddings are then stored in **Pinecone**, which is a vector database designed to efficiently store and retrieve vectorized data.

### **4. Document Loading and Splitting**
- The file is loaded and split into smaller chunks for easier processing. This step ensures that large documents can be divided into manageable pieces for better performance in the RAG process.

### **5. OpenAI Chatbot Model**
- The **OpenAI GPT** model is used to generate responses based on the embeddings stored in Pinecone. The chatbot can respond to queries and provide answers based on the content of the uploaded documents.

### **6. Chat Message Reception**
- The chatbot is triggered whenever a new chat message is received. It uses the previously created embeddings and the OpenAI model to generate a response based on the stored knowledge.

### **7. RAG Pipeline**
- The retrieval-augmented generation (RAG) pipeline retrieves relevant information from Pinecone and uses it to generate high-quality, context-aware responses for the chatbot.

---

## **Features**

- **Automated File Processing**: Automatically triggers and processes newly uploaded files from a Google Drive folder.
- **Document Embeddings**: Uses OpenAI embeddings to convert document content into vector representations.
- **Pinecone Integration**: Stores and retrieves embeddings for efficient search and retrieval.
- **RAG Pipeline**: Enhances chatbot responses with information retrieved from a vector store.
- **AI-Powered Chatbot**: Uses OpenAI GPT models to generate answers based on the retrieved data.

---

## **Tech Stack**

- **n8n**: For orchestrating the workflow and integrating various tools.
- **OpenAI GPT**: For language models used in document processing and chatbot generation.
- **Pinecone**: For vector storage and retrieval.
- **Google Drive API**: For monitoring and downloading files from Google Drive.
- **Node.js**: For running n8n workflows.

---

## **Setup Instructions**

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/rag-pipeline-chatbot.git
cd rag-pipeline-chatbot
```

### 2. Install Dependencies

Ensure that you have **n8n** installed and configured. You can follow the official installation guide for **n8n** if it's not already installed.

```bash
npm install -g n8n
```

Alternatively, you can use **Docker** to set up **n8n**:

```bash
docker run --name n8n -d -p 5678:5678 n8nio/n8n
```

### 3. Configure Environment Variables

Create a `.env` file in the root of the project with the following variables:

```env
GOOGLE_DRIVE_OAUTH2_API_KEY=your_google_drive_oauth2_api_key
OPENAI_API_KEY=your_openai_api_key_here
PINECONE_API_KEY=your_pinecone_api_key_here
```

### 4. Import Workflow into n8n

- Navigate to your **n8n dashboard** at `http://localhost:5678` (if running locally).
- Import the **RAG Pipeline & Chatbot Workflow** (`RAG PIPELINE & Chatbot.json`) into n8n.
- Configure the necessary API keys and test the workflow to ensure it’s working properly.

### 5. Run the Workflow

You can manually trigger the workflow, or set it to run periodically based on the specified schedule. Ensure that your Google Drive folder is properly configured to detect new files.

---

## **Usage**

Once the workflow is set up:

1. **Upload a File**: Upload a new file to the monitored Google Drive folder.
2. **Processing**: The workflow automatically triggers, downloads the file, generates embeddings, and stores them in Pinecone.
3. **Chatbot Interaction**: Users can send chat messages, and the chatbot will respond based on the content of the uploaded document and the stored embeddings.
4. **RAG Responses**: The chatbot uses the RAG pipeline to retrieve relevant information from Pinecone, improving the response quality.

---

## **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## **Acknowledgments**

- **n8n**: For providing the automation platform to connect all services.
- **OpenAI GPT**: For providing the AI-powered language models.
- **Pinecone**: For vector storage and retrieval capabilities.
- **Google Drive API**: For managing file uploads and downloads.

---
