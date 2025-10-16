🧠 Hypergraph-Enhanced T5 for Multi-Hop Question Generation

This repository contains the implementation of a Hypergraph-Enhanced T5 model designed for multi-hop question generation (QG) from unstructured text.
The model integrates a custom Hypergraph Transformer Encoder with a T5 decoder, enabling reasoning across multiple context sentences through dynamic hyperedge connections.

🚀 Overview

Traditional Question Generation models struggle with multi-hop reasoning, where a question requires combining information from multiple sentences or facts.
Our model introduces a Hypergraph Encoder that represents sentences and entities as nodes, linking them via dynamic hyperedges based on semantic similarity.

These hypergraph-based representations are fed into a T5 decoder to generate coherent, contextually relevant, and reasoning-rich questions.

🧩 Architecture

Main Components:

Frozen T5 Encoder – Generates contextual embeddings (768-dim).

Hypergraph Construction – Builds top-K hyperedges between support and distractor facts based on cosine similarity.

Custom Hypergraph Encoder – Stack of 3 Hypergraph Transformer layers performing attention over hyperedges.

Linear Projection – Projects 256-dim hypergraph outputs to 768-dim for T5 decoder input.

T5 Decoder – Generates the final question using beam search.

📊 Key Innovation:
Unlike standard T5, which treats text linearly, this model leverages graph-based reasoning to capture higher-order relationships between facts.

📁 Project Structure

├── models/
│   └── hypergraph_qg_model.py            # Main model combining encoder + T5
│
├── modules/
│   ├── hypergraph_encoder.py             # Stacked hypergraph transformer layers
│   └── hypergraph_transformer_layer.py   # Attention and message passing logic
│
├── train.py                              # Model training script
├── evaluate.py                           # Evaluation and generation script
├── requirements.txt                      # Dependencies
├── Dockerfile                            # Docker configuration
└── README.md                             # You’re here 🙂

⚙️ Installation

Clone the repository

git clone https://github.com/<your-username>/Hypergraph-T5-QG.git
cd Hypergraph-T5-QG


Install dependencies

pip install -r requirements.txt


(Optional) Build Docker image

docker build -t hypergraph-qg .

🧪 Usage
▶️ Train the model
python train.py

🧠 Evaluate / Generate Questions
python evaluate.py

🐳 Run via Docker
docker run -it hypergraph-qg

📊 Results
Model	BLEU	ROUGE-L	BERTScore
Vanilla T5	0.28	0.42	0.85
Hypergraph-T5 (ours)	0.35	0.49	0.89

The model demonstrates improved reasoning and coherence on HotpotQA, especially in multi-hop question scenarios.

💡 Key Innovations
Gap	Standard GCN / T5	Our Model (Hypergraph-T5)
Graph Structure	Static pairwise edges	Dynamic hyperedges
Higher-Order Relations	Pairwise only	N-ary relationships
Reasoning Path	Fixed	Adaptive traversal
Scalability	Over-smoothing	Sparse top-K hyperedges
Input Type	Flat sentences	Context-aware embeddings
📦 Dockerized Product

This repository includes a complete Docker setup:

✅ Pre-installed dependencies

✅ Automatic execution of evaluate.py

✅ Portable and reproducible environment

Build and export the Docker image for deployment or submission:

docker save hypergraph-qg -o hypergraph_qg.tar
