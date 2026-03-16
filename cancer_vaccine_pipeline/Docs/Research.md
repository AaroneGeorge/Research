# DIY mRNA Cancer Vaccine: Paul Conyngham's AI-Powered Approach to Save His Dog Rosie

---

## The Person

Paul Conyngham is a Sydney-based tech entrepreneur who runs Core Intelligence, an AI/ML consultancy. He has 17 years of experience in machine learning and data science but no formal biomedical or biology degree. He adopted Rosie, a Staffordshire Bull Terrier–Shar Pei cross, from a shelter in 2019.

---

## The Problem

In 2024, large tumors appeared on Rosie's hind leg. She was diagnosed with mast cell cancer — the most common skin cancer in dogs and typically incurable. Conventional treatments — surgery, chemotherapy, and immunotherapy — all failed. She was given 1–6 months to live.

---

## Step-by-Step: How He Did It

### Step 1: Research Planning with ChatGPT

Conyngham opened ChatGPT and used it as a research assistant and brainstorming partner:

- Asked ChatGPT to help draft a research and development plan for designing a personalized cancer vaccine
- ChatGPT suggested immunotherapy as a promising direction and pointed him toward genomic sequencing of the tumor
- He iterated back and forth with ChatGPT throughout the entire process — it functioned as an always-available domain expert to help a non-biologist navigate oncology and vaccinology literature

> **Key insight:** ChatGPT wasn't "designing the vaccine" — it was acting as a tireless research co-pilot that helped Conyngham understand concepts, plan next steps, and process findings.

### Step 2: Tumor DNA Sequencing (~$3,000)

Conyngham contacted UNSW's Ramaciotti Centre for Genomics at the University of New South Wales. The process:

1. A biopsy sample was taken from Rosie's tumor
2. Next-Generation Sequencing (NGS) was performed — likely Whole Exome Sequencing (WES) of both the tumor tissue and matched healthy tissue
3. The DNA was extracted and converted into digital genetic data (FASTQ files → aligned reads → variant calls)
4. Cost: approximately $3,000 for the sequencing (this same process cost ~$100,000 a decade earlier)

### Step 3: Mutation Identification & Analysis

With gigabytes of genomic data in hand, Conyngham:

1. Compared tumor DNA to healthy cell DNA to identify somatic mutations specific to the cancer
2. Used ChatGPT to help analyze the large volumes of genetic information
3. Ran the data through bioinformatics pipelines to identify which mutations were likely driving the cancer (variant calling, filtering passenger vs. driver mutations)

### Step 4: Neoantigen Prediction with AlphaFold + Custom ML

This was the critical intellectual step:

