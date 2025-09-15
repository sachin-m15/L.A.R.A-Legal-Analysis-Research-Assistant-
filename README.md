# L.A.R.A - Legal Analysis Research Assistant

## Overview


LARA is an intelligent, Python-based application designed to assist legal professionals and citizens in conducting comprehensive research and case studies based on Indian law. Inspired by the principles of deep research agents, this tool automates the legal analysis workflow by transforming user queries into precise search terms, retrieving information from multiple sources, and synthesizing a cohesive, citable legal analysis.

The system is built using a modular state graph (langgraph) to ensure a scalable and maintainable architecture.



---

## Features
The LARA is designed to be a powerful tool for legal professionals and citizens, streamlining legal research and providing data-driven legal analysis. The core features of the application include:

- **Intelligent Query Rewriting:** Automatically reformulates user-provided legal problems or case descriptions into optimized, legally precise search queries.

- **Hybrid Data Retrieval:**
  - **Vector Store Retrieval:** Queries a pre-indexed FAISS vector store containing a vast corpus of Indian laws, statutes, and previous case judgments.
  - **Web Search Integration:** Utilizes a web search API (e.g., Tavily, DuckDuckGo) to perform deep research on the web, gathering supplementary information and recent developments.
- **Iterative Research:**  The system dynamically evaluates the retrieved information, identifies gaps in knowledge, and generates new search queries in a continuous loop until a comprehensive analysis is achieved.
-**Cohesive Legal Analysis:**  Combines findings from both vector store and web sources into a single, structured, and easy-to-read legal analysis.
- **Citations and Recommendations:** The final output includes clear citations, a summary of key findings, and actionable recommendations based on the gathered data.
- **Legal Advice for Citizens:** A simplified interface and workflow for non-lawyers to get basic, system-generated legal advice on disputes or problems.


- **Model Evaluation Dashboard:** A dedicated Streamlit application to evaluate the performance of various models on legal queries using custom metrics.
  - **Metrics:** Hallucination Score, Relevance Score, Correctness Score, Context Utilization, and Context Precision.
- **Streamlit Visualization:** A Streamlit front-end to present the model evaluation results in an intuitive, visual format, with charts and tables.
- **Modular Workflow (LangGraph):** The entire research process is orchestrated using a state-of-the-art LangGraph state machine, ensuring a robust, scalable, and easy-to-debug architecture.
---

## Structure
```bash
LARA/
├── app.py                    # Main Streamlit app
├── agent.py                  # AI agent and workflow definitions
├── models_score_checker.py   # Model evaluation and Streamlit visualization
├── legal_rag/                # Directory for RAG components
│   ├── retrieval.py          # Vector store and web search logic
│   ├── query_rewriter.py     # Legal query rewriting module
│   └── summarizer.py         # Summary and analysis generation
├── data/                     # Directory for pre-indexed data and raw files
│   ├── faiss_index/          # Stores the FAISS index files
│   ├──indian_law_docs/       # Placeholder for raw Indian law text documents
│   └── data_converter.py     # Converts pdf and json to txt
├── raw_data                  # pdfs and json file 
├── requirements.txt          # Python dependencies
└── README.md                 # Project README file
```

---

## Installation

1. **Clone the repository**

```bash
git clone https://github.com/sachin-m15/L.A.R.A-Legal-Analysis-Research-Assistant-.git
cd L.A.R.A-Legal-Analysis-Research-Assistant-
```

2. **Create and activate a virtual environment**
```bash
python -m venv venv
# Linux/Mac
source venv/bin/activate
# Windows
venv\Scripts\activate
```
3.**Install dependencies**
```bash
pip install -r requirements.txt
```
4.**Set Environment Variables**
Create a .env file in the root directory and add your API keys.
```bash
GROK_API_KEY="your_grok_api_key_here"
TAVILY_API_KEY="your_tavily_api_key_here"
```

5.**Run the application**
```bash
streamlit run app.py
```
