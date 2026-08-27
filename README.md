# Amma's Kitchen — AI Customer Support Agent

An AI-powered customer support agent built using **n8n, Pinecone, RAG, and OpenAI**.

##  Project Overview

This project demonstrates how an AI agent can answer customer questions using information stored in a business knowledge base.

The project was created as a practical learning project to understand **Agentic AI, Retrieval-Augmented Generation (RAG), embeddings, vector databases, and workflow automation**.

The use case is a fictional cafe called **Amma's Kitchen**.

##  Objective

The objective was to create an AI customer-support assistant that can:

* Receive questions from customers through a chat interface
* Understand the customer's question
* Retrieve relevant information from the Amma's Kitchen knowledge base
* Generate an appropriate response using an AI model
* Maintain conversation context using memory

## Concepts Learned

### 1. Agentic AI

First, the project explored the concept of **Agentic AI** and how an AI agent can perform tasks based on instructions and available tools instead of simply generating a static response.

### 2. Retrieval-Augmented Generation (RAG)

RAG allows an AI system to retrieve relevant information from an external knowledge base before generating an answer.

The learning process covered:

* Chunking
* Embeddings
* Vector databases
* Retrieval
* Generating responses using retrieved information

A simple **teacher and student analogy** was used to understand how information can be divided into smaller pieces, converted into embeddings, and retrieved when needed.

##  Architecture

The workflow was built using **n8n** and connected with **Pinecone** as the knowledge retrieval layer.

### Main workflow components

**Customer Chat → n8n Chat Trigger → AI Agent → OpenAI Chat Model + Simple Memory → Pinecone Knowledge Retrieval → AI Response**

##  Technologies Used

| Technology    | Purpose                                        |
| ------------- | ---------------------------------------------- |
| n8n           | Workflow automation and AI agent orchestration |
| OpenAI        | Language model used to generate responses      |
| Pinecone      | Vector database and knowledge retrieval        |
| RAG           | Retrieval-Augmented Generation                 |
| HTTP Request  | Communication between n8n and Pinecone         |
| Simple Memory | Maintains conversation context                 |

##  Workflow Implementation

### Step 1 — Chat Trigger

The **When Chat Message Received** trigger was used to receive customer questions.

This provides the AI agent with the customer's real-time chat input.

### Step 2 — AI Agent

An **AI Agent** node was added to act as the main AI orchestrator.

It connects the incoming customer question with the AI model, memory, and external tool.

### Step 3 — OpenAI Chat Model

An **OpenAI Chat Model** was connected to the AI Agent.

The model is responsible for understanding the customer's question and generating the final response.

### Step 4 — Simple Memory

**Simple Memory** was connected to the AI Agent so that the conversation could maintain context between messages.

### Step 5 — Pinecone Knowledge Base

A Pinecone assistant named **ammas-kitchen** was created.

The **Amma's Kitchen Master Document** was uploaded to the Pinecone knowledge base.

This document acts as the source of information for the AI assistant.

### Step 6 — API Connection

A Pinecone API key was generated and the required Pinecone request information was connected to n8n using an **HTTP Request** node.

The API key was configured inside the workflow rather than being exposed in the public project documentation.

### Step 7 — Dynamic Customer Input

Inside the HTTP Request JSON body, the customer message was made dynamic using the n8n expression:

`{{ $json.chatInput }}`

Instead of sending a fixed question, the workflow passes the **actual question entered by the customer** to the request.

This allows the agent to respond to different questions in real time.

##  How the System Works

1. A customer enters a question in the chat.
2. The n8n chat trigger receives the question.
3. The AI Agent processes the request.
4. The AI model helps understand and generate the response.
5. The Pinecone knowledge base is queried for relevant information.
6. Relevant information is retrieved from the Amma's Kitchen knowledge base.
7. The AI Agent uses the retrieved information to generate a response.
8. The response is returned to the customer through the chat.

##  Testing

After completing the workflow, different questions were entered through the n8n chat interface.

The AI agent successfully processed the questions and returned responses using the connected workflow and knowledge base.

##  Security Note

API keys and other credentials should **never be published in a public GitHub repository**.

Credentials used during the project are intentionally excluded from this documentation.

##  What I Learned

Through this project, I gained practical exposure to:

* Agentic AI
* AI agents
* RAG
* Chunking
* Embeddings
* Vector databases
* Pinecone
* n8n workflow automation
* AI orchestration
* API integration
* HTTP requests
* Dynamic expressions in n8n
* Conversation memory
* Building and testing an AI customer-support workflow

##  Future Improvements

Possible future improvements include:

* Connecting the agent to a real customer-facing website
* Adding order-status functionality
* Connecting a database for customer and order information
* Adding automated order processing
* Integrating email or WhatsApp notifications
* Adding more tools to the AI Agent
* Improving response evaluation and testing
* Adding monitoring and error handling

##  Project

**Project:** Amma's Kitchen AI Customer Support Agent
**Built with:** n8n + Pinecone + RAG + OpenAI

This project represents my hands-on learning journey into **AI agents, RAG, vector databases, and workflow automation**.
