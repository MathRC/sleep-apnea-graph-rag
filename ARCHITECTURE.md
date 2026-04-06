# Architecture

## System Design

### Phase 1: POC (Weeks 1-2)
- Collect 1000-5000 posts from r/sleepapnea
- Validate data quality and relevance
- Establish baseline metrics

### Phase 2: MVP (Weeks 3-4)
- Full embedding pipeline
- PostgreSQL + pgvector setup
- Retrieval evaluation (nDCG@10 > 0.60)
- Neo4j knowledge graph construction

### Phase 3: Scale (Weeks 5+)
- 50k+ documents
- AWS deployment
- Multi-tenant API
- Production monitoring

## Data Flow
Reddit Posts (PRAW)
↓ (Validation)
PostgreSQL (raw posts)
↓ (Chunking)
Embeddings (SentenceTransformer)
↓ (Indexing)
pgvector (vector search)
↓ (Context enrichment)
Neo4j (knowledge graph)
↓ (Retrieval + Generation)
Claude API → Answer
↓ (Evaluation)
RAGAS Metrics

## Key Decisions

### Why PostgreSQL + pgvector?
- No vendor lock-in
- ACID guarantees for medical data
- Cost-effective at POC scale
- Scales to MVP with RDS Multi-AZ

### Why Neo4j?
- Relationship queries 10-100x faster than SQL
- Natural fit for medical knowledge (symptom → diagnosis → treatment)
- Graph patterns capture treatment hierarchies

### Why Claude API?
- Best quality for medical domain
- Can use Sonnet in production for cost optimization
- Easily evaluable with RAGAS

## Metrics & Success Criteria

### Retrieval Quality
- nDCG@10 ≥ 0.60
- P@1 ≥ 0.75
- MAP@10 ≥ 0.55

### Generation Quality
- Faithfulness ≥ 0.80 (RAGAS)
- Answer Relevance ≥ 0.75
- 100% evidence citation

### System Health
- Query latency P95 < 3s
- Cost per query < $0.10
- Success rate ≥ 99%