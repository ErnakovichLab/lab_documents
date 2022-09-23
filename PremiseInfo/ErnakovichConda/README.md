# Shared Conda Environments
## Impetus
- when premise went down in September 2022, the `anaconda/colsa` package information was lost, which meant that for a temporary time we'd need to have locally installed conda. Rather than have every member of the lab install conda, Hannah Holland-Moritz created a shared lab conda environment in the `/mnt/home/ernakovich/shared/software` directory. 
- This conda installation can be a temporary location for packages that are in anaconda/colsa that we need to use in the short term
- For the long term, it makes sense to install packages here that dont' require being installed globally. Generally we'd prefer to rely on the global installation because we won't have to maintain it ourselves, but for some use cases, it might be useful to have a unified lab version separate from the anaconda/colsa verison.

## How to use

To use the conda environment either on a login node or in a slurm script in such a way that it doesn't interfere with the  anaconda/colsa module:
```bash
module purge
source /mnt/home/ernakovich/shared/software/miniconda3/bin/activate # activates base environment
conda activate /mnt/home/ernakovich/shared/software/miniconda3/envs/<conda environment> # activates specific environment
```

*Note: Untested whether or not activating this environment and then trying to activate an anacodan/colsa environment subsequently will cause conflicts. I think it's likely to do that, so best practice would to be to use a new shell/slurm script or log out and back in before enabling the anaconda/colsa module. The reverse (using anaconda/colsa, purging the module and then using the Ernakovich conda) shouldn't be an issue.*

## Currently available environments

### Amplicon analyses
| Environment | Location | Notes | 
| ----------- | -------- | ----- |
| dada2_ernakovich |`/mnt/home/ernakovich/shared/software/miniconda3/envs/dada2_ernakovich`| Contains packages necessary for running the [dada2_ernakovich pipeline](https://github.com/ErnakovichLab/dada2_ernakovichlab) including dada2, cutadapt, and several other R packages |

### Metagenomic analyses
| Environment | Location | Notes | 
| ----------- | -------- | ----- |
| fastqc |`/mnt/home/ernakovich/shared/software/miniconda3/envs/fastqc`| [Fastqc](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/) is a tool for assesing the quality of fastq files. |
| multiqc |`/mnt/home/ernakovich/shared/software/miniconda3/envs/multiqc`| [Multiqc](https://multiqc.info) is a tool for making summaries of outputs from a number of genomic tools. |
| cutadapt |`/mnt/home/ernakovich/shared/software/miniconda3/envs/cutadapt`| [Cutadapt](https://cutadapt.readthedocs.io/en/stable/) can be used to remove adapters from fastq files. |
| bbtools |`/mnt/home/ernakovich/shared/software/miniconda3/envs/bbtools`| [BBtools](https://jgi.doe.gov/data-and-tools/software-tools/bbtools/) contain a number of sequence-handling tools, most notably, BBduk which is used for cleaning and filtering fastq data. |
| pf |`/mnt/home/ernakovich/shared/software/miniconda3/envs/pf`| Environment contains [phyloflash](https://github.com/HRGV/phyloFlash), a tool for extracting and summarizing the 16/18S SSU fragments in metagenomic data. Currently not fully functional as databases need to be installed. |

### Other
| Environment | Location | Notes |
| ----------- | -------- | ----- |
| XCT_FCN |`/mnt/home/ernakovich/shared/software/miniconda3/envs/XCT_FCN`| [XCT_FCN](https://github.com/daripp/XCT_FCN) is an image deep-learning workflow for segmenting soil and plant X-ray CT images. Hasn't been tested yet, use at your own risk. |

## Installation Instructions and Notes
Notes from the installation instructions can be found in the text files in this repository folder.