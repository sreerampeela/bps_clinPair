# bps_clinPair
Supplementary files for Bps clinical pair:

The repository contains all the intermediate files generated during the analysis of paired Burkholderia pseudomallei 
isolates obtained from a single patient in two different episodes.
Overall, the following tools were used with local resources:

1. Read QC: FASTQC
2. Genome assembly: Shovill pipeline
   Outputs: Contigs for each assembly
   Parameters: all default parameters, except contig size set to a minimum of 100bp
3. Annotation: Prokka
   Input: contigs
   Parameters: genbank-compliant
               find ncRNA - "--rfam"
5. Variant calling: Snippy
   Outputs: VCF and BAM file
   Input: EX14915 annotation in GBK format
   Parameters: minimum coverage- 10
               minimum mapping quality- 60
6. Coverage estimation: TIDDIT cov
   Input: BAM and reference files from Snippy
   Output: Coverages in BED format
7. Structural variants: TIDDIT SV
   Input: BAM and reference files from Snippy
   Parameters: Polidy (-n) - 1
               force_ploidy - yes
   Output: SVs in VCF format
   This VCF file is filtered to include only INDELS, Tandem duplications and inversions. The contig breaks ("BND") were excluded for analysis
8. Visualization: BRIG
   Input: GBK files of EX14915, EX7035, MSHR7901 (ref)
   Parameters: Max identity - 100
               Min identity - 70

The other tools have dedicated webservers and their parameters were mentioned in the manuscript file
