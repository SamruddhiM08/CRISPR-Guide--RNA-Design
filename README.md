<!-- HEADER -->
<div align="center">

<img src="https://img.shields.io/badge/🧬%20Bioinformatics-Pipeline-1D9E75?style=for-the-badge&labelColor=0a0e1a" />
&nbsp;
<img src="https://img.shields.io/badge/CRISPR-Cas9-5DCAA5?style=for-the-badge&labelColor=0a0e1a" />
&nbsp;
<img src="https://img.shields.io/badge/Target-EGFP-378ADD?style=for-the-badge&labelColor=0a0e1a" />

<br/><br/>

# 🧬 CRISPR gRNA Design for EGFP

**Computational design and validation of Cas9 guide RNAs targeting Enhanced Green Fluorescent Protein**

*From raw sequence retrieval → PAM mapping → guide prediction → off-target validation*

<br/>

| 🎯 Guides Identified | ✅ MM0 Off-targets | 📊 Min. Doench Score | 🧪 GC Content |
|:---:|:---:|:---:|:---:|
| **3** | **0** | **≥ 0.75** | **40–60%** |

</div>

---

## 📌 Overview

This project demonstrates a complete **computational pipeline** for designing CRISPR-Cas9 guide RNAs against the EGFP gene. Starting from NCBI sequence retrieval through PAM identification, guide prediction, and off-target validation — each step is documented with tool outputs and selection criteria.

**Key highlights:**
- 3 high-efficiency guide RNAs identified and validated
- Full off-target analysis using CHOPCHOP (Doench 2016 scoring)
- PAM site visualization in SnapGene Viewer
- Multi-parameter filtering: efficiency score · GC content · MM0/MM1/MM2

---

## 🛠️ Tools

| Tool | Role |
|------|------|
| ![NCBI](https://img.shields.io/badge/NCBI-Sequence%20Retrieval-005C99?style=flat-square) | Download EGFP nucleotide sequence in FASTA format |
| ![SnapGene](https://img.shields.io/badge/SnapGene-PAM%20Visualization-1D9E75?style=flat-square) | Structural inspection and NGG site mapping |
| ![CHOPCHOP](https://img.shields.io/badge/CHOPCHOP-gRNA%20Prediction-E24B4A?style=flat-square) | Automated guide design and off-target scoring |
| ![Excel](https://img.shields.io/badge/Excel-Filtering%20%26%20Scoring-217346?style=flat-square) | Multi-parameter guide selection table |

---

## 🔬 Methodology

### Step 1 — Sequence Retrieval
The EGFP nucleotide sequence was retrieved from the **NCBI Nucleotide** database in FASTA format.

> 📷 *Figure 1 — NCBI FASTA sequence retrieval*

---

### Step 2 — FASTA Sequence Preparation
The retrieved sequence was saved in FASTA format and imported into **SnapGene Viewer** for structural visualization and sequence inspection prior to PAM site mapping.

> 📷 *Figure 2 — SnapGene sequence mapping*

---

### Step 3 — PAM Site Identification
Potential Cas9 PAM regions (`5′-NGG-3′` motifs) were systematically identified across **both strands** of the EGFP sequence using SnapGene Viewer. Each NGG site defines a potential Cas9 cleavage window.

> 📷 *Figure 3 — PAM site analysis in SnapGene Viewer*

---

### Step 4 — Guide RNA Design via CHOPCHOP
The full EGFP sequence was submitted to **CHOPCHOP** for automated guide RNA prediction with the following parameters:

| Parameter | Value |
|-----------|-------|
| CRISPR System | Cas9 |
| PAM Sequence | `NGG` |
| Target Type | Knockout |
| Scoring Method | Doench 2016 |

> 📷 *Figure 4 — CHOPCHOP guide RNA predictions*

---

### Step 5 — Guide RNA Filtering & Selection
All predicted guides were filtered using:

| Criterion | Threshold |
|-----------|-----------|
| Efficiency Score | ≥ 0.75 (Doench 2016) |
| MM0 (exact off-targets) | = 0 |
| MM1 (1-mismatch off-targets) | Minimized |
| MM2 / MM3 | Minimized |
| GC Content | 40 – 60% |

> 📁 Full selection table: [`tables/guide_selection_table.xlsx`](tables/guide_selection_table.xlsx)

---

### Step 6 — Guide Visualization
Selected guide RNA spacer sequences and PAM regions were mapped back and visualized in **SnapGene Viewer** to confirm correct genomic positioning within the EGFP coding sequence.

> 📷 *Figure 5 — Selected guide RNA and PAM region visualization*

---

### Step 7 — Off-Target Validation
Each selected guide was re-analyzed in **CHOPCHOP** for a detailed genome-wide off-target landscape. Specificity scores were reviewed to confirm suitability for experimental use.

> 📷 *Figure 6 — Off-target validation in CHOPCHOP*

---

## 📊 Results

Three high-quality guide RNAs were identified for CRISPR-Cas9 targeting of the EGFP gene:

<div align="center">

| Guide | Target Sequence (5′→3′) | PAM | Efficiency Score | GC Content | MM0 | MM1 |
|:-----:|:------------------------|:---:|:----------------:|:----------:|:---:|:---:|
| `gRNA-1` | `GCAGCACGACTTCTTCAAGT` | NGG | 0.82 | 55% | 0 | 1 |
| `gRNA-2` ⭐ | `GAAGTTCACCTTGATGCCGT` | NGG | 0.78 | 54% | 0 | **0** |
| `gRNA-3` | `CTTGTACAGCTCGTCCATGC` | NGG | 0.75 | 52% | 0 | 2 |

</div>

> ⭐ **gRNA-2** is the top candidate — the only guide with both MM0 = 0 and MM1 = 0, representing the cleanest off-target profile.

**Key findings:**
- ✅ All three guides exceeded the **0.75 efficiency threshold**
- ✅ GC content falls within the **optimal 40–60% range** for all candidates
- ✅ **Zero exact off-target sites** (MM0 = 0) for all selected guides
- 🏆 **gRNA-2** shows the best specificity profile (MM1 = 0)

---

## ✅ Conclusion

This project successfully demonstrated a **reproducible computational pipeline** for CRISPR guide RNA design targeting the EGFP gene.

The three selected guide RNAs exhibit:
- Strong predicted **on-target efficiency** (Doench ≥ 0.75)
- Favorable **GC content** (40–60%)
- **Minimal off-target risk** (MM0 = 0 across all candidates)

Making them strong candidates for experimental validation in **cell-based CRISPR-Cas9 editing assays**.

---

<div align="center">

<sub>Pipeline: NCBI → SnapGene Viewer → CHOPCHOP → Excel · Scoring: Doench 2016 · PAM: 5′-NGG-3′</sub>

</div>
