# 🐦 Social Network Analysis of Xoxoday's Twitter Interactions

> **BANL6900 Business Analytics Capstone · University of New Haven · December 2025**

[![R](https://img.shields.io/badge/R-4.3%2B-276DC3?style=flat-square&logo=r)](https://www.r-project.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=flat-square&logo=powerbi)](https://powerbi.microsoft.com/)
[![igraph](https://img.shields.io/badge/igraph-SNA-orange?style=flat-square)](https://igraph.org/r/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

---

## 📌 Project Overview

This project performs a **Social Network Analysis (SNA)** on Xoxoday's Twitter ecosystem — examining how brand-related mentions, replies, and retweets flow between users. The goal was to surface structural engagement patterns, identify influential nodes, detect organic communities, and uncover whether Xoxoday's social presence is **genuinely community-driven or campaign-dependent**.

**Key questions answered:**
- Who are the most influential accounts in the Xoxoday Twitter network?
- Is engagement organic or artificially inflated by contest accounts?
- How does information diffuse through retweets?
- What structural weaknesses exist in the network?

---

## 🗂️ Repository Structure

```
xoxoday-twitter-sna/
│
├── 📁 data/
│   ├── nodes_for_powerbi.csv          # Node-level metrics (degree, betweenness, community)
│   ├── edges_for_powerbi.csv          # Edge list with weights
│   └── network_metrics.csv            # Full centrality metrics per node
│
├── 📁 notebooks/
│   └── SNA_Analysis.Rmd               # Full R Markdown analysis notebook
│
├── 📁 visuals/
│   ├── mentions_replies_network.png   # Figure 1 – Mentions & Replies graph
│   ├── retweet_network.png            # Figure 2 – Retweet network graph
│   ├── indegree_rankings.png          # Figure 3 – Top indegree nodes table
│   ├── outdegree_patterns.png         # Figure 4 – Outdegree bar chart
│   ├── top_indegree_comparison.png    # Figure 5 – thexoxoday vs pratima_talreja
│   ├── tweet_frequency_over_time.png  # Figure 6 – Temporal activity chart
│   └── retweet_weight_distribution.png # Figure 7 – Retweet weight distribution
│
├── 📁 powerbi/
│   └── Xoxoday_SNA_Dashboard.pbix     # Interactive Power BI report
│
├── 📁 report/
│   └── Final_Report.pdf               # Full academic report (9 sections)
│
├── 📁 presentation/
│   └── Final_Presentation.pptx        # Capstone slide deck
│
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🔍 Methodology

| Step | Technique | Tool |
|------|-----------|------|
| Data Cleaning | Column normalization, NA handling, deduplication | R (`dplyr`, `janitor`, `tidyr`) |
| Graph Construction | Directed graphs from edge lists | `igraph`, `tidygraph` |
| Centrality Analysis | Indegree, Outdegree, Betweenness, PageRank | `igraph` |
| Community Detection | Louvain Modularity Algorithm | `igraph` |
| Visualization | Force-directed network graphs | `ggraph`, `ggplot2` |
| Temporal Analysis | Tweet frequency time series | `ggplot2` |
| Interactive Dashboard | Slicers, drill-through pages, KPI cards | Power BI |

---

## 📊 Key Findings

### 1. Highly Centralized Hub-and-Spoke Network
The **Mentions & Replies network** reveals a star topology: `thexoxoday` sits at the center with an indegree of **47** — more than 10× the next most-mentioned account (`pratima_talreja` at 4). Most users connect only to the brand, not to each other, indicating **low peer-to-peer interaction**.

### 2. Artificial Engagement Inflation
The account `contestadventur` generated **4,000+ outgoing mentions** — an anomaly consistent with automated contest-tagging behavior. This inflates apparent network activity without contributing to genuine community engagement.

### 3. Fragmented Retweet Diffusion
The **Retweet network** consists of isolated star-shaped subgraphs rather than an interconnected diffusion web. One outlier tweet received nearly **300 retweets** while most received near zero — a classic **power-law distribution** indicating viral content is rare and unpredictable.

### 4. Campaign-Driven Temporal Spikes
Tweet frequency spiked sharply around **January 26–27** and dropped off immediately after, matching a campaign launch pattern rather than sustained organic community activity.

### 5. Minimal Secondary Influencers
No strong secondary advocates or micro-influencers were identified. The network lacks distributed influence nodes that could help conversations spread horizontally.

---

## 🛠️ How to Run the Analysis

### Prerequisites
```r
install.packages(c("readxl", "dplyr", "janitor", "igraph",
                   "ggraph", "tidygraph", "ggplot2", "tidyr"))
```

### Steps
1. Clone this repository
   ```bash
   git clone https://github.com/YOUR_USERNAME/xoxoday-twitter-sna.git
   cd xoxoday-twitter-sna
   ```
2. Open `notebooks/SNA_Analysis.Rmd` in RStudio
3. Update the `file_path` variable to point to your local copy of the raw Excel data
4. Click **Knit** to reproduce the full analysis

> ⚠️ The raw Excel dataset is not included in this repo due to data licensing. The cleaned CSVs in `/data` are provided for Power BI and reproducibility purposes.

---

## 📈 Power BI Dashboard

The interactive dashboard (`powerbi/Xoxoday_SNA_Dashboard.pbix`) includes:

- **Network Metrics Table** — sortable by indegree, outdegree, betweenness
- **Outdegree Bar Chart** — identify anomalous high-activity accounts
- **Indegree Comparison** — top nodes ranked by incoming attention
- **Tweet Frequency Timeline** — campaign spike detection
- **Retweet Weight Distribution** — viral content identification
- **Community Slicers** — filter by Louvain community assignment

---

## 💡 Strategic Recommendations

Based on the analysis, the following actions are recommended for Xoxoday's social media team:

1. **Diversify Influencer Partnerships** — Recruit 5–10 micro-influencers to distribute conversational power beyond the brand account
2. **Filter Contest Bot Activity** — Implement anomaly detection to exclude automated contest accounts from engagement metrics
3. **Encourage Peer Conversations** — Design campaigns that reward user-to-user interaction, not just brand tagging
4. **Sustain Engagement Post-Campaign** — Develop a content calendar to maintain baseline activity between campaign spikes
5. **Replicate Viral Content Features** — Study the attributes of the top retweeted post (~300 RTs) to inform future content strategy

---

## 👥 Authors

| Name | 
|------|
| Preethi Vudugula |

**Course:** BANL6900 Business Analytics Capstone  
**Institution:** University of New Haven  
**Date:** December 5, 2025

---

## 📚 References

- Borgatti, S. P., et al. (2009). Network analysis in the social sciences. *Science*, 323(5916), 892–895.
- Berger, J., & Milkman, K. L. (2012). What makes online content viral? *Journal of Marketing Research*, 49(2), 192–205.
- Kwak, H., et al. (2010). What is Twitter, a social network or a news media? *WWW '10 Proceedings*, 591–600.
- Liu, Y., & Dai, R. (2020). Understanding promotional tagging behaviors in social media contests. *Social Media + Society*, 6(4).
- Wasserman, S., & Faust, K. (1994). *Social Network Analysis: Methods and Applications*. Cambridge University Press.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
