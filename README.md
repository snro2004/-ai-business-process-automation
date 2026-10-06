# AI Business Process Automation

**Personal / Learning Project**

An AI-powered employee policy assistant that demonstrates how Retrieval-Augmented Generation (RAG) and workflow automation can turn company policy documents into a searchable knowledge base while preserving source grounding and human review for exceptions.

## Business Problem

Employees often spend time searching policy documents or asking repetitive questions. Manual lookup can be slow, inconsistent, and difficult to scale.

This project explores a business-oriented solution that automatically ingests policy PDFs, creates a searchable knowledge base, answers employee questions using retrieved policy content, and provides a foundation for routing higher-risk requests to a human workflow.

## Solution

**Policy ingestion:** PDF added to a controlled folder → document text extracted → text embedded → vectors stored in Pinecone.

**Employee Q&A:** Employee question → AI agent → relevant policy content retrieved from Pinecone → answer generated from retrieved context → source-oriented response.

## Architecture

```text
POLICY INGESTION
Policy PDF
   ↓
Google Drive Folder
   ↓
n8n File Trigger
   ↓
PDF Text Extraction
   ↓
OpenAI Embeddings
   ↓
Pinecone Vector Database

EMPLOYEE QUESTION
Employee
   ↓
n8n Chat Trigger
   ↓
AI Agent
   ↓
Pinecone Retrieval
   ↓
Relevant Policy Context
   ↓
LLM Response
   ↓
Employee Answer / Human Review When Needed
```

## Business Objectives

- Reduce time spent locating policy information.
- Reduce repetitive manual policy lookups.
- Provide answers grounded in approved source documents.
- Identify requests that should remain subject to human judgment.
- Demonstrate how AI can support a business process without replacing necessary controls.

## Technology

- n8n — workflow orchestration
- Google Drive — controlled document intake
- OpenAI embeddings — semantic representation
- Pinecone — vector knowledge base
- OpenRouter / DeepSeek — language-model response generation
- GitHub — project documentation and version control

## Repository Guide

| Folder | Purpose |
|---|---|
| `01-project-overview` | Business problem, objectives, scope and assumptions |
| `02-current-state` | Manual process and baseline measurement framework |
| `03-solution-design` | Future-state workflow, architecture and controls |
| `04-testing-and-results` | Test plan, test cases and results framework |
| `05-ai-prompts` | Prompt-development examples and independent review prompts |
| `06-artifacts` | Sample inputs, outputs and screenshot guidance |
| `07-reflection` | Lessons learned and possible next steps |
| `policies` | Fictional policy used by the demonstration |
| `workflow` | Sanitized n8n workflow template |

## Measurement Approach

This repository does **not** claim production savings. A real implementation would compare the manual and automated processes using the same representative cases and measure total task time, manual task time, number of manual steps, errors, exceptions, and required human interventions.

Potential labor value can then be estimated as:

`Annual Labor Savings = Annual Hours Saved × Weighted Average Hourly Compensation`

A full business case should also account for implementation cost, software licensing, ongoing support, error-related cost avoidance, payback period, and ROI.

## Controls

The design intentionally keeps human judgment in the process. The assistant should not invent policy, make employment decisions, or treat generated text as authoritative when supporting policy content cannot be retrieved. Sensitive, ambiguous, or exception-based requests should be routed for human review.

## Security

The workflow included here is sanitized for public GitHub use. It contains no API keys, credential IDs, private folder identifiers, webhook identifiers, or n8n instance identifiers. Credentials should be configured locally using n8n credential management and environment-specific configuration.

## Skills Demonstrated

Business Analysis • Process Improvement • AI • Automation • Requirements Analysis • Workflow Design • RAG • Testing • Controls • Documentation • Communication

## Key Takeaway

The primary lesson is that useful business automation starts with understanding the process. AI should be applied where it creates measurable value, while exceptions, sensitive decisions, and accountability remain appropriately controlled by people.
