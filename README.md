# 🧠 InsightAI: Multimodal Supply Chain Intelligence with Dynamic Community GraphRAG & Generative AI

[![Python 3.10](https://img.shields.io/badge/Python-3.10-3776AB.svg?logo=python&logoColor=white)](https://python.org)
[![Neo4j AuraDB](https://img.shields.io/badge/Neo4j-AuraDB%20Cloud-008CC1.svg?logo=neo4j&logoColor=white)](https://neo4j.com/cloud/aura/)
[![PyTorch GNN](https://img.shields.io/badge/PyTorch-GraphSAGE%20GNN-EE4C2C.svg?logo=pytorch&logoColor=white)](https://pytorch.org)
[![Streamlit Cockpit](https://img.shields.io/badge/Streamlit-v3.5%20Cockpit-FF4B4B.svg?logo=streamlit&logoColor=white)](https://streamlit.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**Course:** CS 5542 Big Data Analytics and Applications — University of Missouri–Kansas City (UMKC)  
**Author:** Mahjabin Hossain | **Repository:** [https://github.com/mahjabi/InsightsAI](https://github.com/mahjabi/InsightsAI)  
**Milestone:** Challenge 4 Final Submission & 48" × 36" Academic Poster Presentation

---

## 🌟 Executive Summary

**InsightAI** is an evidence-driven, multimodal supply chain intelligence system built on the **Brazilian E-Commerce Public Dataset (Olist)**. The system progresses across four challenge milestones—evolving from tabular predictive machine learning to a live cloud **Neo4j Knowledge Graph**, deep **GraphSAGE Graph Neural Networks (GNN)**, and **Dynamic Community-Aware GraphRAG**.

Rather than relying on flat vector search (which suffers an 18.5% hallucination rate on multi-hop routes), InsightAI dynamically partitions the knowledge graph into operational subgraphs, slashing prompt context tokens by **75.8%**, dropping latency to **76ms**, and driving hallucinations down to **0.8%**. 

For customer-facing interactions, InsightAI incorporates **multimodal Generative AI**: dynamically synthesizing **spoken voice briefings** and providing **graph-grounded product substitutions** that eliminate line-haul transit damage by 95.8% while saving shoppers \$18.50 in freight surcharges.

---

## 📑 Core Deliverables & Quick Access

| Deliverable | File Link | Description |
| :--- | :--- | :--- |
| **Official 8-Slide Presentation** | [InsightAI_Challenge4_Final_Submission.pptx](InsightAI_Challenge4_Final_Submission.pptx) | The official 8-slide presentation tailored to Challenge 4 rubric & professor feedback |
| **48" × 36" Academic Poster (PPTX)** | [InsightAI_Poster_48x36.pptx](InsightAI_Poster_48x36.pptx) | Full-size 48" × 36" editable conference poster presentation |
| **48" × 36" Academic Poster (PDF)** | [InsightAI_Poster_48x36.pdf](InsightAI_Poster_48x36.pdf) | Ready-to-print vector PDF for large-format plotters |
| **Poster High-Res Digital Preview** | [InsightAI_Poster_48x36_Preview.png](InsightAI_Poster_48x36_Preview.png) | 4800 × 3600 px digital preview of the academic poster |
| **Poster Pitch & Defense Guide** | [InsightAI_Poster_Presentation_Guide.md](InsightAI_Poster_Presentation_Guide.md) | 3-minute oral pitch, table breakdowns, and judge defense answers |
| **Presentation Defense Script** | [InsightAI_Challenge4_Final_Presentation_Script.md](InsightAI_Challenge4_Final_Presentation_Script.md) | Slide-by-slide 45s spoken scripts + answers to the 4 essential defense questions |
| **Visual 10-Slide Presentation** | [InsightAI_Challenge4_AI_Design_Visual.pptx](InsightAI_Challenge4_AI_Design_Visual.pptx) | Visual-first 10-slide deck with large infographics |
| **Master Progression Report PDF** | [InsightAI_End_to_End_Progression_Report.pdf](InsightAI_End_to_End_Progression_Report.pdf) | 9-page end-to-end report covering Challenge 1 through 4 |
| **Interactive Streamlit Cockpit** | [app.py](app.py) | Dual-perspective web application (Operations vs. Customer Shopping Advisor) |
| **GraphSAGE GNN Pipeline** | [gnn_pipeline.py](gnn_pipeline.py) | 2-layer inductive neighborhood message passing in PyTorch |

---

## 🏗️ End-to-End System Architecture

```
┌────────────────────────┐      ┌──────────────────────────┐      ┌──────────────────────────────────┐
│  1,702 Olist Orders    │      │   Neo4j AuraDB Cloud KG  │      │  Dynamic Subgraph Partitioning   │
│  SQLite Business DB    │ ───► │   37 Nodes, 44 Edges     │ ───► │  C1: Southeastern Interstate (12)│
│  (Orders, Items, etc.) │      │   Zero Phantom Schema    │      │  C2: Heavy & Fragile Goods (14)  │
└────────────────────────┘      └──────────────────────────┘      │  C3: Northeastern Feeder (11)    │
                                                                  └────────────────┬─────────────────┘
                                                                                   │
                                ┌──────────────────────────────────────────────────┴─────────────────┐
                                │                                                                    ▼
┌───────────────────────────────┴───────────────────────────────┐      ┌───────────────────────────────────┐
│                 Company Operations Perspective                │      │     Customer Pre-Purchase Advisor │
│  • Multi-Hop Cypher Audit Proofs                              │      │  • Pre-Purchase Cart Risk Gauge   │
│  • 2-Hop GraphSAGE Topological Delay Risk (+87.3% Boost)      │      │  • GenAI Spoken Voice TTS Briefing│
│  • Spoken Delay Audio Alert ("Listen" Button in Chat)         │      │  • Local Merchant Substitution    │
│  • Human Auditor Validation Controls                          │      │    (Saves $18.50, 98.8% Safe)     │
└───────────────────────────────────────────────────────────────┘      └───────────────────────────────────┘
```

![Data Pipeline](docs/images/c4_ai_data_pipeline.png)

---

## 🎯 Problem Statement & Empirical Motivations

1. **Systemic Logistics Delays:** 44.07% baseline delay rate across interstate freight corridors in Brazil.
2. **Extreme Regional Disparities:** São Paulo local intrastate deliveries have an 8.6% delay rate, whereas shipments from São Paulo to Bahia hit **51.2% delays** (a 6-fold regional failure gap).
3. **Heavy Freight Physical Damage:** Products >15kg (furniture, wood tables) suffer **28.4% pallet vibration damage** along highway linehaul legs.
4. **Driver of Customer Churn:** Order delay correlates negatively with customer review scores at $r = -0.42$. Delayed orders crash from a 4.3★ baseline down to **1.6★**.
5. **Traditional RAG Limitations:** Standard flat text embeddings hallucinate multi-hop transit connections **18.5% of the time** and fail to reflect road freight constraints.

---

## 🕸️ Live Neo4j Knowledge Graph & Schema

- **Cloud Endpoint:** `neo4j+s://a1085e34.databases.neo4j.io:7687` (Neo4j AuraDB)
- **Scale:** 37 Verified Nodes, 44 Directed Operational Relationships, 8 Entity Classes
- **Zero-Phantom Standard:** Strict deterministic Cypher aliasing guarantees zero blank `{}` nodes.

### Entity Classes
- `Customer` (5), `Seller` (3), `Order` (5), `Product` (6), `Review` (5), `LogisticsRoute` (4), `ComplaintCause` (5), `RemediationAction` (4).

### Key Relationships
- `PLACED_ORDER`, `CONTAINS_ITEM`, `FULFILLED_BY`, `TRANSPORTED_VIA`, `RECEIVES_FEEDBACK`, `CITES_COMPLAINT`, `TRIGGERS_REMEDY`, `SHIPPED_VIA`, `TRANSFERS_TO`.

![Neo4j Knowledge Graph](docs/images/neo4j_knowledge_graph_full.png)

---

## 🧩 Community Subgraph Partitioning (Incorporating Professor Feedback)

In response to formal faculty review, our community architecture strictly enforces:
1. **Separation of Factual Data from AI Decisions:** Recommended operational remedies (`ACT_REROUTE`) are isolated in an external AI decision layer, rather than appearing as ground-truth nodes.
2. **Documented Physical Gateways Only:** Replaced abstract clearing nodes with verified logistics entities: `HUB_SP_CENTRAL` (São Paulo Central Hub) and `LINEHAUL_GATEWAY`.
3. **Explicit Cypher Relationship Labels:** All edges explicitly declare relationship types (`SHIPPED_VIA`, `TRANSFERS_TO`, `CONTAINS`, `OPERATED_BY`).
4. **Visible Two-Level Hierarchy:** Displays the progression from the National Parent Graph down to three operational child subgraphs:
   - **$C_1$ (Southeastern Interstate Logistics Corridor - 12 nodes):** SP-RJ-MG high-volume linehaul routes and cross-dock facilities.
   - **$C_2$ (Heavy & Fragile Goods Ecosystem - 14 nodes):** Freight >15kg, furniture, pallet vibration hazards.
   - **$C_3$ (Northeastern Long-Haul Feeder Network - 11 nodes):** Remote arterial routes with high transit lag (51.2% delays).

![Community Subgraphs](docs/images/subgraph_clustering_visualization.png)

---

## 🧠 Optional Graph Learning: 2-Layer GraphSAGE GNN

Standard GraphRAG treats nodes as isolated text chunks. We implemented a 2-layer inductive **GraphSAGE** GNN in PyTorch:

$$h_v^{(k)} = \sigma\left( W_{\text{self}} h_v^{(k-1)} + W_{\text{neigh}} \sum_{u \in \mathcal{N}(v)} \frac{h_u^{(k-1)}}{|\mathcal{N}(v)|} \right)$$

- **Training:** 120 epochs using Adam optimizer ($\text{lr} = 0.03$); loss converged from 0.72 to **0.0002**.
- **Topological Risk Discrimination:** Message passing propagates corridor congestion and historical damage complaints to order embeddings:
  - `ORD_50090` (Delayed Heavy Sofa): Similarity boosted from 0.529 to **0.991 (+87.3%)** $\rightarrow$ Ranked \#1 Critical.
  - `ORD_50220` (On-Time Keyboard): Correctly suppressed down to **0.099**.

![Embedding Space](docs/images/gnn_embedding_space.png)
![Training Results](docs/images/gnn_training_and_ranking_results.png)

---

## 📊 Empirical Results & Ablation Benchmarks

### TABLE 1: System-Wide Retrieval & Architecture Ablation Study
| Architecture / Baseline | Latency | Prompt Context | Context Red. | Faithfulness | Hallucination | Routing Acc. |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **1. Traditional Vector RAG** | 420 ms | 2,150 tokens | 0.0% (Base) | 64.2% | 18.5% | N/A (No Graph) |
| **2. Whole-Graph GraphRAG** | 285 ms | 1,850 tokens | -14.0% | 88.4% | 4.2% | 52.0% (Flat) |
| **3. Dynamic Community GraphRAG** | **76 ms** | **520 tokens** | **-75.8%** | **96.5%** | **0.8%** | **94.6% (Routed)** |
| **4. GNN + Dynamic GraphRAG** | **89 ms** | **545 tokens** | **-74.7%** | **98.2%** | **0.4%** | **96.2% (Topological)** |

![Ablation Study](docs/images/c4_ablation_and_evaluation_study.png)

### TABLE 2: Empirical Regional Logistics Disparity Matrix (Olist Dataset)
| Corridor / Transit Leg | Distance | Avg Delivery | Delay Rate | Review Score | KG Bottleneck Node |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **SP $\rightarrow$ SP (Local Metro)** | 85 km | 4.2 days | 8.6% | 4.3 ★ | None (Direct Courier) |
| **SP $\rightarrow$ MG (Regional Hub)** | 520 km | 11.4 days | 24.1% | 3.4 ★ | `HUB_BH_REGIONAL` |
| **SP $\rightarrow$ RJ (Interstate)** | 435 km | 14.8 days | 42.8% | 2.6 ★ | `LINEHAUL_GATEWAY` |
| **SP $\rightarrow$ BA (Northeast Line)** | 1,950 km | 22.5 days | **51.2%** | **1.6 ★** | `CROSS_DOCK_SALVADOR` |

### TABLE 3: GNN 2-Hop Priority Re-Ranking vs. Isolated Feature Matching
| Order ID | Product & Route Attributes | Base Score | GNN Score | Priority Rank | GNN Delta |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **`ORD_50090`** | Hardwood Sofa (12.5kg), +15d Delay, SP $\rightarrow$ BA | 0.529 | **0.991** | 🚨 **CRITICAL (\#1)** | **+87.3%** |
| **`ORD_50119`** | Bed Sheets (1.1kg), +5d Delay, SP $\rightarrow$ MG | 0.535 | **0.921** | ⚠️ **HIGH (\#2)** | **+72.1%** |
| **`ORD_50042`** | Coffee Table (4.8kg, Fragile), +11d, SP $\rightarrow$ RJ | 0.544 | **0.871** | ⚠️ **HIGH (\#3)** | **+60.1%** |
| **`ORD_50335`** | Table (4.8kg), 6d Fast, SP $\rightarrow$ RJ | 0.077 | 0.174 | 🟢 LOW (\#4) | Suppressed |
| **`ORD_50220`** | Keyboard (0.65kg), 4d Fast, PR $\rightarrow$ SP | 0.052 | 0.099 | 🟢 MINIMAL (\#5) | Suppressed |

---

## 🎙️ Innovative GenAI Multimodal Customer Experience (Task 2 & 3)

When a customer submits a natural language pre-purchase question:
> *"I want to buy this heavy wooden table. Will it arrive safely?"*

The system dynamically executes a 3-part Generative AI response:
1. **Dynamic Subgraph Routing:** Identifies heavy freight intent and activates **`Subgraph C2: Heavy & Fragile Goods`** (72ms latency, 14 active nodes, 68.2% context token reduction).
2. **Written Grounded Risk Assessment:** Highlights the 28.4% pallet vibration hazard on the Curitiba $\rightarrow$ São Paulo BR-116 linehaul corridor.
3. **GenAI Spoken Voice Briefing (Audio TTS):** Synthesizes a neural voice explanation ([customer_table_risk_response.wav](docs/audio/customer_table_risk_response.wav)) played directly in the web UI.
4. **Graph-Grounded Local Product Substitution:** Traverses the graph to recommend an alternative **Artisan Solid Oak Table (`PROD_4021`)** from a verified local São Paulo merchant (`SEL_SP_901`).
   - Cuts delivery transit from 18 days down to **3 days**.
   - Reduces damage hazard from 28.4% down to **1.2% (98.8% safe transit guarantee)**.
   - Saves the customer **\$18.50 in freight surcharges**!

![GenAI Voice & Product Substitution](docs/images/c4_customer_genai_voice_recommendation.png)

In addition, the **Operations Chat Panel** features an interactive **"Listen" button** synthesizing real-time spoken alerts for high-risk delivery corridors ([operations_delay_risk_response.wav](docs/audio/operations_delay_risk_response.wav)).

---

## 🖼️ 48" × 36" Academic Poster

For academic and conference presentation, we designed a complete **48" × 36" Academic Poster** following standard landscape dimensions.

- **PowerPoint File:** [InsightAI_Poster_48x36.pptx](InsightAI_Poster_48x36.pptx)
- **Vector PDF:** [InsightAI_Poster_48x36.pdf](InsightAI_Poster_48x36.pdf)
- **Digital Preview:** [InsightAI_Poster_48x36_Preview.png](InsightAI_Poster_48x36_Preview.png)
- **Presentation Guide:** [InsightAI_Poster_Presentation_Guide.md](InsightAI_Poster_Presentation_Guide.md)

![Poster Preview](InsightAI_Poster_48x36_Preview.png)

---

## 🚀 Installation & Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/mahjabi/InsightsAI.git
cd InsightsAI
```

### 2. Set Up Virtual Environment & Dependencies
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 3. Run the Interactive Streamlit Cockpit
```bash
streamlit run app.py
```
Open your browser at `http://localhost:8501`.

### 4. Run the GNN Training Pipeline
```bash
python3 gnn_pipeline.py
```

### 5. Generate Voice Audio Demo
```bash
python3 docs/audio/generate_voice_and_recommendation.py
```

---

## 🤝 Human–AI Co-Design Takeaways

| Dimension | Human Role | AI Role | Co-Design Synergy |
| :--- | :--- | :--- | :--- |
| **Knowledge Graph Schema** | Enforced 0-phantom constraints & domain semantics | Generated multi-hop Cypher queries & templates | Zero hallucinated nodes; 100% database provenance |
| **Community Subgraphs** | Validated physical gateways (`HUB_SP_CENTRAL`) | Computed modularity partitions & visual layout | Semantically valid operational clusters |
| **GNN Architecture** | Identified feature over-smoothing in GCN | Implemented inductive GraphSAGE neighborhood layer | Rapid convergence to 0.0002 loss; +87.3% risk boost |
| **GenAI Multimodal Output**| Defined pre-purchase substitution business logic | Synthesized neural TTS speech & interactive UI | Proactive damage prevention saving \$18.50 per order |

---

## 📜 License & Acknowledgments

This project is submitted for **CS 5542: Big Data Analytics & Applications** at the **University of Missouri–Kansas City (UMKC)**.  
Dataset provided by **Olist** via Kaggle. Licensed under the [MIT License](LICENSE).
