# haila-ZoopMetabarcoding

This is the repository for my project analyzing metabarcoding data from zooplankton in Puget Sound from 2018-2020. Zooplankton samples were collected using vertical and oblique net tows at seven stations in April, July, and September. I will create a bioinformatics pipeline that identifies the zooplankton taxa found in each sample.

I downloaded fastq files for the LrCOI marker onto my local machine in the folder "FASTQ_Generation_2022-07-03_03_27_35Z-580375800-20230407T223438Z-002.zip" from this page:https://drive.google.com/drive/folders/1poXFdaBpk1SnPIPDc3-212Xz39gHohIL

I then uploaded the zipped file into Raven using the Rstudio upload function

Hash values are located in haila-ZoopMetabarcodning/data/fastq.checksums.sha

The code 01-download-data checks current versions of the file against the original version.