# InsightAI: 48" × 36" Academic Poster Presentation Guide
**Course:** CS 5542 – Big Data Analytics & Applications (UMKC)  
**Project:** Challenge 4 – Human–AI Co-Design with GraphRAG and Generative AI  
**Author:** Mahjabin Hossain  
**Poster Dimensions:** 48 inches wide × 36 inches high (Standard Academic Landscape Poster)

---

## 📁 Generated Poster Artifacts

| Format | File Location | Intended Usage |
| :--- | :--- | :--- |
| **PowerPoint (.pptx)** | [InsightAI_Poster_48x36.pptx](file:///Users/mahjabin/Downloads/InsightAI_Poster_48x36.pptx) | Editable conference submission format; vector shapes & tables |
| **Vector PDF (.pdf)** | [InsightAI_Poster_48x36.pdf](file:///Users/mahjabin/Downloads/InsightAI_Poster_48x36.pdf) | Ready-to-print format for FedEx/Staples/University plotters |
| **High-Res PNG (.png)** | [InsightAI_Poster_48x36_Preview.png](file:///Users/mahjabin/Downloads/InsightAI_Poster_48x36_Preview.png) | 4800 × 3600 px digital preview for immediate inspection |
| **Repository PPTX** | [InsightAI_Poster_48x36.pptx](file:///Users/mahjabin/Downloads/InsightAI/InsightAI_Poster_48x36.pptx) | Mirrored in project repository root |

---

## 🏛️ Poster Architecture & Structural Layout

The poster adopts a visual-first, dark slate aesthetic (`#0B0F19`) organized into three balanced vertical columns:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│  TOP HEADER BANNER (48" × 4.2"): Title, Subtitle, UMKC Affiliation, 4 Ribbon Metric Badges      │
├───────────────────────────────┬──────────────────────────────────┬───────────────────────────────┤
│ COLUMN 1: CONTEXT & GRAPH     │ COLUMN 2: METHODOLOGY & CLUSTERS │ COLUMN 3: RESULTS & GENAI APP │
│ 1. Problem Statement & Needs  │ 4. End-to-End Methodology        │ 7. Results (Mostly Tables!)   │
│    • 44.07% Delay Baseline    │    • Big Data Pipeline Graphic   │    • TABLE 1: Ablation Study  │
│    • 51.2% Interstate Spike   │    • 4 Coordinated Modalities    │    • TABLE 2: Disparities     │
│    • Dual Personas            │ 5. Community Subgraph Clustering │    • TABLE 3: GNN Ranking     │
│ 2. Data Source Profile        │    • Verified Hierarchy Graphic  │    • Key Empirical Findings   │
│    • 1,702 Olist Orders (DB)  │    • Physical Gateways Only      │ 8. Innovative GenAI App       │
│    • Schema Entities Table    │    • Isolated AI Recommendation  │    • Heavy Table Demonstration│
│ 3. Neo4j Knowledge Graph      │ 6. Optional Graph Learning (GNN) │    • Voice Audio + Rec Card   │
│    • 37 Nodes, 44 Edges       │    • 2-Layer GraphSAGE           │ 9. Co-Design Takeaways & ROI  │
│    • Zero Phantom Schema      │    • 2-Hop Message Passing Trace │    • 75% Context Reduction    │
└───────────────────────────────┴──────────────────────────────────┴───────────────────────────────┘
```

---

## 🎤 3-Minute Poster Pitch (Standing by Your Poster)

> *"Hello, everyone. Welcome to **InsightAI**. 
> 
> In e-commerce logistics across Brazil, delivery unpredictability is a massive driver of customer churn. As you can see in **Column 1**, our analysis of 1,702 orders from the Olist dataset uncovered a **44.07% baseline delay rate**, with interstate shipments from São Paulo to Bahia spiking to **51.2% delays**—a 6-fold disparity compared to local shipping. Bulky goods over 15kg also suffer a **28.4% pallet vibration damage rate**.
> 
> To solve this, we moved beyond flat vector search—which hallucinates on multi-hop routes 18.5% of the time—and built a **Zero-Phantom Neo4j Knowledge Graph** with 37 nodes and 44 directed operational relationships.
> 
> Moving to **Column 2**, our methodology partitions the national graph into three operational subgraphs: Southeastern Interstate Corridor ($C_1$), Heavy Goods ($C_2$), and Northeastern Feeder Networks ($C_3$), interconnected strictly by verified physical gateways like the São Paulo Central Hub. We also trained an optional **2-layer GraphSAGE GNN** that propagates corridor congestion risk, boosting critical delayed order detection by **+87.3%**.
> 
> Looking at our **Results in Column 3**, our tables highlight three key achievements:
> 1. **Table 1 (Ablation Benchmark):** Our Dynamic Community GraphRAG cuts LLM prompt context tokens by **75.8%** and drops latency to **76 milliseconds**, while slashing hallucinations to **0.8%**.
> 2. **Table 2 (Disparity Matrix):** Empirically proves the 6-fold delay gap that justifies our regional subgraph boundaries.
> 3. **Table 3 (GNN Ranking):** Demonstrates how neighborhood aggregation elevates high-risk orders while suppressing on-time shipments.
> 
> Finally, in **Section 8**, we demonstrate our **GenAI Multimodal Application**. When a customer asks: *'I want to buy this heavy wooden table. Will it arrive safely?'*, the system activates Subgraph $C_2$, synthesizes a **spoken voice briefing**, and recommends an **alternative solid oak table from a local São Paulo merchant**—cutting transit time from 18 days to 3 days, reducing damage hazard to **1.2%**, and saving the buyer **$18.50 in freight**!
> 
> Thank you, and I welcome your questions!"*

---

## 📊 Detailed Table Breakdown (For Answering Judge Questions)

### Table 1: System-Wide Retrieval & Architecture Ablation Benchmark
- **Judge Question:** *"Why is Dynamic Community GraphRAG better than traditional RAG or Whole-Graph GraphRAG?"*
- **Defense Answer:** 
  - *Traditional Vector RAG* lacks topological connectivity; it scores 18.5% hallucination and 64.2% faithfulness because it treats carriers, hubs, and products as disconnected text chunks.
  - *Whole-Graph GraphRAG* improves faithfulness to 88.4%, but dumps all 37 nodes into the LLM prompt (1,850 tokens), causing high latency (285ms) and token bloat.
  - *Dynamic Community GraphRAG* routes queries to domain-specific subgraphs (e.g., $C_2$ for heavy tables). It cuts context tokens by **75.8%** (520 tokens), speeds up retrieval to **76ms**, and slashes hallucinations to **0.8%**.

### Table 2: Empirical Regional Logistics Disparity Matrix
- **Judge Question:** *"How do you justify your three community subgraphs?"*
- **Defense Answer:**
  - São Paulo intrastate routes (SP $\rightarrow$ SP) take only 4.2 days with an 8.6% delay rate and a 4.3★ review score.
  - Interstate corridors (SP $\rightarrow$ RJ) jump to 14.8 days and 42.8% delay.
  - Long-haul northeastern corridors (SP $\rightarrow$ BA) take 22.5 days and reach a **51.2% delay rate**, causing reviews to crash to 1.6★.
  - These stark empirical breaks prove that one monolithic retrieval model cannot handle local couriers and long-haul linehauls simultaneously.

### Table 3: GNN 2-Hop Priority Re-Ranking vs. Isolated Matching
- **Judge Question:** *"What value did the optional Graph Neural Network add?"*
- **Defense Answer:**
  - Without the GNN, standard isolated feature matching gave delayed order `ORD_50090` (0.529) and on-time order `ORD_50042` (0.544) almost identical scores.
  - After 2-hop GraphSAGE message passing, `ORD_50090` absorbed its corridor delay history and was boosted to **0.991 (+87.3%)**, elevating it to Priority \#1. Fast orders were suppressed down to 0.099.

---

## 🛡️ Key Professor Feedback Addressed on the Poster

1. **Separated Factual KG from AI Recommendations:** `ACT_REROUTE` is isolated in an external green AI layer; it does not appear as a factual ground-truth graph entity.
2. **Physical Gateways Only:** Replaced abstract payment nodes with physical logistics entities: `HUB_SP_CENTRAL` and `LINEHAUL_GATEWAY`.
3. **Explicit Cypher Relationship Labels:** All edges display actual Cypher types (`SHIPPED_VIA`, `TRANSFERS_TO`, `CONTAINS`, `OPERATED_BY`).
4. **Visible Hierarchy:** Prominently displays the 2-level tree from National Graph down to $C_1$, $C_2$, and $C_3$.
5. **Results Dominated by Tables:** Three structured tables dominate the results column, replacing walls of text with quantitative benchmarks.
6. **GenAI Voice & Product Substitution:** Visualizes the full customer inquiry flow from spoken audio briefing to graph-grounded local seller substitution.
