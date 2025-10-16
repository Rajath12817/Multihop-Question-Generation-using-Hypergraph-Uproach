# 🧠 Hypergraph-Enhanced T5 for Multi-Hop Question Generation

This repository presents an advanced **Hypergraph-Enhanced T5 model** for **multi-hop question generation (QG)** from unstructured text.  
The model integrates a **custom Hypergraph Transformer Encoder** with a **T5 decoder**, enabling reasoning across multiple context sentences through dynamic hyperedge connections.

---

## 🚀 Overview

Traditional Question Generation models struggle with **multi-hop reasoning**, where a question depends on connecting multiple facts or sentences.  
Our model introduces a **Hypergraph Encoder** that represents facts as nodes and dynamically connects them with **hyperedges** based on semantic similarity.  

The encoded representations are then decoded by a **T5 model** to produce coherent, context-aware questions.

---

## 🧩 Architecture

**Main Components**
1. 🧊 **Frozen T5 Encoder** – Extracts 768-dim embeddings from contextual sentences.  
2. 🕸 **Hypergraph Construction** – Builds top-K hyperedges between support and distractor facts using cosine similarity.  
3. 🔺 **Custom Hypergraph Encoder** – A stack of 3 Hypergraph Transformer layers performing attention over hyperedges.  
4. 🔁 **Linear Projection** – Maps 256-dim encoder output to 768-dim for T5 decoder compatibility.  
5. 🧠 **T5 Decoder** – Generates final questions using beam search decoding.

📊 *Key Difference:*  
Unlike vanilla T5, which treats text sequentially, this model performs **graph-based reasoning** over sentence relationships to improve multi-hop understanding.

---

## 📁 Project Structure

