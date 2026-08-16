# 📚 Milestone3: RAG Knowledge Base for FranchiseOps AI
This milestone focuses on building the **Retrieval-Augmented Generation (RAG) Knowledge Base** for the FranchiseOps AI project. The objective is to collect information from trusted online resources, process the data, convert it into searchable embeddings, and create a FAISS vector database for semantic retrieval.

Instead of relying only on predefined responses, the RAG pipeline enables the AI system to retrieve relevant information from a large knowledge base, making responses more accurate, contextual, and reliable.

# 🎯 Objectives
- Build a knowledge repository for Franchise Operations.
- Collect information from trusted HTML websites and PDF documents.
- Extract and clean textual data automatically.
- Create a searchable vector database using FAISS.
- Support semantic search using sentence embeddings.
- Validate the retrieval process with sample business queries.
 
# 🛠 Technologies Used
- Python
- Google Colab
- LangChain
- FAISS
- HuggingFace Embeddings
- Sentence Transformers
- BeautifulSoup
- Requests
- PyMuPDF (fitz)
- TextBlob
- VADER Sentiment
- Google Drive

# 📂 Project Structure
FranchiseOps_AI/
│
├── rag_documents/
│   ├── html_*.txt
│   ├── pdf_*.txt
│   ├── manifest.json
│
├── kb_franchise.json
│
├── franchiseops_faiss_index/
│
├── RAG_KnowledgeBase.ipynb
│
└── README.md

# 🚀 Workflow
## Step 1 – Environment Setup
- Install all required Python libraries.
- Mount Google Drive.
- Create the RAG document storage directory.
- Configure warning filters.
## Step 2 – Data Source Collection
The system collects data from two major categories:

### HTML Sources
The project gathers information from trusted websites including:
- Marketing research
- Customer experience
- HR management
- Food Safety
- FSSAI
- Labour laws
- OSHA
- WHO
- FDA
- Government portals
- Franchise management resources

### PDF Sources
The project downloads official PDF documents such as:
- FSSAI Regulations
- Food Safety Standards
- WHO Reports
- OSHA Guidelines
- Labour Acts
- Franchise Regulations
- Government Manuals
- Compliance Documents

## Step 3 – HTML Scraping
Each webpage is automatically processed by:
- Sending HTTP requests
- Parsing HTML using BeautifulSoup
- Removing unnecessary tags
- Extracting meaningful text
- Saving cleaned content as text files
  <img width="817" height="282" alt="Screenshot 2026-08-06 180903" src="https://github.com/user-attachments/assets/c2fd6b7a-bdd0-410a-a84c-499feac52d87" />

  <img width="805" height="297" alt="Screenshot 2026-08-06 180924" src="https://github.com/user-attachments/assets/dbc61f80-306c-4baa-b795-0e126d11fff7" />

  <img width="750" height="250" alt="Screenshot 2026-08-06 180939" src="https://github.com/user-attachments/assets/d248cd53-5956-4e7b-9d1c-96cf7746e738" />

## Step 4 – Automatic PDF Discovery
The scraper automatically scans HTML pages for embedded PDF links.
Features include:
- Relative URL conversion
- Duplicate removal
- Automatic PDF collection
- Expansion of the knowledge base
- 
## Step 5 – PDF Processing
Each PDF is:
- Downloaded
- Parsed using PyMuPDF
- Converted into text
- Stored as a text document
- Logged in the manifest file

## Step 6 – Manifest Tracking
A manifest file records every processed URL.
Benefits include:
- Prevents duplicate downloads
- Enables resumable execution
- Tracks successful and failed files

## Step 7 – Document Loading
All generated text files are loaded into LangChain Documents.
Each document stores:
- Content
- Source filename
- Metadata

## Step 8 – Curated Knowledge Base
Along with external data, the project adds manually curated Standard Operating Procedures (SOPs).
Examples include:
- Freezer temperature guidelines
- Food hygiene rules
- Staff requirements
- Marketing ROI thresholds
- Customer complaint handling
- Store opening checklist
- Safety procedures
- FSSAI compliance

These SOPs improve retrieval quality by providing structured operational knowledge.

