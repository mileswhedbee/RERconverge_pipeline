# RERconverge_pipeline
Pre-processing steps from Cactus mammalian  [whole genome alignment](https://zoonomiaproject.org/the-data/) (Genereux, et al. 2020) (HAL file) to gene trees for RERconverge analyses (Kowalczyk et al. 2019). 

## Overview

```mermaid
graph TD;
    A["`**Multiple whole genome alignment: HAL**
       _cactus-hal2maf_
       _--noAnc:_ remove ancestral nodes
       _--dupeMode single:_ remove multiple sequences from same species in each block
       _--refGenome:_ species to use as ref genome
       _--refSeq:_ select sequence to subset whole alignment (e.g. chromosome)
       _--targetGenomes:_ list of genomes to subset alignment`"]--Large HAL file split into chromosome maf files-->B["`**Chromosome maf files**
                                                                                                                    _mafExtractor_`"];
    B--Use annotation file (BED) to generate gene maf files-->C("`**Gene maf files**
                                                                  _merge_blocks.py_`");
    C--Uses get_spliced() from Bio.AlignIO to splice maf blocks-->D("`**Gene aligned fasta files**
                                                                      _Count_SeqNucs_selectLongest.sh_`");
    E("`_Pull_coords.sh_
        _Remove_blankLines.sh_`")--Generate start/stop coordinates for splcing maf blocks and remove empty maf files-->C;
    D--Select longest species sequence, remove all others-->F("`**Deduplicated species gene aligned fasta files**
                                                                _Convert_fasta_header.sh_`");
    F--Modify fasta header to species name only-->G("`**Header converted gene aligned fasta files**
                                                      _Build_gene_trees.R_`");
    G--Uses R Phangorn::estimatePhangornTreeAll() to generate ML gene trees-->H("`**Gene tree file for RERconverge**`");
```

