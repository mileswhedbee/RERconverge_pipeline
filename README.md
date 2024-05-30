# RERconverge_pipeline
Pre-processing steps from Cactus mammalian  [whole genome alignment](https://zoonomiaproject.org/the-data/) (Genereux, et al. 2020) (HAL file) to gene trees for RERconverge analyses (Kowalczyk et al. 2019). 

## Overview

```mermaid
graph TD;
    A[Multiple whole genome alignment: HAL]-->B[Chromosome maf files];
    A-->C;
    B-->D;
    C-->D;
```

