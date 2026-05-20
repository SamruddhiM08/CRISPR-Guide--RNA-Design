🧬 CRISPR Guide RNA Design for EGFP Gene

Computational design and analysis of CRISPR-Cas9 guide RNAs targeting the Enhanced Green Fluorescent Protein (EGFP) gene using bioinformatics tools.


📌 Project Overview

This project demonstrates a complete computational pipeline for designing CRISPR-Cas9 guide RNAs against the EGFP gene. Starting from raw sequence retrieval through PAM identification, guide prediction, and off-target validation, each step is documented with tool outputs and selection criteria.
Key highlights:

3 high-efficiency guide RNAs identified
Full off-target analysis using CHOPCHOP
PAM site visualization in SnapGene Viewer
Multi-parameter filtering (efficiency score, GC content, MM values)


🎯 Objective

To identify efficient and specific CRISPR-Cas9 guide RNAs targeting the EGFP gene using computational bioinformatics tools, prioritizing high on-target activity and minimal off-target effects.

🛠️ Tools Used
- NCBI
- SnapGene Viewer
- CHOPCHOP
- Microsoft Excel 

🔬 Methodology

Step 1 — Sequence Retrieval
The EGFP nucleotide sequence was retrieved from the NCBI Nucleotide database in FASTA format.
Figure 1 — NCBI FASTA sequence retrieval:


Step 2 — FASTA Sequence Preparation
The retrieved sequence was saved in FASTA format and imported into SnapGene Viewer for structural visualization and sequence inspection prior to PAM site mapping.
Figure 2 — SnapGene Mapping

Step 3 — PAM Site Identification
Potential Cas9 PAM regions (5′-NGG-3′ motifs) were systematically identified across both strands of the EGFP sequence using SnapGene Viewer. Each NGG site defines a potential Cas9 cleavage window.
Figure 3 — PAM site analysis in SnapGene Viewer:


Step 4 — Guide RNA Design via CHOPCHOP
The full EGFP sequence was submitted to CHOPCHOP for automated guide RNA prediction with the following parameters:
Parameter Value CRISPR System Cas9 PAM Sequence NGGTarget TypeKnockoutScoring MethodDoench 2016
Figure 4 — CHOPCHOP guide RNA predictions:

Step 5 — Guide RNA Filtering & Selection
All predicted guides were filtered using the following criteria:
Criterion Threshold Efficiency Score ≥ 0.75 (Doench) 
MM0 (exact off-target matches) 
MM1 (1-mismatch off-targets)
MM2/MM3 Minimized 
GC Content 40–60%
The filtered selection table is available here: tables/guide_selection_table.xlsx

Step 6 — Guide Visualization
The selected guide RNA spacer sequences and corresponding PAM regions were mapped back and visualized in SnapGene Viewer to confirm correct genomic positioning within the EGFP coding sequence.
Figure 5 — Selected guide RNA and PAM region visualization:


Step 7 — Off-Target Validation
Each selected guide was re-analyzed in CHOPCHOP for a detailed off-target landscape assessment. Specificity scores and genome-wide off-target predictions were reviewed to confirm suitability for experimental use.
Figure 5 — Off-target validation in CHOPCHOP:


📊 Results

Three high-quality guide RNAs were identified for CRISPR-Cas9 targeting of the EGFP gene:
Guide RNATarget Sequence (5′→3′)Efficiency ScoreGC ContentMM0MM1gRNA-1GCAGCACGACTTCTTCAAGT + NGG0.8255%01gRNA-2GAAGTTCACCTTGATGCCGT + NGG0.7854%00gRNA-3CTTGTACAGCTCGTCCATGC + NGG0.7552%02
Key findings:

All three guides exceeded the 0.75 efficiency threshold
GC content falls within the optimal 40–70% range for all candidates
No exact off-target sites (MM0 = 0) detected for any selected guide
gRNA-2 shows the best specificity profile (MM1 = 0)


✅ Conclusion

This project successfully demonstrated a reproducible computational pipeline for CRISPR guide RNA design targeting the EGFP gene. The three selected guide RNAs exhibit strong predicted on-target efficiency, favorable GC content, and minimal off-target risk — making them strong candidates for experimental validation in cell-based CRISPR-Cas9 editing assays.
