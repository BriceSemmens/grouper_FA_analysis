**Fatty Acid Signatures Reveal Trophic Niche Partitioning in Spawning Groupers**

This repository contains data and analysis code for fatty acid profiling of grouper eggs from the Little Cayman spawning aggregation. The work demonstrates species-specific maternal investment strategies and trophic niche partitioning among three sympatric Caribbean grouper species.

🔬 Project Overview
This study analyzes fatty acid (FA) composition in eggs from Nassau Grouper (Epinephelus striatus), Tiger Grouper (Mycteroperca tigris), and Yellowfin Grouper (M. venenosa) collected during active spawning at the west-end spawning aggregation site in Little Cayman, Cayman Islands (2023-2024 spawning seasons).
Key Findings:

Maternal FA signatures remain stable during first 24 hours post-fertilization
Species identity explains ~17% of FA variance after controlling for maternal effects
Tiger Grouper eggs contain highest DHA and ARA provisioning
Both Mycteroperca species provision more EPA than Nassau Grouper
FA profiles reveal distinct trophic niches aligned with known foraging behaviors

📊 Data Description
File: Cayman_Grouper_2023-24_FA_results.csv

Samples: 58 egg samples from 3 species

Nassau Grouper: n = 30
Tiger Grouper: n = 14
Yellowfin Grouper: n = 14


Sampling times: Early (3 hpf) and Late (22 hpf) development stages
Measurements: 27 individual fatty acids expressed as % of total identified FAs
Grouping variable: Spawning burst ID (proxy for individual females)

Data Columns

Analysis: Sample type (all "bulk")

Time (hpf): Hours post-fertilization (3 or 22)

Species: Full species name with scientific name

Spawning burst ID: Individual spawning event identifier (maternal grouping)

Date Collected/Fertilized: Collection date

C14_0_pct through C22_6n3_pct: Individual fatty acid percentages

Derived metrics: FA ratios, sums by saturation class, n-3:n-6 ratios


🛠️ Installation & Requirements

R Version

Tested with R 4.4.0 or higher

Required Packages

rinstall.packages(c(

  "tidyverse",      # Data manipulation and visualization
  
  "vegan",          # Community ecology (PERMANOVA, RDA)
  
  "janitor",        # Data cleaning
  
  "ggrepel",        # Non-overlapping text labels
  
  "lme4",           # Linear mixed-effects models
  
  "lmerTest",       # p-values for LMMs
  
  "emmeans",        # Post-hoc comparisons
  
  "compositions",   # Compositional data analysis (CLR)
  
  "zCompositions",  # Zero replacement for compositional data
  
  "scales",         # Axis scaling functions
  
  "patchwork"       # Multi-panel figures
  
))



### Output Files

The script generates:

**Figures (PDF, 300 dpi):**
- `Figure_1_temporal_stability.pdf` - LC-PUFA stability over development
- `Figure_2_RDA_ordination.pdf` - Partial RDA showing trophic differentiation
- `Figure_3_LCPUFA_provisioning.pdf` - Species-specific DHA, EPA, ARA provisioning
- `Figure_4_FA_heatmap.pdf` - Heatmap of 25 most variable FAs
- `Figure_5_FA_ratios.pdf` - Diagnostic trophic biomarker ratios

**Data Tables:**
- `Table_1_Summary_Statistics.csv` - Mean ± SD for key FAs by species

**Console Output:**
- Zero replacement diagnostics
- PERMANOVA results (species, time, interaction effects)
- RDA variance partitioning
- Linear mixed-effects model results (DHA, EPA, ARA)
- Post-hoc pairwise comparisons

Compositional Data Analysis

Zero replacement using CZM method (Baruzzo et al. 2022)
Centered log-ratio (CLR) transformation (Aitchison 1986)


Temporal Stability (PERMANOVA)

Model: FA ~ species + hpf + species:hpf
Distance: Euclidean (on CLR-transformed data)
Strata: Spawning burst ID (controls for maternal effects)
Result: No significant species × time interaction (p = 0.810)


Trophic Niche Differentiation (Partial RDA)

Model: FA ~ species + Condition(spawning_burst_id)
Removes maternal variation before testing species effects
Species explains ~10% of variance after conditioning


Maternal Provisioning (Linear Mixed-Effects Models)

Fixed effect: Species
Random effect: Spawning burst ID (maternal variation)
Response variables: DHA, EPA, ARA concentrations
Post-hoc: Tukey-adjusted pairwise comparisons



Key Fatty Acids

DHA (C22:6n-3): Neural/retinal development, pelagic food web marker
EPA (C20:5n-3): Immune function, diatom-based production marker
ARA (C20:4n-6): Stress response, benthic/terrestrial energy marker

📖 Background
Fish spawning aggregations (FSAs) concentrate adults from disparate foraging grounds, providing a natural "aggregator" of trophic signals from across the seascape. The Little Cayman FSA represents a conservation success story where sustained protection has enabled recovery of grouper populations, creating a study system that approximates pre-exploitation dynamics.
Fatty acids function as:

Diet-derived biomarkers - Discriminate among energy pathways (pelagic vs. benthic)
Currency of maternal investment - Essential LC-PUFAs determine offspring quality

This dual lens allows simultaneous inference of adult trophic ecology and species-specific maternal allocation strategies.
🤝 Contributing
This is a research data repository associated with an in prep manuscript. While we welcome feedback and questions, we are not currently accepting code contributions. If you identify issues with the data or analysis, please open an issue.
📧 Contact
Principal Investigator: Brice Semmens
Institution: Scripps Institution of Oceanography, UC San Diego
Email: Bsemmens@ucsd.edu
Project Website: Grouper Moon Project
🙏 Acknowledgments
This work was conducted under research permissions from the Cayman Islands Department of Environment. We thank the Grouper Moon partnership, local dive operators, and community members of Little Cayman for their continued support of grouper conservation and research.