1. AlphaFold (Google DeepMind's protein structure prediction tool, free and publicly available) was used to model the 3D structures of proteins encoded by the tumor's mutated genes
2. By understanding the 3D shape of the mutant proteins, he could identify which parts (epitopes/neoantigens) would be visible to the immune system and could serve as vaccine targets
3. Conyngham wrote his own custom machine learning algorithms for neoantigen selection — ranking which mutated proteins would most likely trigger a strong immune response
4. The output: a ranked list of the best neoantigen targets for the vaccine

**How AlphaFold fits in:** Neoantigens are mutated protein fragments displayed on the tumor surface. AlphaFold predicts how these mutant proteins fold in 3D space. This helps determine:

- Whether a mutation changes the protein surface (and would thus be "visible" to immune cells)
- Which epitopes are structurally accessible for immune recognition
- How different the mutant protein looks compared to the normal version

### Step 5: mRNA Vaccine Sequence Design

Conyngham designed the mRNA sequence — the output was described as a "half-page formula" — specifying:

- The mRNA coding sequence encoding the selected neoantigens (likely a polyepitope construct — multiple neoantigen sequences strung together)
- The sequence was likely codon-optimized for efficient translation in canine cells
- UTR (untranslated region) elements for stability and efficient expression

### Step 6: Vaccine Production at UNSW RNA Institute

Conyngham brought his sequence design to Professor Páll Thordarson, Director of the UNSW RNA Institute:

1. The researchers initially hesitated but agreed to collaborate after reviewing his analysis
2. Thordarson's team designed and produced the bespoke mRNA vaccine based on Conyngham's sequence
3. The mRNA was synthesized and encapsulated in lipid nanoparticles (LNPs) — the same delivery technology used in Pfizer/BioNTech and Moderna COVID-19 vaccines
4. Timeline from sequence handoff to finished vaccine: less than 2 months

### Step 7: Regulatory Approval

Conyngham spent approximately 3 months preparing documentation for ethical approval applications. He described this as more challenging than the actual development. The vaccine was administered with proper ethical approvals under veterinary supervision.

Dr. Rachel Allavena (University of Queensland) handled vaccine administration with ethical approvals.

### Step 8: Administration & Results

- **First injection:** December 2025
- **Booster shots:** Following months
- **Results within ~1 month:**
  - Primary tumor on leg: shrank by **75%**
  - Rosie regained mobility, started jumping fences and chasing rabbits again by January 2026
  - However: A second tumor on Rosie did not respond — indicating the approach has limitations

---

## Tools Used

| Tool | Cost | Role |
|------|------|------|
| ChatGPT (OpenAI) | ~$20/month | Research assistant, R&D planning, data interpretation, iterative strategy |
| AlphaFold (Google DeepMind) | Free | 3D protein structure prediction of mutant proteins |
| Custom ML algorithms (Conyngham's own) | Free (self-built) | Neoantigen selection and ranking |
| Next-Gen Sequencing (UNSW Ramaciotti Centre) | ~$3,000 | Tumor + healthy tissue DNA sequencing |
| UNSW RNA Institute lab | Collaborative/academic | mRNA synthesis, LNP formulation, vaccine production |
| Bioinformatics tools (likely BWA, GATK, etc.) | Free/open-source | Sequence alignment, variant calling |

**Total out-of-pocket cost:** ~$3,000 + ChatGPT subscription

---

## How mRNA Cancer Vaccines Work (Simplified)

```
Tumor Biopsy → DNA Sequencing → Find Mutations → Predict Neoantigens
                                                          ↓
                                                  Design mRNA Sequence
                                                          ↓
                                        Synthesize mRNA + Wrap in LNPs
                                                          ↓
                                                  Inject into Patient
                                                          ↓
                                  Cells read mRNA → Produce neoantigen proteins
                                                          ↓
                                  Immune system recognizes → Attacks tumor cells
                                      displaying those neoantigens
```

The vaccine teaches the immune system to recognize the specific mutant proteins unique to the tumor. Unlike chemotherapy (which kills all fast-dividing cells), this is a targeted approach — the immune system hunts down cells displaying those specific markers.

---

## Key People Involved

| Person | Role |
|--------|------|
| Paul Conyngham | Tech entrepreneur, Core Intelligence — drove the entire project |
| Páll Thordarson | Director, UNSW RNA Institute — designed & produced the mRNA vaccine |
| Rachel Allavena | University of Queensland — administered vaccine with ethical approvals |
| Martin Smith | UNSW Associate Professor, Computational Biology — research support |
| David Thomas | Director, UNSW Centre for Molecular Oncology — oversight |
| Kate Michie | UNSW Structural Biologist — found it "encouraging that a non-scientist could execute such a pipeline" |

---

## Is This Reproducible?

### What CAN be reproduced

- The general pipeline (sequence → identify mutations → predict neoantigens → design mRNA → produce vaccine) is well-established in academic oncology research
- AlphaFold is free and publicly available at [alphafold.ebi.ac.uk](https://alphafold.ebi.ac.uk)
- ChatGPT is commercially available
- DNA sequencing is now affordable (~$3,000)
- The scientific literature on neoantigen prediction is open access

### What CANNOT easily be reproduced

- Conyngham had 17 years of ML/data science expertise — he wasn't a random person; he wrote custom neoantigen selection algorithms
- The UNSW RNA Institute actually synthesized the mRNA and formulated the LNPs — this requires specialized lab equipment (in vitro transcription systems, microfluidic mixers for LNP production), expertise, and reagents that are not available to the general public
- Regulatory/ethical approval took 3 months of paperwork
- The "DIY" framing is somewhat misleading — critical steps required world-class university labs and domain experts (Thordarson is one of Australia's leading RNA scientists)

### Honest Assessment

The headline "man uses ChatGPT to make vaccine" overstates what happened. A more accurate description:

> A highly skilled ML engineer used ChatGPT as a research assistant, AlphaFold for protein modeling, and his own ML expertise to identify vaccine targets — then partnered with a leading university RNA lab that did the actual wet-lab synthesis and production.

The AI dramatically lowered the barrier to entry for the computational/bioinformatics side, but the wet-lab production still required institutional infrastructure.

---

## Critical Analysis

### Strengths

- Demonstrates AI can compress timelines and lower knowledge barriers in drug design
- $3,000 + free AI tools vs. millions in traditional pharma R&D
- Proves personalized cancer vaccines are feasible for veterinary use
- Scientists involved call it the first personalized cancer vaccine ever designed for a dog

### Limitations

- N=1 — single anecdotal case, not clinical evidence
- One tumor shrank 75%, but a second tumor didn't respond
- No control group, no blinding, no peer-reviewed publication yet
- No long-term durability data
- The immune response mechanism (T-cell activation, antibody levels) hasn't been publicly characterized
- ChatGPT can hallucinate — using it for medical/scientific decisions carries risk

### What Experts Say

- **Thordarson:** The approach "absolutely" could translate to human oncology; "we can democratize this technology"
- **Greg Brockman (OpenAI President):** Called it "the first personalized cancer vaccine designed for a dog"
- **Martin Smith:** "Raises the question of why similar approaches have not been implemented for human patients"

---

## Broader Context

This story sits at the intersection of several converging trends:

1. DNA sequencing costs dropped from $100M (2001) → $100K (2013) → $3K (2024)
2. AlphaFold (released 2021–2024) made protein structure prediction free and instant
3. LLMs like ChatGPT (2022+) made complex scientific literature accessible to non-specialists
4. mRNA technology was validated at scale by COVID-19 vaccines (Pfizer/Moderna)
5. BioNTech and Moderna are already running personalized mRNA cancer vaccine trials in humans (e.g., BioNTech's autogene cevumeran for pancreatic cancer showed 3-year persistence of immune response)

Paul Conyngham essentially stitched together publicly available tools that didn't exist even 5 years ago to create something that previously required a pharmaceutical company.

---

## Sources

- [AI-Designed mRNA Vaccine Shrinks Dog's Cancer Tumor | Awesome Agents](https://awesomeagents.ai)
- [DIY mRNA Cancer Vaccine Analysis | Blockchain News](https://blockchain.news)
- [ChatGPT and AlphaFold Case Study | Blockchain News](https://blockchain.news)
- [Tech entrepreneur uses ChatGPT for dog vaccine | PapaLinc](https://papalinc.com)
- [AI helps Australian man develop cancer vaccine | Storyboard18](https://storyboard18.com)
- [Dog's Cancer Cure via ChatGPT | Archyde](https://archyde.com)
- [Trung Phan on X](https://x.com)
- [Anish Moonka on X](https://x.com)
- [Greg Brockman on X](https://x.com)
- [Neoantigen cancer vaccines review | Cancer Biology & Medicine](https://cbmjournal.com)
- [mRNA Cancer Vaccines review | PMC](https://pmc.ncbi.nlm.nih.gov)
- [AI-powered mRNA vaccine engineering | Frontiers in Oncology](https://frontiersin.org)
