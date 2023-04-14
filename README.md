# BMP9_FSS_ATAC_analysis
Code used in the data analysis of hte paper titled as " BMP9 and Fluid Shear Stress  regulate endothelial chromatin accessibility  and expression of SMAD low affinity target genes"


The paper analyses ATAC-seq data of 4 different conditions:

| conditions    | with BMP        |  witho BMP |
| :------------ |:---------------| :------------------|
| **with FSS**  | 1.	BMP9_flow   | 2.	control_flow   |
| **witho FSS** | 3.	BMP9_static |  4.	control_static |

Analysis steps:
0. Pre-process the data according to [ENCODE ATAC-seq pipeline](https://github.com/ENCODE-DCC/atac-seq-pipeline)

1. Which regions are common and differentially accessible in different conditions | Find differentially accessible regions
  - Differential accessibility analysis via [DiffBind](https://bioconductor.org/packages/release/bioc/html/DiffBind.html) || [vignette](vignettes/TF_motif_enrichment_HOMER.ipynb)
2. What are the closest genes to the differential regions | Annotate the differential regions by the closest promoter in gene symbol || [vignette](vignettes/annotate_by_closeset_TSS.ipynb)
3. What is the overlap of the accessible regions between different conditions || [vignette](vignettes/find_overlaps_between_regions.ipynb)
4. Which TFs are enriched in the interested regions of interests || [vignette](vignettes/TF_motif_enrichment_HOMER.ipynb)

   Find enriched motif sequences within the differentially accessible regions for:

      a. Regions specific to BMP9 stimulation only: BMP9_static VS control_static

      b. Regions specific to flow only: control_flow VS control_static

      c. Regions different between BMP9 stimulation and flow: (BMP9_static VS control_static) VS (control_flow VS control_static)  

- Reformat the input for HOMER
- Perform de novo and known motif enrichment analysis via HOMER 


4. We are interested in 3 TFs (GC-SBEs, 5bp GC-SBEs and SBEs) found in the analysis. What are the Further investigate the 3 TFs: GC-SBEs, 5bp GC-SBEs and SBEs
- Find the BMP9 specific regions that can be bound by the above-mentioned TFs & Obtain the sequences of these regions || [vignette]vignettes/get_regions_binging_both_motif5_and_motif6_200bp.ipynb)
- Find the number of sequence matches for each TF || [vignette](vignettes/TF_sequence_match_analysis.ipynb)
