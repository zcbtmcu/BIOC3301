# BIOC3301 Data Analysis Code 

This repository contains the code used for the data analysis portion of the project "Determination of temporal changes in the composition and diversity of a core microbiome in Central London".
The bioinformatics pipleline QIIME was utilised on the Cartesius high performance computing cluster.

## Order of workflow:

1) joined_paired_ends_script.pbs - Joined Read1 and Read2 fastq files for the 2018 data set, not carried out for 2016/17 due to the poor quality of Read2. 

2) Demultiplexing_script.pbs, Demultiplexing_2017.pbs, Demultiplexing_2016.pbs - Demultiplexed the 2018, 2017 and 2016 data sets, respectively.

3) Picking_OTUs_closed_SILVA.pbs, Picking_OTUs_2017.pbs, Picking_OTUs_2016.pbs - OTUs were picked closed reference for the 2018, 2017 and 2016 data sets, respectively, using the SILVA reference database.

4) remove_samples.pbs - Removed the samples from the 2018 data set that were not collected in Gordon Square Garden.

5) merge_OTUs_all.pbs - The OTU tables from the 3 data sets were merged. 

6) Diversity_analysis_merged.pbs - Ran core diversity analysis using this merged OTU table. 

7) compute_core_microbiome_2018.pbs, compute_core_microbiome_2017.pbs, compute_core_microbiome_2016.pbs - Computed the core microbiomes of each data sets using various cut-off levels. A 90% level was selected.

8) merge_OTUs_core_90.pbs - Merged the OTU tables containing the core microbiomes for each data set.

9) core_diversity_merged_core_90.pbs - Carried out core diversity analysis using this merged OTU table containing the core microbiomes. 

10) summarize_taxa_merged_core_90.pbs - The OTU table was summarised at the phlyum level.

11) make_heatmap_core_90.pbs - Generated a heat map based on the abundances of the OTUs summarised at phylum level for each sample. 

12) jackknifed_beta_diversity_core_merged_90.pbs - Generated weighted UniFrac distances and repeatedly resampled a subset of the data for each sample to test the robustness of the clustering.

13) adonis_weighted_core.pbs, anosim_weighted_core.pbs - Carried out adonis and ANOSIM statistical tests, respectively, to assess the significance of the beta diversity based on year.

14) group_significance_core_90_KW.pbs - Carried out a Kruskal-Wallis test to assess the significance of the alpha diversity based on year.

15) split_core_90_merged_phyla.pbs - Split the merged OTU table containing the core microbiomes to phylum level. 

16) Proteobacteria_core_diversity_analysis.pbs - Ran core diversity analysis using the split OTU table for Proteobacteria. 

17) adonis_weighted_Proteobacteria.pbs, anosim_weighted_Proteobacteria.pbs - Carried out adonis and ANOSIM statistical tests, respectively, to assess the significance of the beta diversity in the Proteobacteria phylum based on year.

18) summarize_taxa_Proteobacteria.pbs - The OTU table for Proteobacteria was summarized at the class level.

19) group_significance_core_Proteobacteria.pbs - Carried out a Kruskall-Wallis test to assess the significance of the alpha diversity at the class level of Proteobacteria based on year.
