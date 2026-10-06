# Automation Design

## Document Ingestion

1. An approved policy PDF is placed in the designated source folder.
2. n8n detects the new file.
3. The file is downloaded and its text is extracted.
4. Text is divided into retrievable document chunks by the vector-store integration.
5. Embeddings are created.
6. The content is stored in Pinecone under the configured knowledge-base namespace.

## Question Answering

1. An employee submits a question.
2. The AI agent receives the question.
3. The retrieval tool searches the policy knowledge base.
4. Relevant policy context is returned to the agent.
5. The language model produces an answer based on that context.
6. Questions that lack sufficient support or require judgment should be escalated rather than guessed.
