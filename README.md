# 🌐 Regional Trade Integration & Network Analysis Dashboard

**An interactive dashboard applying graph theory and network analysis to bilateral trade data — mapping how Asia's trade architecture has structurally evolved from 2000 to 2024 and comparing with Africa as this research is primarily directed towards Africa and AfCTA.**

🔗 **Live Dashboard:** [swaraj1313.github.io/Regional-Trade-Integration](https://swaraj1313.github.io/Regional-Trade-Integration/index.html)

**Data Source:** IMF Direction of Trade Statistics (DOTS)

---

## Overview

Most trade analysis focuses on *how much* countries trade — volumes, values, growth rates. This project asks a fundamentally different question:

> **How is trade structurally organised — and how has that organisation changed over 24 years?**

By transforming bilateral trade data into directed networks and applying graph-theoretic metrics, the dashboard surfaces patterns that value-based analysis cannot capture: which countries are structurally central vs. peripheral, where regional blocs are forming, which economies are "throughways" vs. "endpoints", and where integration is deepening or stalling.

The methodology draws on techniques from **network science** — Eigenvector Centrality, Louvain Community Detection, Force-Atlas-2 layout, and structural density metrics — applied to the IMF DOTS bilateral trade matrix across 6 benchmark years (2000, 2005, 2010, 2015, 2020, 2024).

---

## Dashboard Modules

### 1. 🕸️ Asia Trade Network 2024
**[View](https://swaraj1313.github.io/Regional-Trade-Integration/visuals/Asian_Trade_2024.html)**

An interactive force-directed network graph of Asia's trade architecture in 2024.

**Methodology:**
- **Trade Intensity Index (TII)** — normalises bilateral trade flows to identify relationships that are disproportionately strong relative to global trade shares, correcting for country size
- **Louvain Community Detection** — identifies dense trade blocs where countries trade more intensely with each other than with outsiders; colours represent algorithmically detected communities
- **Force-Atlas-2 layout** — positions countries physically based on trade gravity; countries that trade heavily are pulled closer together; peripheral countries with few connections appear on the outer edges
- **Node size** — scaled to total regional exports (Out-Degree Centrality); larger nodes act as "gravity wells"

**Key findings:**
- **Blue cluster** — North-East Asian core (China, Japan, Korea); China functions as the dominant gravity well
- **Green cluster** — ASEAN manufacturing zone (Singapore, Malaysia, Indonesia); Singapore and Malaysia act as bridges between ASEAN and the North-East Asian core
- **Orange cluster** — Central Asian peripheral group with weaker integration into the main network
- Countries physically far from the centre are structurally decoupled — fewer connections means less gravitational pull toward the core

---

### 2. 🌊 Intra-Regional ASEAN to Asia Trade Sankey
**[View](https://swaraj1313.github.io/Regional-Trade-Integration/visuals/asean_sankey_2024.html)**

A Sankey flow diagram mapping how ASEAN's trade intensity distributes across the broader Asian region.

**Methodology:** Built on Trade Intensity Index to show not just volume but the relative strength of trade corridors — which ASEAN-to-Asia flows are disproportionately strong relative to global baselines.

**Use case:** Identifies which corridors represent genuine structural integration vs. size-driven trade relationships.

---

### 3. 📍 Intra-Regional Shift in Trade Influence — Asia (2000–2024)
**[View](https://swaraj1313.github.io/Regional-Trade-Integration/visuals/asian_trade_shift_interactive.html)**

An interactive dumbbell chart showing every Asian economy's change in structural trade influence between 2000 and 2024.

**How to read it:**
- Each horizontal line = one country
- Grey dot = Eigenvector Centrality score in 2000
- Green dot = score increased by 2024 | Red dot = score decreased
- The length and direction of movement shows the structural trajectory

**Methodology — Eigenvector Centrality:**
This metric measures not just how many countries you trade with, but how *important* your partners are. A country scores highly if it trades with many countries AND those countries are themselves influential. This identifies structural position in the network — not trade volume.

| Position | What it means |
|---|---|
| **High score — "Throughway"** | Components enter, are processed, exit to a third country. Embedded in global value chains. |
| **Low score — "Endpoint"** | Imports finished goods or exports raw materials. Trade is a one-way street. |

**Key finding — Vietnam vs. India/Pakistan:**

| Feature | Vietnam (Central) | India / Pakistan (Peripheral) |
|---|---|---|
| FDI Type | Efficiency-seeking (export-oriented manufacturing) | Market-seeking (domestic consumption driven) |
| Shock Absorption | High — diversified partners enable rapid re-routing | Low — reliance on limited trade corridors |
| Technology Transfer | High — embedded within global value chains | Low — limited spillovers beyond final-stage production |

Vietnam's dramatic rise is structural, not coincidental. It reflects a deliberate insertion into the network through export-oriented FDI policy. India's peripheral positioning despite its economic size reflects the dominance of domestic-consumption-oriented trade policy.

---

### 4. 🏆 Evolution of Trade Hubs — Asia Power Rankings (2000–2024)
**[View](https://swaraj1313.github.io/Regional-Trade-Integration/visuals/asian_trade_ranks.html)**

An interactive bump chart showing how the top 10 Asian trade hubs have changed in structural ranking from 2000 to 2024, measured by Eigenvector Centrality.

**Methodology:**
For each benchmark year, bilateral trade data is represented as a directed graph G. Eigenvector Centrality λ is computed for every node. Rankings are derived from these scores — not from trade volumes.

$$\lambda x_i = \sum_{j} A_{ij} x_j$$

Where $A_{ij}$ is the adjacency matrix and $x_i$ is the centrality score of country $i$.

**Headline finding:**
> **Vietnam surged to #3 by 2024, overtaking Taiwan, Singapore, and South Korea** — a structural confirmation of Vietnam's role as the primary alternative manufacturing hub in the "China Plus One" diversification strategy.

This is not a volume story. Vietnam's rise in the *structural* rankings — based on the quality and diversity of its trade connections — is evidence that it has genuinely embedded itself in the core of the Asian production network, not merely grown bilateral trade with one partner.

---

### 5. 📐 Asian Trade Network Topology — Density, Clustering & Reciprocity (2000–2024)
**[View](https://swaraj1313.github.io/Regional-Trade-Integration/visuals/asian_trade_topology.html)**

Tracks three structural metrics of Asia's trade network across six benchmark years, using binary adjacency networks (trade link exists or not — value is deliberately excluded to isolate structural organisation).

**Metrics:**

| Metric | Definition | Range | Interpretation |
|---|---|---|---|
| **Network Density** | Actual links / All possible links | 0 → 1 | Breadth of integration — how many countries are trading with each other |
| **Clustering Coefficient** | How interconnected a country's partners are with each other | 0 → 1 | Depth/cohesion — captures formation of trade triangles and regional value chain blocs |
| **Reciprocity** | Share of relationships that are genuinely bidirectional | 0 → 1 | Mutual dependence — balanced vs. one-directional trade relationships |

**Results:**

| Year | Network Density | Clustering Coefficient | Reciprocity | Active Nations |
|---|---|---|---|---|
| 2000 | 0.3048 | 0.5996 | 0.5198 | 46 |
| 2005 | 0.3460 | 0.6044 | 0.5401 | 47 |
| 2010 | 0.3659 | 0.5665 | 0.5158 | 47 |
| 2015 | 0.3839 | 0.5850 | 0.5398 | 47 |
| 2020 | 0.3922 | 0.5600 | 0.5519 | 47 |
| 2024 | 0.4126 | 0.5829 | 0.5448 | 47 |

**Policy implications:**
- Peripheral countries need targeted strategies to move from the edges into core trade networks
- High-influence countries got there through multi-partner embeddedness — policy should prioritise supply chain investment attraction, logistics and digital connectivity
- Regional cooperation must focus on bringing smaller economies into the network, not just deepening existing hub relationships

---

### 6. 🌍 Asia vs. Africa Regional Integration Gap & Post-COVID Divergence
**[View](https://swaraj1313.github.io/Regional-Trade-Integration/visuals/africa_vs_asia_density.html)**

A comparative structural analysis of intra-regional trade integration between Asia Pacific and Africa from 2000 to 2024, using network density as the primary metric.

**Methodology:**
- Directed trade networks constructed for each region using only **intra-regional** trade flows (exporter and importer both within the same region)
- Network density formula: $D = E / [N(N-1)]$ where E = observed trade links, N = active countries
- Directed, unweighted graphs — presence of trade relationship, not value

**Results:**

| Year | Africa Density | Asia Pacific Density | Africa Active Nations | Asia Pacific Active Nations |
|---|---|---|---|---|
| 2000 | 0.1742 | 0.3048 | 52 | 46 |
| 2005 | 0.2044 | 0.3460 | 52 | 47 |
| 2010 | 0.2662 | 0.3659 | 52 | 47 |
| 2015 | 0.2787 | 0.3839 | 53 | 47 |
| 2020 | 0.2841 | 0.3922 | 53 | 47 |
| 2024 | 0.2892 | 0.4126 | 53 | 47 |

**Key findings:**

Africa's integration has been growing — but the gap with Asia is **widening, not closing**. A visible **post-COVID divergence** shows Asia's integration accelerating while Africa's momentum stalled.

Critically: active nation counts remain stable in both regions throughout the period. This means the density changes are driven entirely by **intensification of connections among existing participants** — not new countries entering trade. Africa has the countries. It lacks the density of linkages between them.

The structural contrast:
- **Asia Pacific** — a dense, highly redundant production network where countries trade with multiple regional partners simultaneously; characteristic of integrated global value chains
- **Africa** — a comparatively sparse network where trade relationships are fewer and more fragmented; limited intra-regional supply chain integration despite the AfCFTA framework

> The implication is that integration gaps are not merely about trade volume — they are about the **density and redundancy of economic linkages**.

---

## Analytical Framework

### Why Network Analysis for Trade?

Standard trade analysis answers: *How much does country A trade with country B?*

Network analysis answers: *What structural position does country A occupy in the global trading system, and how has that changed?*

These are fundamentally different questions with fundamentally different policy implications. A country can have large bilateral trade volumes and still be structurally peripheral — dependent on a single corridor, vulnerable to shocks, excluded from value chain triangles.

### Core Metrics Used

| Metric | Formula | What it captures |
|---|---|---|
| Trade Intensity Index | $TII_{ij} = \frac{x_{ij}/X_i}{m_j/M_w}$ | Whether bilateral trade is disproportionately strong relative to both countries' global shares |
| Eigenvector Centrality | $\lambda x_i = \sum_j A_{ij} x_j$ | Structural influence — accounts for the quality, not just quantity, of trade connections |
| Network Density | $D = E / [N(N-1)]$ | Breadth of integration across the full regional network |
| Clustering Coefficient | Local triangle density | Depth of integration — value chain formation and trade bloc cohesion |
| Reciprocity | Bidirectional link share | Balance of trade relationships — mutual vs. one-directional dependence |
| Louvain Community Detection | Modularity maximisation | Identifies algorithmically emergent trade blocs without pre-defining them |

---

## Tech Stack

| Component | Technology |
|---|---|
| Network Construction & Analysis | Python · NetworkX |
| Community Detection | python-louvain (Louvain algorithm) |
| Network Layout | ForceAtlas2 |
| Interactive Visualisations | Plotly · Pyvis |
| Sankey Diagrams | Plotly |
| Data Processing | Pandas · NumPy |
| Data Source | IMF Direction of Trade Statistics (DOTS) |
| Hosting | GitHub Pages |

---

## Repository Structure

```
Regional-Trade-Integration/
│
├── index.html                          # Main dashboard landing page
│
├── visuals/                            # All interactive HTML visualisations
│   ├── Asian_Trade_2024.html           # Force-directed network graph
│   ├── asean_sankey_2024.html          # ASEAN trade flow Sankey
│   ├── asian_trade_shift_interactive.html  # Dumbbell chart — centrality shift
│   ├── asian_trade_ranks.html          # Bump chart — hub power rankings
│   ├── asian_trade_topology.html       # Density/clustering/reciprocity
│   └── africa_vs_asia_density.html     # Asia vs Africa comparison
│
├── notebooks/                          # Analysis notebooks (if applicable)
│   ├── network_construction.ipynb
│   ├── eigenvector_centrality.ipynb
│   ├── topology_analysis.ipynb
│   └── africa_asia_comparison.ipynb
│
├── data/                               # Processed data files
│   └── imf_dots_processed.csv
│
└── README.md
```

---

## Key Findings Summary

1. **Vietnam is Asia's structural breakout story** — rising to #3 in Eigenvector Centrality rankings by 2024, overtaking Taiwan, Singapore, and South Korea. This confirms its role as the primary "China Plus One" manufacturing hub — embedded in the network, not just bilaterally connected.

2. **India and Pakistan remain structurally peripheral** despite their economic size — a consequence of market-seeking rather than efficiency-seeking FDI orientation. They are endpoints, not throughways.

3. **Asia's trade network is densifying steadily** — from 0.30 density in 2000 to 0.41 in 2024, driven by intensification among existing participants, not new entrants.

4. **Three distinct trade communities have emerged in Asia** — a North-East Asian core, an ASEAN manufacturing zone, and a Central Asian periphery. Singapore and Malaysia serve as structural bridges between the first two.

5. **Africa's integration gap with Asia is widening post-COVID** — Africa grew from 0.17 to 0.29 density over 24 years, but lost momentum after 2020 while Asia accelerated. The constraint is not the number of countries but the sparseness of connections between them.

---

## Context

This is an ongoing research project exploring structural patterns in global and regional trade using network analysis. The analytical approach was developed independently, applying methods from network science to publicly available trade statistics to generate insights beyond what standard bilateral flow analysis can surface.

Part of a broader trade analytics portfolio developed during research work in international trade and export promotion.

---

## Related Projects

🔗 [**Services Trade Data Explorer**](https://trade-in-services-data-explorer-tool.streamlit.app/) — Bilateral services trade flows across 202 economies (OECD-WTO BaTIS)

🔗 [**Services Trade Dependency Analysis**](https://services-trade-partner-dependency-analysis.streamlit.app/) — Revealed Comparative Advantage & partner dependency ratios

---

## Data Attribution

All analysis uses the **IMF Direction of Trade Statistics (DOTS)** dataset. Please refer to IMF's terms of use for data attribution requirements.

---

## License

MIT License — code and visualisations are open for reuse with attribution.
