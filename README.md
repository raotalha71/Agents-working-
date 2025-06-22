README: CrewAI Customer Support Automation
Overview
This script (crewai_support_automation.py) implements a Customer Support Automation system using CrewAI with the Grok API (Llama-3.3-70B-Versatile model). It automates e-commerce support queries (e.g., "Where is my delayed shipment?") with context-aware responses, using memory management and RAG.
Features

Scenario: Handling customer support queries for an e-commerce platform.
Memory Management:
Short-Term Memory (STM): ChromaDB for task-specific context.
Long-Term Memory (LTM): SQLite3 for query-response history.
RAG: Retrieves context from ChromaDB for task execution.


Tools: Grok API, ChromaDB, SQLite3, CrewAI components (Agent, Task, Crew).

Setup
Prerequisites

Python 3.8+ (recommended).
Grok API key (Grok console).
Google Colab or local Python environment.

Installation

Install dependencies:pip install crewai crewai_tools langchain-groq chromadb


Set environment variable:
Replace your_grok_api_key_here with your Grok API key.



Data Preparation

The script includes sample support context in ChromaDB ("Shipment delays may occur due to weather...").
Customize the context by modifying the collection.add() call if needed.

Usage

Save the script as crewai_support_automation.py.
Run the script in Colab or a local environment:python crewai_support_automation.py


Observe the console output for the response to the query: "Where is my delayed shipment?"
Check the support_history.db SQLite3 database for stored responses.
Test with custom queries by modifying the Task description.
Visualize the workflow using the Mermaid diagram (below) in Mermaid Live Editor.

Mermaid Workflow Diagram
graph TD
    A[Customer Query] --> B[ChromaDB: STM]
    B --> C[RAG: Context Retrieval]
    C --> D[SQLite3: LTM]
    D --> E[Support Agent]
    E --> F[Response]

Memory Management

STM: ChromaDB stores task context (e.g., shipment delay info) for immediate retrieval.
LTM: SQLite3 persists query-response pairs for historical reference.
RAG: Queries ChromaDB to fetch relevant context, informing accurate responses.

Pros and Cons

Pros:
User-friendly for multi-agent tasks.
Simple setup for small-scale automation.


Cons:
Limited LTM scalability with SQLite3.
Less flexible for complex workflows.


