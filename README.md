# Info
Collection of sequencing adapter/primer sequences (mainly Illumina) from all around the internet. I appologize but this list is so old I no longer remember most of the sources where I got it from.

Each adapter has it's reverse-complement "version" at the end since I've observed this "version" in the past at some experiments.

The code to merge & deduplicate sequences is from [Stephen Turner](https://github.com/stephenturner/adapters).

# Notes
Make sure your adapter fasta is one-line fasta:
```
cat adapters.fa | awk '/^>/ { if(NR>1) print "";  printf("%s\n",$0); next; } { printf("%s",$0);}  END {printf("\n");}' > adapters-oneline.fa
```

Merge and deduplicate with [combine_adapters.R](combine_adapters.R):
```
R --no-save < combine_adapters.R
```
The adapter file/files have to be in this directory (doesn't go recursive) and must have *.fa* (**not** *.fasta*) suffix.

# Sources
* [https://github.com/OpenGene/fastp/blob/master/src/knownadapters.h](https://github.com/OpenGene/fastp/blob/master/src/knownadapters.h)
* [https://github.com/stephenturner/adapters/blob/master/adapters_combined_256_unique.fasta](https://github.com/stephenturner/adapters/blob/master/adapters_combined_256_unique.fasta)
* [https://github.com/BioInfoTools/BBMap/blob/master/resources/adapters.fa](https://github.com/BioInfoTools/BBMap/blob/master/resources/adapters.fa)
* Other sources I have forgotten about (I apologize).
