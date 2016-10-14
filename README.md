# hichipper

[![Build Status](https://travis-ci.org/aryeelab/hichipper.svg?branch=master)](https://travis-ci.org/aryeelab/hichipper)

The hichipper package implements our data processing and quality control pipeline for HiChIP data. This package takes aligned `.bam` files and a parameter manifest file (.yaml) as input and produces output that can be used to 1) determine quality of library prep, 2) visualize loops interactively, and 3) estimate per-loop statistical confidence measures.

![hichipper_overview](overview.png)

## Dependencies

The following dependencies need to be manually installed and available in the PATH when executing the commands. 

- samtools
- bedtools

Additionally, to produce a QC report, R must be available in the environment as well as these packages:

- dplyr
- foreach
- ggplot2
- gridExtra
- reshape2
- scales

These can all be installed (if needed) running these lines of code in the R console--

```
install_pkgs <- function(pkg){
    new.pkg <- pkg[!(pkg %in% installed.packages()[, "Package"])]
    if (length(new.pkg)) install.packages(new.pkg, dependencies = TRUE)
}
install_pkgs(c("dplyr", "foreach", "ggplot2", "gridExtra", "reshape2", "scales"))
```

Finally, to produce a `.rds` file for immediate visualization of loops in [DNAlandscapeR](https://dnalandscaper.aryeelab.org),
the package `diffloop` must be installed either from Bioconductor or aryeelab. Run the following commands in the R console to get `diffloop` (if needed).  

```
install.packages("devtools") # if needed
devtools::install_github("aryeelab/diffloop")
```

## Installation

To install hichipper given the dependencies above, simply run:

    $ pip install hichipper

## Usage example

The example below uses the test dataset bundled with the `hichipper` package source code. Download the package with:

`git clone https://github.com/aryeelab/dnaloop.git`


1. Create a sample description file:
  
  Sample description files can be created with the `.yaml` format. 

  **Processing `.yaml` format**
   
   Example [yaml](https://en.wikipedia.org/wiki/YAML) format sample description file:
   
   ```
   samples:
      test_sample1: 
        - bam/t_1_hg19.bwt2merged.bam bam/t_2_hg19.bwt2merged.bam
      test_sample2:
	- bam/t_1_hg19.bwt2merged.bam bam/t_2_hg19.bwt2merged.bam
   ```
   
  In this example, the `test_sample1` sample is defined the `t_1_hg19.bwt2merged.bam` and `t_2_hg19.bwt2merged.bam` which
  where output files from [HiC-Pro](https://github.com/nservant/HiC-Pro). Any `.bam` files from Hi-C preprocessing
  software should be valid input. 
  
  
2. Run the pipeline:
  ```
  $ hichipper --out output1 example.yaml
  ```

## Usage details
  ```
  $ hichipper --help
  Usage: hichipper [OPTIONS] file.yaml

  A preprocessing and QC pipeline for ChIA-PET data.

  Options:
    --out TEXT         Output directory name  [required]
    --peak-pad TEXT    Peak padding width (applied on both left and right)
    --merge-gap TEXT   Max gap size for merging peaks
    --keep-temp-files  Keep temporary files?
    --no-R     	       Skip QC report generation and creation of .rds file? (Requires R)
    --help             Show this message and exit.

