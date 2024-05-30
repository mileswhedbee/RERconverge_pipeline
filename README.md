# RERconverge_pipeline
Pre-processing steps from Cactus mammalian  [whole genome alignment](https://zoonomiaproject.org/the-data/) (Genereux, et al. 2020) (HAL file) to gene trees for RERconverge analyses (Kowalczyk et al. 2019). 

## Overview

```mermaid
graph TD;
    A["`**Multiple whole genome alignment: HAL**
       cactus-hal2maf
       _--noAnc:_ remove ancestral nodes
       _--dupeMode single:_ remove multiple sequences from same species in each block
       _--refGenome:_ species to use as ref genome
       _--refSeq:_ select sequence to subset whole alignment (e.g. chromosome)
       _--targetGenomes:_ list of genomes to subset alignment`"]--Large HAL file split into chromosome maf files-->B[Chromosome maf files];
    B-->C;
    C-->D;
```