## Step 9 – Text Chunking
Large documents are split into manageable chunks using:
- RecursiveCharacterTextSplitter
- Chunk Size = 1000 characters
- Chunk Overlap = 100 characters
This improves semantic search accuracy.

## Step 10 – Embedding Generation
Each text chunk is converted into vector embeddings using:
**Model**
all-MiniLM-L6-v2
Advantages:
- Lightweight
- Fast
- High semantic accuracy
- Suitable for Retrieval-Augmented Generation

## Step 11 – FAISS Vector Database
The embeddings are stored in a FAISS vector index.
Benefits:
- Fast similarity search
- Efficient storage
- Scalable retrieval
- Supports semantic queries
The vector database is saved locally for future use.

## Step 12 – Semantic Retrieval Testing
The project validates the RAG system using sample queries such as:
- Minimum freezer temperature
- Staff requirements
- Handwashing procedure
- FSSAI penalties
- Customer complaint escalation
- Marketing ROI threshold
- Staff performance review
The system retrieves the most relevant document along with its source metadata.

# 🔍 Code Analysis
## Data Collection
The code gathers knowledge from trusted websites and official documents.

## Data Cleaning
HTML tags, navigation bars, scripts, and styles are removed to preserve only meaningful textual information.

## PDF Extraction
PyMuPDF extracts machine-readable text from PDF files while ignoring unsupported scanned documents.

## Knowledge Base Construction
The project combines:
- External research documents
- Government regulations
- Official standards
- Internal SOP documents
into a single unified knowledge repository.

## Embedding Pipeline
Each document chunk is converted into numerical vectors using HuggingFace sentence embeddings.
Semantic similarity is preserved, allowing intelligent retrieval.

## Vector Search
FAISS performs nearest-neighbor search to identify the most relevant information based on user queries rather than exact keyword matching.

## Testing
The retrieval system is evaluated using operational and compliance-related questions to ensure relevant information is returned accurately.

# 📈 Features
- HTML Web Scraping
- Automatic PDF Harvesting
- PDF Text Extraction
- Knowledge Base Generation
- SOP Integration
- Document Chunking
- Sentence Embeddings
- FAISS Vector Database
- Semantic Search
- Metadata Tracking
- Manifest Management
- Retrieval Testing

# 📊 Expected Output
- Downloaded HTML and PDF knowledge sources
- Clean text repository
- Curated SOP database
- Chunked documents
- Sentence embeddings
- FAISS vector index
- Successful semantic retrieval for business queries
# Queries
<img width="764" height="283" alt="Screenshot 2026-08-06 181349" src="https://github.com/user-attachments/assets/a8402730-d477-47df-b9b2-6e6f394911b7" />

# Answers
<img width="733" height="288" alt="Screenshot 2026-08-06 181413" src="https://github.com/user-attachments/assets/48cdbb2c-d40f-4b14-b362-ca1d1cfa6eb9" />
<img width="815" height="268" alt="Screenshot 2026-08-06 181430" src="https://github.com/user-attachments/assets/76e76329-e359-48b6-888e-53b2e92989b7" />
<img width="814" height="256" alt="Screenshot 2026-08-06 181510" src="https://github.com/user-attachments/assets/2361aabe-e740-4ba3-aa87-b5a773df0be1" />
<img width="850" height="260" alt="Screenshot 2026-08-06 181539" src="https://github.com/user-attachments/assets/3fb4d5e7-40ff-461a-bafa-d7acae14e3f8" />

# 🎓 Learning Outcomes
Through this milestone, the following concepts were learned:
- Retrieval-Augmented Generation (RAG)
- Web scraping using BeautifulSoup
- PDF text extraction using PyMuPDF
- Document preprocessing
- Text chunking
- Sentence embeddings
- Semantic search
- FAISS indexing
- Knowledge base creation
- LangChain document processing

# 🚀 Future Enhancements
- Integrate a Large Language Model (LLM)
- Build an interactive chatbot
- Support real-time document updates
- Enable multilingual retrieval
- Improve ranking using hybrid search
- Deploy the RAG pipeline as a web application


# Team Members
- Ponnam Shiva Ram
- Muskan Patel
- Nandani Kumari Saha
- Priti
- Madumitha
