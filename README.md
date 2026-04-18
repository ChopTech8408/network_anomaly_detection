# Network Anomaly Detection Using Machine Learning

An unsupervised machine learning model that detects anomalies 
and potential DDoS attacks in real network traffic data using 
the CICIDS 2017 dataset.

## Overview

Traditional intrusion detection systems require prior knowledge 
of attack signatures. This project uses unsupervised learning to 
detect anomalies purely from network behaviour — without needing 
labeled attack examples.

## Dataset

- **Source:** CIC-IDS-2017 — Canadian Institute for Cybersecurity
- **File:** Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv
- **Records:** 226,000 network flow records
- **Traffic types:** BENIGN (normal) and DDoS (attack)

## Methodology

### Pipeline
Raw CSV → Select Columns → Preprocess → Impute →
Data Sampler → k-Means Clustering → Outlier Detection

### Algorithms
- **k-Means Clustering** — groups similar traffic into 3 clusters
- **One-Class SVM** — flags traffic that doesn't fit normal patterns

### Features Used
- Flow Duration
- Total Forward Packets
- Total Backward Packets
- Fwd Packet Length Max
- Bwd Packet Length Max

## Results

| Metric | Value |
|--------|-------|
| Records processed | 11,300 (5% sample) |
| Clusters identified | 3 |
| Anomaly detection rate | ~10% flagged |
| DDoS separation | Visually confirmed via scatter plot |

The model successfully separated DDoS attack traffic from normal 
traffic without being told what DDoS looks like.

## Scatter Plot

![Anomaly Detection Scatter Plot](screenshots/scatter_plot.png)

## Tools Used

- Orange Data Mining 3.x
- CICIDS 2017 Dataset
- Python (scikit-learn — next phase)

## Limitations

- Tested on single day traffic capture only
- 5% sample used for computational efficiency
- Two features excluded due to infinite values in source data
- Built in Orange — Python conversion planned

## Full Report

See `report/Network_Anomaly_Detection_Report.docx` for complete 
methodology, findings, and analysis.

## Author
Esihlisipho Nikelo  
ESK Solutions (PTY) LTD — Durban, KZN  
esknikelo@gmail.com  
[Portfolio](https://esihlisipho-nikelo.netlify.app/) | [LinkedIn](https://linkedin.com/in/esihlisipho-nikelo)
