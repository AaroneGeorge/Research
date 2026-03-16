# mRNA Cancer Vaccine Pipeline — Feasibility Analysis

---

## The Pipeline Broken Into Two Halves

---

### Half A: Computational (CAN be automated by an agent)

| Step | Tool | Automatable? | Constraint |
|------|------|-------------|------------|
| 1. Read QC & trimming | fastp, FastQC | Yes | Input: FASTQ files (50–200 GB per sample) |
| 2. Alignment to reference genome | BWA-MEM2 | Yes | Needs reference genome (~3 GB download for hg38) |
| 3. Sort/Index | Samtools | Yes | Straightforward |
| 4. Somatic variant calling | GATK Mutect2 | Yes | Needs tumor + matched normal; 16–64 GB RAM, hours of compute |
| 5. Variant annotation | VEP / Funcotator | Yes | Needs annotation databases |
| 6. HLA typing | OptiType / arcasHLA | Yes (human) | Canine DLA typing: very limited databases |
| 7. Neoantigen prediction & ranking | pVACseq (pVACtools) | Yes | This tool was literally built for this exact pipeline |
| 8. Protein structure modeling | AlphaFold / ColabFold | Yes | Needs GPU (8 GB+ VRAM), or use API |
| 9. Codon optimization | CodonW, custom scripts | Yes | — |
| 10. mRNA sequence design | RNAfold (ViennaRNA) + scripts | Yes | UTR design is less standardized |
| 11. Report generation | Agent/script | Yes | — |

---

### Half B: Wet Lab + Clinical (CANNOT be automated by software)

| Step | What's Needed | Why It Can't Be Automated |
|------|--------------|--------------------------|
| 12. mRNA synthesis | In vitro transcription kits, T7 polymerase, modified nucleotides (N1-methylpseudouridine) | Physical chemistry |
| 13. LNP formulation | Microfluidic mixer, ionizable lipids, cholesterol, PEG-lipid, helper lipids | Physical nanotechnology |
| 14. Quality control | HPLC, gel electrophoresis, endotoxin testing, encapsulation efficiency assays | Lab instruments |
| 15. Regulatory approval | Ethics committees, paperwork | Human/institutional process |
| 16. Administration | Veterinarian/physician, sterile injection | Medical act |

---

## Honest Answer

Yes, Half A is technically feasible to automate as a skill/agent. Here's specifically what it would look like:

```
INPUT:  Tumor FASTQ + Normal FASTQ  (or pre-called VCF file)
        ↓
        fastp → BWA-MEM2 → Samtools → Mutect2 → VEP → pVACseq → AlphaFold → CodonOpt
        ↓
OUTPUT: Report containing:
        - Ranked neoantigens with MHC binding affinities
        - Predicted immunogenicity scores
        - Designed mRNA sequences (codon-optimized)
        - Protein structure visualizations
        - Recommended polyepitope construct
```

pVACtools (from Washington University in St. Louis) is specifically an open-source pipeline that does steps 5–7 end-to-end. It's used in actual clinical trials.

---

## Hard Constraints

### 1. Compute Requirements — Not Trivial

| Resource | Requirement |
|----------|-------------|
| WES FASTQ files | 50–200 GB per sample (tumor + normal = 100–400 GB) |
| BWA alignment | 16–64 GB RAM, 2–8 hours |
| GATK Mutect2 | 16+ GB RAM, 4–12 hours |
| AlphaFold (local) | GPU with 8+ GB VRAM, ~minutes per structure |
| Total disk space | ~500 GB minimum |

This won't run on a laptop. You'd need a workstation or cloud instance (AWS, GCP). A single run on AWS would cost roughly **$20–50** in compute.

### 2. Environment Setup Is Complex

The bioinformatics stack requires:
- Reference genome downloads (hg38: ~3 GB, or canFam6 for dogs)
- Annotation databases (VEP cache: ~15 GB)
- Conda/Docker environments with specific dependency versions
- GATK requires Java, pVACtools requires Python 3.8+, AlphaFold requires CUDA

This is realistically a Docker container, not a "just run it" script.

### 3. Species Problem

For **dogs** specifically:
- Canine DLA (Dog Leukocyte Antigen) typing databases are sparse — far less characterized than human HLA
- NetMHCpan has some canine MHC alleles but coverage is poor
- pVACseq is primarily designed for human genomes
- This is likely why Conyngham wrote custom ML algorithms — the off-the-shelf tools don't fully support canine immunogenomics

For **humans**: the pipeline is much more mature and well-supported.

### 4. The Output Is a Prediction, Not a Cure

The agent would output an mRNA sequence on a screen. The gap between that and an injectable vaccine requires:
- A lab with mRNA synthesis capability (~$50K+ in equipment)
- LNP formulation expertise and equipment
- Quality control instrumentation
- A licensed professional to administer it

---

## What a Realistic Skill File Could Actually Do

A skill file that is honest about its scope would:

**Name:** `neoantigen-pipeline`  
**Input:** VCF file (pre-called variants) OR raw FASTQ files  
**Requires:** Docker, 64 GB RAM, 500 GB disk, GPU (optional for AlphaFold)

**Steps:**
1. Validate inputs
2. If FASTQ: run alignment + variant calling (BWA + GATK)
3. If VCF: skip to annotation
4. Annotate variants (VEP)
5. Run HLA typing (OptiType)
6. Run neoantigen prediction (pVACseq)
7. Optionally model top candidates (ColabFold)
8. Design mRNA sequences (codon optimization + UTR selection)
9. Generate structured report

**Output:** PDF/HTML report with:
- Candidate neoantigens ranked by predicted immunogenicity
- MHC binding predictions
- Designed mRNA sequences
- Structural models of top candidates
- Recommended polyepitope construct sequence

This is genuinely useful — it's essentially what bioinformatics teams at cancer centers do, packaged as an automated pipeline. The computational side is well-established.

---
