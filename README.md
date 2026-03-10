# Engineering and In Silico Cloning of Human Thrombopoietin (TPO) for Expression in Pichia pastoris

## 📌 Project Overview
This project outlines the comprehensive *in silico* pipeline for the design, optimization, and cloning of the human Thrombopoietin (TPO) protein for heterologous expression in the methylotrophic yeast *Komagataella pastoris* (formerly *Pichia pastoris*). The workflow encompasses three main phases: Human Protein Design & Modeling, Gene Construction & Codon Optimization, and *In Silico* Restriction-Based Cloning.

---

## 🔬 Phase 1: Human Protein Design & Structural Validation

To prepare the human TPO for yeast expression and subsequent purification, the wild-type amino acid sequence was engineered as follows:

* **Signal Peptide Cleavage:** The native human signal peptide was identified and removed using **SignalP v6.0**. 
    * *Probability:* 99.98%
    * *Cleavage Site:* Between amino acids 18 and 19.
    * *Outcome:* Residues 1–18 were cleaved to obtain the mature pro-protein. This ensures compatibility with the yeast's native secretion machinery (e.g., the $\alpha$-factor secretion signal present in the expression vector).

![image](https://github.com/abdulaziz-khaled/From-Protein-Design-to-In-Silico-Cloning/blob/main/IMG_4347.jpeg)


* **Tag Addition:** A 6xHis-tag was fused to the C-terminus of the mature sequence to facilitate downstream affinity chromatography purification and immunodetection.
* **Ab Initio Modeling & Validation:** * The 3D structure of the engineered protein was predicted using **AlphaFold**.
    * Energy minimization was performed using **MOE (Molecular Operating Environment)** to resolve steric clashes.
    * Structural integrity was validated via the **SAVES server**. The Ramachandran plot confirmed excellent stereochemical quality (favorable dihedral angles), and analysis verified that the C-terminal His-tag does not interfere with the native protein folding.


---

## 🧬 Phase 2: Gene Construction & Codon Optimization

The validated amino acid sequence was reverse-translated into a 2766 bp DNA sequence. To maximize translational efficiency in *K. pastoris*, the sequence was optimized using the **GenSmart™ Codon Optimization Tool (Beta 1.0)**.

### Technical Report: NC Gene Optimization
*Analysis Date: March 9, 2026*

**1. GC Content Comparative Analysis**
| Metric | Original Sequence | Optimized Sequence | Status |
| :--- | :--- | :--- | :--- |
| **Overall GC Content** | 60.52% | **52.93%** | Target Reached |
| **Target Range** | 30% - 70% | 30% - 70% | Compliant |

*Technical Insight:* The pre-optimized sequence exhibited sharp local GC peaks exceeding 80% (particularly around the 1000 bp mark), which could cause RNA polymerase pausing or premature termination. Optimization flattened the GC distribution curve, minimizing complex mRNA secondary structures and ensuring stable translation in *K. pastoris*.


**2. Synonymous Codon Substitution**
Comprehensive DNA alignment revealed dense silent mutations to match the codon bias of *K. pastoris*. Rare codons were systematically replaced with abundant ones (e.g., `TTCTTCCCCTTC` to `TTTTTCCCATTT`). This prevents rare tRNA depletion, thereby increasing the translation elongation rate and preventing ribosomal stalling.

**3. Restriction Site Planning**
The sequence was screened using **GenScript Restriction Enzyme Map Analysis Tools**. Internal sites for **EcoRI** (`GAATTC`) and **NotI** (`GCGGCCGC`) were successfully excluded (0 occurrences). Finally, EcoRI and NotI flanking sequences were added to the 5' and 3' ends, respectively, to enable directional cloning. The final sequence was submitted for commercial chemical synthesis.

---

## 💻 Phase 3: In Silico Restriction-Based Cloning

Prior to wet-lab execution, the entire cloning strategy was simulated and validated using **CLC Genomics Workbench**.

* **Vector Preparation:** A customized *Pichia* expression vector (`Exported`) was utilized as the backbone. This vector harbors a `TEF1` promoter, an `alpha-factor` secretion signal for extracellular expression, and downstream elements including Myc and 6xHis tags.
* **Restriction Digestion:** Both the optimized `tpo` insert and the target vector were *in silico* digested using the selected endonucleases: **EcoRI** and **NotI**.
* **Ligation & Integration:** The 2.7 kb `tpo` fragment was successfully stitched into the vector backbone.
* **Sequence Verification:** The resulting circular plasmid (`Exported_tpo`) was analyzed. Sequence View and Circular Map visualizations confirmed:
    1.  Flawless integration at the specified restriction sites.
    2.  An intact Open Reading Frame (ORF). The mature TPO sequence is correctly maintained in-frame with the upstream $\alpha$-factor secretion signal, ensuring accurate post-translational processing and secretion by the yeast host.


---
*Developed by: AbdulAziz*
