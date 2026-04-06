# Sleep Apnea Graph RAG

A Retrieval-Augmented Generation system that analyzes sleep apnea clinical discussions 
to extract treatment patterns and generate evidence-based context for medical professionals.

## Motivation

Sleep apnea has 1000+ treatment discussions across Reddit, clinical forums, and research. 
Current tools don't synthesize this knowledge. This RAG system will:
- Ingest clinical discussions (Reddit r/sleepapnea, forums, etc.)
- Extract entities and relationships (treatments, symptoms, outcomes)
- Build a knowledge graph of sleep apnea treatment patterns
- Generate evidence-grounded clinical context on-demand

## Architecture

### Core Components
1. **Data Pipeline**: Scrape Reddit + clinical sources
2. **Embedding Layer**: Convert text to vectors (384-dim with all-MiniLM-L6-v2)
3. **Storage**: PostgreSQL + pgvector for embeddings, Neo4j for knowledge graph
4. **Retrieval**: Vector search + graph-based context enrichment
5. **Generation**: Claude API for evidence-grounded answers
6. **Evaluation**: Multi-layer metrics (RAGAS, nDCG, medical accuracy)

### Tech Stack
- Python 3.11+
- PostgreSQL + pgvector
- Neo4j
- Claude API (Anthropic)
- PRAW (Reddit data collection)
- Sentence-Transformers (embeddings)
- FastAPI (REST endpoints, future)

## Data Sources

**Public Data Only:**
- Reddit r/sleepapnea subreddit (public posts)
- Purpose: Research and analysis

## Privacy & Ethics

- No user identification (anonymized post content only)
- No data redistribution
- Research-only use case
- Compliant with Reddit's Terms of Service

## Installation
```bash
# (Coming after Reddit API approval)
pip install -r requirements.txt
```

## Usage
```bash
# (Coming after Reddit API approval)
python src/main.py
```

## Development Status

🟡 **POC Phase**: Awaiting Reddit API approval to begin data collection.

Once approved, the roadmap is:
1. Week 1-2: Data ingestion and validation (1000-5000 posts)
2. Week 3: Embedding generation and pgvector setup
3. Week 4: Retrieval pipeline and evaluation
4. Week 5: Knowledge graph construction (Neo4j)
5. Week 6+: Generation, optimization, and scaling

## Responsible Use

- This system collects data for research purposes only
- No automated posting or bot accounts
- Respects Reddit's rate limits and Terms of Service
- Transparent about data usage

## License

MIT License (see LICENSE file)

## Contact

Questions? Open an issue or discuss on r/sleepapnea

---

**Status:** Waiting for Reddit API approval to proceed with development.