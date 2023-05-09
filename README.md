# haila-ZoopMetabarcoding

This is the repository for my project analyzing metabarcoding data from zooplankton in Puget Sound from 2018-2020. Zooplankton samples were collected using vertical and oblique net tows at seven stations in April, July, and September. I will create a bioinformatics pipeline that identifies the zooplankton taxa found in each sample.

## Getting the data
The HTML for this step is here: https://rpubs.com/HailaSchultz/download-data

I downloaded fastq files for the LrCOI marker onto my local machine in the folder "FASTQ_Generation_2022-07-03_03_27_35Z-580375800-20230407T223438Z-002.zip" from this page:https://drive.google.com/drive/folders/1poXFdaBpk1SnPIPDc3-212Xz39gHohIL

I then uploaded the zipped file into Raven using the Rstudio upload function (when working in the desktop I did not have to upload)

Hash values are located in haila-ZoopMetabarcodning/data/fastq.checksums.sha

The code 01-download-data checks current versions of the file against the original version.

I noticed that some files were missing from the original download (mostly 2018 and 2020 data), so I downloaded to my computer again on May 1, 2023. Downloaded zipped file is available on my computer at users/hailaschultz/GitHub/haila-ZoopMetabarcoding


## Identifying the endpoint

At the end of this project, I will be able to compare zooplankton communities identified by metabarcoding and the LrCOI marker. I will examine differences in communities on spatial and temporal scales, comparing annual differences, seasonal differences, and location differences. I will make NMDS plots to look at separations in zooplankton communities as well as stacked bar plots comparing relative proportions of various zooplankton taxonomic groups among the different samples. I will calculate diversity indices for each sample to see which conditions correlated with the highest zooplankton diversity.

The general order of operations (adapted from a workflow created by a collaborator who previously analyzed a subset of the dataset I have):

1. Trim adapters and amplicon primers from sequence reads (use Cutadapt).
notes on this step: it appears cutadapt doesn't work well with rstudio, but there is an option to open rstudio from within the conda environment, so I am switching to working with my rstudio desktop. The original error I had connecting rstudio desktop to git was fixed when I typed `xcode-select --install` into the terminal.
2. Filter reads based on quality (use DADA2).
- this code is complete, I just need to re-run after filtering out the files that didn't make it through the cutadapt step.
3. Merge forward and reverse reads.
4. Run BLASTn against the NCBI nt database as a reference.
5. Use Taxonkit to convert BLAST results to a taxonomic heirarchy.
6. Calculate diversity index for each sample.
7. Make NMDS plots colored by year, month, and location.
8. Make barplots to compare relative abunances among samples.

## multiqc files 
The multiqc file of the raw data files are located here: haila-ZoopMetabarcoding/output/raw-read-qc

here is the multiqc file after using cutadapt: haila-ZoopMetabarcoding/output/after-cutadapt-qc

