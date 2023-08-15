# Eukfinder
A bioinformatics tool designed to enable rapid recovery of high-quality draft genomes of microbial eukaryotes from various environmental metagenomic samples.

- reference-independent and cultivation-free
- separate reads or contigs into five groups: Bacteria, Archaeal, Eukaryotic, Viral, and Unknown. 
- generate a fasta file with Euk and unknown contigs for binning


## Overview
Schematic representation of Eukfinder workflows. Eukfinder is a taxonomic classification-based bioinformatics approach to retrieve microbial eukaryotic nuclear and mitochondrial genomes from WGS metagenomic sequencing data. Eukfinder has two different workflows based on the input files, (a) Eukfinder_short using Illumina short reads, it first classifies Illumina reads into 5 distinct taxonomic categories (Archaeal, Bacterial, Viral, Eukaryotic, and Unknown), after assembling the Eukaryotic and Unknown reads together, second round of classification and supervised binning, it will output Eukaryotic nuclear and mitochondrial genomes, and (b) Eukfinder_long using MAG assembled contigs or long-read sequencing data generated by Nanopore or Pacbio platforms. It goes through one round of classification to select Eukaryotic and Unknown contigs, and after supervised binning generates Eukaryotic nuclear and mitochondrial genomes.
![Graphical_abstract](https://user-images.githubusercontent.com/39600837/235653095-c4686819-354c-4252-ad13-960420e46d12.png)

## Publication/Citation
Currently under development


## Requirements


## Installation 

A step-by-step tutorial on installation.

Note: We are working to making DeepMicrobes available on Bioconda, so that this tutorial may be frequently updated.

### 1. Clone this repository

```sh
git clone https://github.com/dzhao2019/eukfindertest.git
```

<br>

### 2. Create a conda environment for DeepMicrobes

Please install [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html) first.


```sh
conda env create -f eukfindertest.yml

# activate it
source activate eukfindertest
```

<br>

### 3. Install other dependencies

(Required) Install PLAST <br>

```sh
wget https://github.com/PLAST-software/plast-library/releases/download/v2.3.2/plastbinary_linux_v2.3.2.tar.gz
tar -zxf plastbinary_linux_v2.3.2.tar.gz
export PATH=/path/to/plastbinary_linux_v2.3.2/bin:$PATH
```
(Required) Install `acc2tax` <br>
https://github.com/richardmleggett/acc2tax

<br>

### 4. Download or build databases
 
  Default reference databases can be downloaded from [Eukfinder Databases](https://perun.biochem.dal.ca/Metagenomics-Scavenger/)
- Plast Database
- Centrifuge Database
- acc2tax Database

 Users can flexibly customize the reference data (see [here](https://github.com/dzhao2019/eukfindertest/wiki/Build-a-customized-reference-database))
 

<!-- USAGE EXAMPLES -->
## Usage

**Eukfinder read_prep**
usage: Eukfinder read_prep [-h] --r1 R1 --r2 R2 -n THREADS -i ILLUMINA_CLIP
                           --hcrop HCROP -l LEADING_TRIM -t TRAIL_TRIM --wsize
                           WSIZE --qscore QSCORE --mlen MLEN --hg HG -o
                           OUT_NAME --cdb CDB

optional arguments:
  -h, --help            show this help message and exit

Required arguments:
  Description

  --r1 R1, --reads-r1 R1    left reads
  
  --r2 R2, --reads-r2 R2    right reads
  
  -n THREADS, --threads THREADS     number of threads
                        
  -i ILLUMINA_CLIP, --illumina-clip ILLUMINA_CLIP     adaptor file
                        
  --hcrop HCROP, --head-crop HCROP    head trim
                        
  -l LEADING_TRIM, --leading-trim LEADING_TRIM    leading trim
                        
  -t TRAIL_TRIM, --trail-trim TRAIL_TRIM    trail trim
                        
  --wsize WSIZE, --window-size WSIZE    sliding window size
                        
  --qscore QSCORE, --quality-score QSCORE     quality score for trimming
                        
  --mlen MLEN, --min-length MLEN    minimum length
                        
  --hg HG, --host-genome HG     host genome to get map out
                        
  -o OUT_NAME, --out_name OUT_NAME    out name
                        
  --cdb CDB, --centrifuge-database CDB    path to centrifuge database
  
**Eukfinder short_seqs**
usage: Eukfinder short_seqs [-h] --r1 R1 --r2 R2 --un UN -o OUT_NAME -n
                            NUMBER_OF_THREADS -z NUMBER_OF_CHUNKS -t
                            TAXONOMY_UPDATE -p PLAST_DATABASE -m PLAST_ID_MAP
                            [-p2 ANCILLARY_PLAST_DATABASE]
                            [-m2 ANCILLARY_PLAST_ID_MAP]
                            [--force-pdb FORCE_PDB] -a ACC2TAX_DATABASE --cdb
                            CDB -e E_VALUE --pid PID --cov COV --max_m MAX_M
                            --mhlen MHLEN --pclass PCLASS --uclass UCLASS

optional arguments:
  -h, --help            show this help message and exit
  -p2 ANCILLARY_PLAST_DATABASE, --ancillary-plast-database ANCILLARY_PLAST_DATABASE
                        path to plast database
  -m2 ANCILLARY_PLAST_ID_MAP, --ancillary-plast-id-map ANCILLARY_PLAST_ID_MAP
                        path to taxonomy map for plast database
  --force-pdb FORCE_PDB, --force_plast_database FORCE_PDB
                        impose the declared plast_database

Required arguments:
  Description

  --r1 R1, --reads-r1 R1
                        left reads
  --r2 R2, --reads-r2 R2
                        right reads
  --un UN, --un-pair-reads UN
                        orphan reads
  -o OUT_NAME, --out_name OUT_NAME
                        out name
  -n NUMBER_OF_THREADS, --number-of-threads NUMBER_OF_THREADS
                        Number of threads
  -z NUMBER_OF_CHUNKS, --number-of-chunks NUMBER_OF_CHUNKS
                        Number of chunks to split a file
  -t TAXONOMY_UPDATE, --taxonomy-update TAXONOMY_UPDATE
                        Set to True the first time the program is used.
                        Otherwise set to False
  -p PLAST_DATABASE, --plast-database PLAST_DATABASE
                        path to plast database
  -m PLAST_ID_MAP, --plast-id-map PLAST_ID_MAP
                        path to taxonomy map for plast database
  -a ACC2TAX_DATABASE, --acc2tax-database ACC2TAX_DATABASE
                        path to acc2tax database
  --cdb CDB, --centrifuge-database CDB
                        path to centrifuge database
  -e E_VALUE, --e-value E_VALUE
                        threshold for plast searches
  --pid PID, --percent_id PID
                        percentage identity for plast searches
  --cov COV, --coverage COV
                        percentage coverage for plast searches
  --max_m MAX_M, --max_memory MAX_M
                        Maximum memomry allocated to carry out an assembly
  --mhlen MHLEN, --min-hit-length MHLEN
                        Maximum memomry allocated to carry out an assembly
  --pclass PCLASS, --p-reads-class PCLASS
                        Classification for pair end reads
  --uclass UCLASS, --u-reads-class UCLASS
                        Classification for un-pair end reads



**Eukfinder long_seqs**

usage: Eukfinder long_seqs [-h] -l LONG_SEQS -o OUT_NAME --mhlen MHLEN --cdb
                           CDB -n NUMBER_OF_THREADS -z NUMBER_OF_CHUNKS -t
                           TAXONOMY_UPDATE -p PLAST_DATABASE -m PLAST_ID_MAP
                           -a ACC2TAX_DATABASE -e E_VALUE --pid PID --cov COV

optional arguments:
  -h, --help            show this help message and exit

Required arguments:
  Description

  -l LONG_SEQS, --long-seqs LONG_SEQS
                        long sequences file
  -o OUT_NAME, --out_name OUT_NAME
                        out name
  --mhlen MHLEN, --min-hit-length MHLEN
                        minimum hit length
  --cdb CDB, --centrifuge-database CDB
                        path to centrifuge database
  -n NUMBER_OF_THREADS, --number-of-threads NUMBER_OF_THREADS
                        Number of threads
  -z NUMBER_OF_CHUNKS, --number-of-chunks NUMBER_OF_CHUNKS
                        Number of chunks to split a file
  -t TAXONOMY_UPDATE, --taxonomy-update TAXONOMY_UPDATE
                        Set to True the first time the program is used.
                        Otherwise set to False
  -p PLAST_DATABASE, --plast-database PLAST_DATABASE
                        path to plast database
  -m PLAST_ID_MAP, --plast-id-map PLAST_ID_MAP
                        path to taxonomy map for plast database
  -a ACC2TAX_DATABASE, --acc2tax-database ACC2TAX_DATABASE
                        path to acc2tax database
  -e E_VALUE, --e-value E_VALUE
                        threshold for plast searches
  --pid PID, --percent_id PID
                        percentage identity for plast searches
  --cov COV, --coverage COV
                        percentage coverage for plast searches

                   
<!-- ROADMAP -->
## Roadmap

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments


<p align="right">(<a href="#readme-top">back to top</a>)</p>
