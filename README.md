# Awesome-Real-Time-Vector-Database-Sharding

## Top Real-Time Vector Database Sharding Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Dynamic Scaling, High-Throughput Semantic Search & Enterprise Vector Sharding*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Real-Time Vector Database Sharding**. These tools enable vector databases to scale horizontally across multiple nodes — sharding embeddings, replicating for high availability, and rebalancing shards dynamically — to support billions of vectors with low-latency semantic search for RAG, recommendation, and AI applications.

**Examples** include Pinecone, Qdrant, Milvus, Weaviate, Chroma, Vespa, Marqo, MyScale, Typesense, and Turbopuffer (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom sharding strategies, and transparent distributed vector search — ideal for AI engineers prioritizing data sovereignty, developers building RAG infrastructure, and teams avoiding per-vector pricing.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Pinecone](https://www.pinecone.io/)**  
  Fully managed, serverless vector database with automatic sharding and replication. Scales to billions of vectors without manual cluster configuration or node monitoring [citation:2]. Zero-ops model with REST API, making it the reference choice for teams prioritizing operational simplicity.

- **[Qdrant Cloud](https://qdrant.tech/cloud/)**  
  Managed version of Qdrant with distributed clusters, Raft-based consensus, zero-downtime scaling, and automatic failover [citation:5]. Optional GPU acceleration available. Enterprise-grade compliance and observability for production RAG workloads.

- **[Zilliz Cloud (Milvus)](https://zilliz.com/)**  
  Managed Milvus service with disaggregated cloud-native architecture. Separates stateless compute (coordinator, query, data nodes) from storage (S3/MinIO, etcd) [citation:16]. Built for billion-scale vector workloads with horizontal sharding.

- **[Weaviate Cloud](https://weaviate.io/)**  
  Managed Weaviate with built-in sharding and replication. Users configure shard and replica counts; Weaviate automatically manages data distribution [citation:12]. Prioritizes ease of deployment and high availability over fine-grained component control.

- **[Vespa Cloud](https://vespa.ai/)**  
  Managed version of Yahoo's Vespa engine with native vector search, lexical search (BM25), and structured data queries. Commercial open-source with strong hybrid search support [citation:18].

- **[Marqo](https://www.marqo.ai/)**  
  Tensor-based cloud-native search and analytics engine with sharding support and HNSW indexing [citation:18]. Focused on multimodal vector search for e-commerce and media.

- **[MyScale](https://myscale.com/)**  
  SQL-native vector database built on ClickHouse with vector search capabilities and sharding for analytics workloads.

- **[Typesense](https://typesense.org/)**  
  Typo-tolerant search engine with vector search support and distributed sharding for high-throughput semantic search.

- **[Turbopuffer](https://turbopuffer.com/)**  
  Serverless vector database built on object storage with automatic scaling and cost optimization through usage-based billing [citation:5].

- **[Chroma Cloud](https://www.trychroma.com/)**  
  Managed version of Chroma with serverless cloud architecture for moderate-scale deployments with high write throughput [citation:5].

## Open-Source GitHub Projects

- **[Milvus](https://github.com/milvus-io/milvus)**  
  **The most mature open-source distributed vector database for billion-scale workloads.** Cloud-native architecture that separates stateless compute (coordinator, query nodes, data/streaming nodes) from storage (S3/MinIO for segments, etcd for metadata, write-ahead log) [citation:12][citation:16]. Features component-based scaling — scale data nodes independently from query nodes when indexing throughput bottlenecks emerge [citation:12]. QueryNodes are evenly distributed across physical nodes in Kubernetes clusters [citation:8]. Apache 2.0 licensed.

- **[Qdrant](https://github.com/qdrant/qdrant)**  
  **The leading open-source vector database for filter-heavy workloads under 50M vectors.** Rust-based with full clustering support, Raft-based consensus, horizontal sharding, and automatic failover [citation:5]. Supports payload-aware HNSW traversal, hybrid search (dense + sparse), pre-filtering for predicated queries, and sub-millisecond query latency [citation:5][citation:11]. Optional GPU acceleration. Apache 2.0 licensed.

- **[Weaviate](https://github.com/weaviate/weaviate)**  
  **Open-source vector database with first-class hybrid search.** Supports sharding and replicas for horizontal scaling — users configure shard and replica counts, and Weaviate manages data distribution automatically [citation:12]. Uses HNSW + LSM-Tree for vector index and inverted index over keywords and attributes [citation:11]. Eventual consistency model with BSD licensing [citation:18]. Pre-filtering for predicated search queries.

- **[Chroma](https://github.com/chroma-core/chroma)**  
  **Open-source vector database optimized for developer velocity and prototyping.** Uses HNSWlib and DuckDB, based on ClickHouse [citation:18]. Handles millions of vectors on a single node with sufficient RAM, but has **no built-in horizontal scaling** — migration to Qdrant, Milvus, or pgvector is required beyond single-machine capacity [citation:9]. Apache 2.0 licensed. Best for embedded applications and mid-scale deployments.

- **[Vespa](https://github.com/vespa-engine/vespa)**  
  **Yahoo's open-source engine for vector, lexical, and structured search.** Supports HNSW and BM25 with disk-backed and in-memory structures [citation:18]. Native hybrid search with strong support for rich filtering. Apache 2.0 licensed. Used in large-scale search and recommendation systems.

- **[NodeDB](https://crates.io/crates/nodedb-bridge)**  
  **Distributed hybrid database for multi-modal AI workloads.** Seven engines (Vector, Graph, Document, Columnar, Key-Value, Full-Text) in a single Rust binary sharing the same storage and query planner [citation:15]. Features HNSW with SQ8/PQ/IVF-PQ quantization, adaptive bitmap filtering, multi-Raft consensus, Thread-per-Core data plane with io_uring, and **automatic shard balancing** [citation:15]. Runs in Origin (server), Local, or embedded Lite (WASM) modes with identical application code.

- **[RuVector](https://github.com/ruvnet/RuVector)**  
  **Open-source vector database with GNN-enhanced search and auto-sharding.** Features **auto-sharding via consistent hashing** with shard migration, Raft consensus for metadata, and multi-master async replication with <100ms replication lag [citation:3][citation:6]. Tracks access patterns to automatically promote/demote vectors between hot/warm/cold tiers [citation:20]. Includes Cypher graph queries, hyperedges, 39 attention mechanisms, and 2-32x tensor compression. Claims 61µs p50 latency and 1M vectors/min parallel HNSW construction [citation:20]. MIT licensed.

- **[pgvector](https://github.com/pgvector/pgvector)**  
  **Open-source vector similarity search for PostgreSQL.** Adds vector indexing and ANN search to existing Postgres deployments, inheriting backups, replication, monitoring, and access control for free [citation:14]. Handles <1M vectors effectively; beyond that, dedicated engines are recommended [citation:14]. Best for teams already operating PostgreSQL who want one fewer system to manage.

- **[Vald](https://github.com/vdaas/vald)**  
  **Cloud-native distributed approximate nearest neighbor (ANN) dense vector search engine** from Yahoo Japan [citation:18]. Uses NGT (Neighborhood Graph and Tree) for vector search with distributed indexing and asynchronous indexing support. Apache 2.0 licensed.

### Additional Strong Open-Source Options

- **[VecGrid](https://pypi.org/project/vecgrid/)** — Distributed HNSW with partitioned graphs (default 271 partitions by consistent hashing of vector ID). Scatter-gather search across all partitions with coordinator merging partial results [citation:1]. Achieves 95-98% recall@10 at 1M vectors. Counterintuitively improves recall for small-to-medium datasets because each partition's graph is denser [citation:1].
- **[HAKES](https://arxiv.org/abs/2505.12524)** — Hybrid ANN with key-enabled sharding for distributed vector databases. Achieves 0.98 recall for k=10 [citation:8].
- **[LanceDB](https://github.com/lancedb/lancedb)** — Embedded vector database for local prototyping and multimodal applications [citation:19].
- **FAISS** — Facebook's library for efficient similarity search and clustering. Single-node only; sharding must be implemented manually [citation:13].
- **DiskANN (Milvus)** — Disk-backed index for billion-scale vectors, reducing memory footprint compared to in-memory HNSW [citation:14].

**Frameworks for building custom systems**: Combine **Milvus** for billion-scale disaggregated architecture, **Qdrant** for filter-heavy workloads under 50M vectors, **Weaviate** for first-class hybrid search, **VecGrid** or **RuVector** for partitioned HNSW with scatter-gather or GNN-enhanced search, and **pgvector** for existing PostgreSQL teams to build a complete self-hosted vector sharding stack.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Vector database sharding tools must comply with data protection regulations (GDPR, CCPA), industry standards (SOC 2), and organizational data governance requirements. Recall and latency benchmarks are workload-dependent and should be validated against your specific data distribution and query patterns.
- Self-hosted open-source solutions require proper Kubernetes orchestration, high-IOPS persistent storage (AWS io2/local NVMe), memory budgeting for HNSW graphs, and ongoing monitoring [citation:16].

---

**Made for AI engineers, RAG developers, platform teams, and developers building high-throughput semantic search infrastructure.**  
Let's make real-time vector database sharding more open, scalable, and data-sovereign.
