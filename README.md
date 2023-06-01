# haila-ZoopMetabarcoding

This is the repository for my project analyzing metabarcoding data from zooplankton in Puget Sound from 2018-2020. Zooplankton samples were collected using vertical and oblique net tows at seven stations in April, July, and September. This workflow contains a bioinformatics pipeline that identifies the zooplankton taxa found in each sample.

This workflow was constructed and conducted using RStudio desktop on my local computer.

The report for this pipeline is located here: https://rpubs.com/HailaSchultz/full-pipeline-report
Rmd files for each step are located in the code directory, but the Schultz-Full-Pipeline.Rmd includes all of the code needed. 

## Getting the data
Samples were extracted and sequenced at Ohio State University.

I downloaded fastq files for the LrCOI marker onto my local machine in the folder "FASTQ_Generation_2022-07-03_03_27_35Z-580375800-20230407T223438Z-002.zip" from this page:https://drive.google.com/drive/folders/1poXFdaBpk1SnPIPDc3-212Xz39gHohIL

The code 01-download-data checks current versions of the file against the original version.

Hash values are located in haila-ZoopMetabarcodning/data/fastq.checksums.sha

## Identifying the endpoint

At the end of this project, I will be able to compare zooplankton communities identified by metabarcoding and the LrCOI marker. I will examine differences in communities on spatial and temporal scales, comparing annual differences, seasonal differences, and location differences. I will make NMDS plots to look at separations in zooplankton communities as well as stacked bar plots comparing relative proportions of various zooplankton taxonomic groups among the different samples. I will calculate diversity indices for each sample to see which conditions correlated with the highest zooplankton diversity.

The general order of operations (adapted from a workflow created by Sean McAllister who previously analyzed a subset of this dataset):

1. Trim adapters and amplicon primers from sequence reads (use Cutadapt).
notes on this step: it appears cutadapt doesn't work well with rstudio, but there is an option to open rstudio from within the conda environment, so I switched to working with my rstudio desktop. An original error I had connecting rstudio desktop to git was fixed when I typed `xcode-select --install` into the terminal.

2. Filter reads based on quality (use DADA2).
3. Merge forward and reverse reads.
4. Run BLASTn against the NCBI nt database as a reference.
5. Calculate diversity index for each sample.
6. Make NMDS plots colored by year, month, and location.
7. Make barplots to compare relative abunances among samples.

