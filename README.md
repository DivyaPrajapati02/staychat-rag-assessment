# StayChat AI - RAG Based Hotel Q&A System

## Overview
This project implements a Retrieval-Augmented Generation (RAG) system for answering hotel-related questions.

## Dataset
- 40 synthetic hotel documents
- Includes amenities, policies, locations, and reviews

## Tech Stack
- Python
- Sentence Transformers
- FAISS
- Pandas
- NumPy

## Preprocessing
Documents were cleaned and converted into structured text chunks.

Chunk Strategy:
- One hotel record = one chunk
- Chunk overlap = 0

Reason:
Each hotel record already contains complete contextual information.

## Retrieval
Embedding Model:
- all-MiniLM-L6-v2

Vector Database:
- FAISS

Top-k Retrieval:
- k = 3

## Example Queries
1. Which hotels have free WiFi and complimentary breakfast?
2. What is the cancellation policy of Hotel 10?
3. Suggest a hotel with excellent reviews near the beach.

## Evaluation

Metric Used:
Precision@k

Results:
- Q1 Precision@3 = 1.0
- Q2 Precision@1 = 1.0
- Q3 Precision@3 = 1.0

## Hallucination Control

Technique:
Strict Context-Based Answering

The system only answers from retrieved documents and returns:

"I could not find that information in the dataset."

when sufficient information is unavailable.

## Failure Case

Pure semantic retrieval occasionally retrieved similar hotels instead of the exact hotel requested.

Solution:
Added exact hotel matching before semantic search.

## Limitations

- Small synthetic dataset
- No external hotel database
- Simple answer generation
