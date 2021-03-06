=======
History
=======

Release v0.1.0 (21/05/2019)
===========================
* support the estimate the genotype and genotype likelihood for each cell.
  The GT is for 0/0, 1/0, 1/1, while the genotype likelihood is for 0/0, 1/0,
  1/1, and 0/0+1/0, 1/1+1/0.
  The genotype estimate is based on the this paper (table 1; same as supp table
  S3 in Demuxlet paper): https://doi.org/10.1016/j.ajhg.2012.09.004
* cell tag changed from CR to CB and the lane info is kept
* pileup whole genome uses the same reads filtering as pile up positions
* add test files (note, the bam file is 19G)
* require pysam>=0.15.2 to get the qqual for each base call in the reads


Release v0.0.8 (21/12/2018)
===========================
* update the default setting that UMItag is not in use in bulk RNA-seq, as UMI 
  is cell specific in pseudo-bulk RNA-seq, hence better turn it UMI off by
  default 
* support output file in the same path of command line
* support cram input file, besides bam/sam 
* update readme file, especially for processed common variants from 1000 genome 
  project (https://sourceforge.net/projects/cellsnp/files/SNPlist/)

Release v0.0.7 (04/10/2018)
===========================
* change the header of the VCF file to be more suitable for bcftools
* realise the issue of heavy memory consuming, which even kills the 
  jobs in cluster. The menory taken increase linearly to the number 
  of processors used. When using 20 CUPs, >20G memory is recomended 
  for >5K cells. Solution for higher memory efficiency will be 
  proposed in future.

Release v0.0.6 (29/09/2018)
===========================
* fix the bug in pileup a list of positions with ``pysam-fetch``: 
  input wrong REF and ALT bases.
* support pileup a list of positions for multiple bulk samples
* check liftOver works fine: the last part of the SNPs have matched
  REF in fasta file.
* polish the printout log: label the three modes: 
  
  * Mode 1: Pileup a list of positions for single cells (most common)
  * Mode 2: Pileup whole genome for single cells
  * Mode 3: Pileup a list of positions for (multiple) bulk sample(s)

Release v0.0.5 (24/09/2018)
===========================
* pileup a list of positions with ``pysam-fetch``, which may returns more
  reads than ``pysam-pileup``. This feature requires further check
* change vcf file header to be more compatible with bcftools
* support turning cell-barcode off to return a sample level only

Release v0.0.4 (25/08/2018)
===========================
* pileup the whole genome for 10x single-cell RNA-seq data
* Note, post-filetering is needed as the current filtering doesn't 
  consider the heterozygous genotype for all donors.

