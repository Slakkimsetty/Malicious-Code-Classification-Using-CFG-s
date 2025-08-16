# 🔐 Malicious Code Classification using Control Flow Graphs (CFG)

Classifying **Ransomware vs Benign executables** by analyzing **Control Flow Graphs (CFGs)** and training machine-learning models on a blend of **node-level (Attributed CFG)** and **graph-level network metrics**.

---

## 🌟 Motivation
Signature-based antivirus struggles against new, obfuscated ransomware. Our goal is to detect ransomware from its **execution structure** rather than its bytes: build CFGs from binaries, extract semantic + network features, and learn a classifier that generalizes to unseen samples.

---

## 🎯 Key Contributions
- Built **Attributed Control Flow Graphs (ACFGs)** from PE files and extracted:
  - **Node features:** counts of calls, arithmetic, logic, move, compare, modulo ops; instruction totals.
  - **Graph metrics:** nodes/edges, degree stats, diameter, density, PageRank, HITS, closeness/harmonic/eigenvector/betweenness centralities, clustering, assortativity, average path length, modularity.
- Compared multiple models:
  - **Random Forest** (best observed accuracy ≈ **98.5%**; average ≈ **87%**)
  - **SVM (RBF)** (best ≈ **92.85%**; average ≈ **91.92%**)
  - **MLP (Neural Network)** with tuning considerations (risk of overfitting)
- Identified **most influential features** for detection:
  **Average Degree**, **Average Eigenvector Centrality**, **Average Betweenness**, **Average Clustering**.

---

## 📊 Results (Summary)
- **Random Forest (10-fold CV):** *Best* ~**98.5%**, *Avg* ~**87%**
- **SVM (RBF, tuned C/γ):** *Best* ~**92.85%**, *Avg* ~**91.92%**
- Feature importance analysis consistently ranks **connectivity and centrality** metrics at the top.
- Visual analyses (PCA & scatter plots) show separability between benign and ransomware samples along these features.

> Full tables, plots, and narrative are available in the project reports.

---

## 🧰 Tech & Tools
- **Python**, **Jupyter Notebook**
- **NetworkX** (graph metrics), **scikit-learn** (ML), **Matplotlib/Seaborn** (viz)
- **IDA Pro / Ghidra** (CFG generation from binaries)
- (Optional) **Pandas / NumPy** for data prep

---

## ⚡ Quickstart

### 1) Install dependencies
```bash
pip install -r requirements.txt
