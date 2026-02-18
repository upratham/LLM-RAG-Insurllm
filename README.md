# Insurellm Expert Assistant

A RAG-powered question answering system for Insurellm employees. This AI assistant provides accurate answers about company information, products, contracts, and employees using retrieval-augmented generation.

## Features

- 🤖 **Conversational AI Interface** - Built with Gradio for easy interaction
- 📚 **RAG Pipeline** - Retrieves relevant context from company knowledge base
- 🔍 **Semantic Search** - Uses ChromaDB for efficient vector similarity search
- 💡 **Smart Ranking** - Re-ranks retrieved chunks for optimal accuracy
- 💬 **Chat History** - Maintains conversation context

## Project Structure

```
├── app.py                  # Gradio web interface
├── src/
│   ├── ingest.py          # Process and embed documents into vector DB
│   ├── answer.py          # RAG pipeline for answering questions
│   ├── eval.py            # Evaluation metrics
│   └── test.py            # Testing utilities
├── data/
│   ├── knowledge-base/    # Source documents (company, contracts, products, employees)
│   ├── vector_db/         # ChromaDB persistent storage
│   └── test/              # Test datasets
└── notebooks/
    └── RAG_Pipeline.ipynb # Development notebook
```

## Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd LLM-RAG-Insurllm
   ```

2. **Create virtual environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate  # Windows
   # or
   source .venv/bin/activate  # Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   
   Create a `.env` file in the root directory:
   ```
   OPENAI_API_KEY=your_openai_api_key_here
   ```

## Usage

### Running the Web Interface

```bash
python app.py
```

The Gradio interface will launch at `http://localhost:7860`

### Demo

The following screenshot shows the Insurellm Expert Assistant in action:

![Insurellm Expert Assistant Demo](/assets/demo_UI.png)

**Example Interaction:**
- **User Query**: "Tell me about your healthcare product"
- **Assistant Response**: Provides detailed information about Healthllm with key features including intelligent plan design, real-time eligibility verification, AI-driven claims adjudication, and more
- **Retrieved Context**: Displays the relevant source documents from the knowledge base that were used to generate the answer

The dual-panel interface shows:
- **Left Panel**: Conversation history and user questions
- **Right Panel**: Retrieved context and source documents used for generating answers

### Ingesting Documents

To process and embed documents into the vector database:

```bash
python -m src.ingest
```

### Answering Questions Programmatically

```python
from src.answer import answer_question

question = "What products does Insurellm offer?"
answer, context = answer_question(question)
print(answer)
```

## Evaluation & Performance

The system has been rigorously evaluated on 150 test cases across multiple question categories. Below are the key performance metrics:

![Evaluation Metrics](/assets/eval_result.png)

### Retrieval Evaluation

The retrieval system demonstrates strong performance in finding relevant context:

- **Mean Reciprocal Rank (MRR)**: 0.8750 - Measures how quickly relevant documents appear in search results
- **Normalized DCG (nDCG)**: 0.8539 - Evaluates the quality of document ranking
- **Keyword Coverage**: 95.7% - Percentage of important keywords found in retrieved context

Performance varies by category, with temporal and numerical queries showing particularly strong results.


The system performs consistently well across different question types, with comparative and numerical questions showing the highest accuracy scores.

## Technology Stack

- **LLM**: OpenAI GPT-4.1-nano (via LiteLLM)
- **Embeddings**: OpenAI text-embedding-3-large
- **Vector DB**: ChromaDB
- **Framework**: LangChain
- **Interface**: Gradio
- **Language**: Python 3.x

## Author

**Prathamesh Uravane**  
Email: upratham2002@gmail.com

## License

See [LICENSE](LICENSE) file for details.
