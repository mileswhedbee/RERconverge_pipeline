# RERconverge_pipeline
Pre-processing steps from Cactus mammalian  [whole genome alignment](https://zoonomiaproject.org/the-data/) (Genereux, et al. 2020) (HAL file) to gene trees for RERconverge analyses (Kowalczyk et al. 2019). 

## Overview

```mermaid
graph TD;
    A["`_Multiple whole genome alignment: HAL_
       cactus-hal2maf`"]--Large HAL file split into chromosome maf files-->B[Chromosome maf files];
    B-->C;
    C-->D;
```

