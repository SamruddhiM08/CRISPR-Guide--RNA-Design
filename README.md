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

> **Tool:** NCBI · **Output:** `.fasta` file · **Database:** Nucleotide

```
>EGFP [Enhanced Green Fluorescent Protein]
ATGGTGAGCAAGGGCGAGGAGCTGTTCACCGGGGTGGTGCCCATCCTGGTCGAGCTGGACGGCGACGTA
AACGGCCACAAGTTCAGCGTGTCCGGCGAGGGCGAGGGCGATGCCACCTACGGCAAGCTGACCCTGAAGT
...
```

---

### Step 2 — Sequence Preparation

The FASTA file was imported into **SnapGene Viewer** for structural visualization and inspection prior to PAM site mapping.

> **Tool:** SnapGene Viewer · **Input:** `.fasta` · **Output:** Annotated sequence map

---

### Step 3 — PAM Site Identification

All `5′-NGG-3′` motifs were systematically identified across **both strands** of the EGFP sequence. Each NGG site defines a potential Cas9 cleavage window.

> **Tool:** SnapGene Viewer · **Motif:** `5′-NGG-3′` · **Strands:** Both (+/−)

```
Strand (+):  ...GCAGCACGACTTCTTCAAGT[NGG]...
Strand (−):  ...CTTGTACAGCTCGTCCATGC[NGG]...
```

---

### Step 4 — Guide RNA Prediction via CHOPCHOP

The full EGFP sequence was submitted to **CHOPCHOP** with the following parameters:

| Parameter | Value |
|-----------|-------|
| CRISPR System | Cas9 |
| PAM Sequence | `NGG` |
| Target Type | Knockout |
| Scoring Method | Doench 2016 |

> **Tool:** CHOPCHOP · **Output:** Ranked guide RNA list with efficiency scores and off-target counts

---

### Step 5 — Multi-Parameter Filtering

All predicted guides were filtered in Excel using:

| Criterion | Threshold | Rationale |
|-----------|-----------|-----------|
| Efficiency Score | ≥ 0.75 (Doench 2016) | High on-target activity |
| MM0 (exact off-targets) | = 0 | No perfect off-target matches |
| MM1 (1-mismatch) | Minimized | Reduce near-perfect off-targets |
| MM2 / MM3 | Minimized | Additional specificity buffer |
| GC Content | 40–60% | Optimal guide stability |

> 📁 Full table: [`tables/guide_selection_table.xlsx`](tables/guide_selection_table.xlsx)

---

### Step 6 — Guide Visualization

Selected guide spacer sequences and PAM regions were mapped back in **SnapGene Viewer** to confirm correct positioning within the EGFP coding sequence.

> **Tool:** SnapGene Viewer · **Verified:** Spacer + PAM location on both strands

---

### Step 7 — Off-Target Validation

Each candidate was re-analyzed in **CHOPCHOP** for genome-wide off-target assessment. Specificity scores confirmed suitability for experimental use.

> **Tool:** CHOPCHOP · **Genome:** Human (hg38) · **Assessment:** MM0–MM3 landscape

---

## 📊 Results

<div align="center">

| Guide | Target Sequence (5′→3′) | PAM | Doench Score | GC% | MM0 | MM1 |
|:-----:|:------------------------|:---:|:------------:|:---:|:---:|:---:|
| `gRNA-1` | `GCAGCACGACTTCTTCAAGT` | `NGG` | 0.82 | 55% | 0 | 1 |
| `gRNA-2` ⭐ | `GAAGTTCACCTTGATGCCGT` | `NGG` | 0.78 | 54% | 0 | **0** |
| `gRNA-3` | `CTTGTACAGCTCGTCCATGC` | `NGG` | 0.75 | 52% | 0 | 2 |

</div>

> ⭐ **gRNA-2** is the top candidate — the only guide with MM0 = 0 **and** MM1 = 0, giving the cleanest off-target profile of the three.

**Key findings:**
- ✅ All three guides exceeded the **0.75 efficiency threshold**
- ✅ GC content within the **optimal 40–60% range** for all candidates
- ✅ **Zero exact off-target sites** (MM0 = 0) across all selected guides
- 🏆 **gRNA-2** shows the best specificity profile (MM0 = 0, MM1 = 0)

---

## ✅ Conclusion

This project demonstrated a reproducible computational pipeline for CRISPR guide RNA design targeting the EGFP gene. The three selected guide RNAs exhibit strong predicted on-target efficiency, favorable GC content, and minimal off-target risk — making them strong candidates for experimental validation in cell-based CRISPR-Cas9 editing assays.

---

<div align="center">

<img src="https://img.shields.io/badge/Status-Complete-1D9E75?style=flat-square&labelColor=0a0e1a" />
&nbsp;
<img src="https://img.shields.io/badge/Scoring-Doench%202016-5DCAA5?style=flat-square&labelColor=0a0e1a" />
&nbsp;
<img src="https://img.shields.io/badge/PAM-5′--NGG--3′-378ADD?style=flat-square&labelColor=0a0e1a" />
&nbsp;
<img src="https://img.shields.io/badge/Candidates-3%20guides-BA7517?style=flat-square&labelColor=0a0e1a" />

<br/><br/>
<sub>Pipeline: NCBI → SnapGene Viewer → CHOPCHOP → Excel</sub>

</div>
