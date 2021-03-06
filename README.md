# taxonsluice
Heuristic algorithm for decontamination of OTU tables: The currently accepted input to this program is a mothur-formated OTU table. However, we are currently working on making this tool compatibale with QIIME output and amplicon sequence variants (ASVs).

Please see the Wiki for Taxonsluice for more information on the algorithm, its installation, and a mock community example.

## Dependencies
-Python3

-BLAST

## Usage

This script takes as input the mothur-formatted tab-delimited OTU table (see sampleOTUtable.txt for specific format of this), as well as a tab-delimited file that maps each sample to a corresponding blank (see sample_blank_map.txt for specific format).

This script will run with only these two inputs, and output two files: 

  -an OTU table with only the OTUs whose abundance in the sample-specific and non-specific-blanks is 10% or less of the abundance in the environmental samples.

  -an OTU table containing sequences that were flagged due to presence within blanks

However, if you provide the script with the location of the SILVA database, and a fasta file containing the OTU sequences, an additional output will include an annotated summary of the OTUs that were flagged. This output will include the closest match to the flagged OTUs in SILVA, the study in which those matches originated, and the source of isolation.

The SILVA database can be downloaded from https://www.arb-silva.de/no_cache/download/archive/current/Exports/. The file you should get is "SILVA_132_SSUParc_tax_silva.fasta.gz". As of April 2018, release 132 is the latest release.

### sample command (with the representative 16S sequences in FASTA format and SILVA database provided for classification of potentially-rare OTUs)
    python3 taxonsluice.py -blank_map mySamplesToBlanks.txt -otu_table myOTUs.txt -seq_file myOTUs.fasta -silva_DB SILVA_128_SSURef_tax_silva.fasta -rare 5 -t 4 -silva_aln 10 -out_folder /path/to/output/directory/

### sample command (simple version without 16S or SILVA database provided)
    python3 taxonsluice.py -blank_map mySamplesToBlanks.txt -otu_table myOTUs.txt -rare 5 -out_folder /path/to/output/directory/

# Citing taxnosluice:
taxonsluice is developed by Gustavo A. Ramírez & Arkadiy Garber in collaboration with Beth N. Orcutt, Bigelow Laboratry for Ocean Sciences, Maine, USA.

This project is still a work in progress, and is involved in a publication currently in review. If it was useful for your work, you can cite it as: Ramírez, G.A., Garber, A.I., and Orcutt, B.N. 2018: taxonsluice, GitHub repository: https://github.com/Arkadiy-Garber/taxonsluice/.


Please also cite various dependencies used by taxonsluice.
