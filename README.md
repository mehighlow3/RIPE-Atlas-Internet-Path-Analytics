# RIPE Atlas Internet Path Analytics: Global Traceroute Enrichment

This repository features a comprehensive Python-based data pipeline designed to analyze and visualize internet routing paths. Using **RIPE Atlas** traceroute data targeting Anchor 6360 in Salzburg, Austria (AS39878), this project explores the complexities of global internet topology, autonomous system (AS) transitions, and geolocation bottlenecks.

Developed as a collaborative seminar project at the **University of Vienna**, this toolset transforms raw, multi-gigabyte JSONL traceroute dumps into enriched, actionable network insights.

## Key Features

* **Streaming Data Pipeline:** Efficiently processes large-scale `.jsonl` and `.bz2` datasets without high memory overhead.
* **Enrichment Engine:** Automatically enriches traceroute hops with:
    * **Reverse DNS (PTR):** Resolving hostnames for infrastructure identification.
    * **ASN Mapping:** Identifying Autonomous Systems via RIPEstat and CAIDA datasets.
    * **Geolocation:** Mapping unique IP addresses to cities and countries using MaxMind and IPinfo APIs.
* **Smart Caching:** Implements a local caching mechanism to minimize redundant external API lookups, ensuring speed and cost-effectiveness.
* **Advanced Visualizations:** Includes automated heatmaps of country-to-country transitions and graph-based representations of transit provider dependencies.

## Technical Results & Insights

The analysis of **88,302,907 traceroute measurements** revealed a high dependency on major transit providers (AS1299 - Telia, AS6939 - Hurricane Electric) for traffic destined for Austria.

### Core Statistics
* **Unique IPs Observed:** 1,004
* **Resolved PTR Records:** 600
* **Top Transit ASN:** AS1299 (92 unique paths)
* **Global Reach:** Traceroutes originated from over 40+ countries, with significant transit clusters in DE, US, and NL.



## Repository Structure

* `parser.ipynb`: Filters and simplifies raw RIPE Atlas measurements into a manageable format.
* `enrichment.ipynb`: The core logic for streaming IP enrichment and geolocation caching.
* `geomap.ipynb`: Generates interactive HTML world maps of unique IP distributions.
* `visualisation1.ipynb`: Creates graph networks of frequent transit Autonomous Systems.
* `fns.pdf`: The complete technical seminar report detailing the research methodology and results.

## Build and Execution

### Prerequisites
* Python 3.10+
* Pandas, Plotly, GeoPandas, NetworkX, Matplotlib

### Installation
```bash
pip install pandas plotly geopandas networkx matplotlib requests
```
Usage
Run parser.ipynb to process the raw .bz2 or .jsonl RIPE Atlas data.

Execute enrichment.ipynb to perform the IP-to-ASN and Geolocation lookups.

Use the visualisation notebooks to generate performance heatmaps and topological graphs.

Collaborators: Mihajlo Katić, Jovana Gojković, Julian Waluschyk
University of Vienna - Computer Science
