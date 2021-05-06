# PCGR Dockerfile

This container follows the installation guideline without the need for Docker. At the moment it works only for Linux systems.

## Usage

See [this link](https://github.com/sigven/pcgr#step-5-run-example)

## Databases

Assembly-specific data bundle needed for the PCGR directory

- [grch37 data bundle - 20201123](http://insilico.hpc.uio.no/pcgr/pcgr.databundle.grch37.20201123.tgz) (approx 17Gb)

- [grch38 data bundle - 20201123](http://insilico.hpc.uio.no/pcgr/pcgr.databundle.grch38.20201123.tgz) (approx 18Gb)

In AWS S3: `s3://fast-ngs/cloudos-public-data-ines/`

## Run test

Important information:

- The VCF file must start with ##fileformat= and the value must be one of 'VCFv4.1', 'VCFv4.2' or 'VCFv4.3'
- The VCF file needs to be unannotated
- It's strongly recommend that the input VCF is compressed and indexed using **bgzip and tabix**
- The `--pcgr_dir` recieves the path where the `data` folder is, containing the assembly-specific data folders. Name of folder is hardcoded
- Requires the `--no-docker` option to be passed
- PCGR runs [VCF validation check by EBI’s vcf-validator](https://github.com/EBIvariation/vcf-validator). To skip this add the `--no_vcf_validate` option

    ./pcgr.py --input_vcf HG001-NA12878-pFDA_S1_L001.vcf --pcgr_dir . --output_dir test/  --genome_assembly grch38 --conf conf/pcgr.toml --sample_id Parabricks --no-docker


## Full documentation
[![Documentation Status](https://readthedocs.org/projects/pcgr/badge/?version=latest)](http://pcgr.readthedocs.io/en/latest/?badge=latest)  &nbsp; [![Build Status](https://travis-ci.org/sigven/pcgr.svg?branch=master)](https://travis-ci.org/sigven/pcgr)

https://pcgr.readthedocs.io/en/latest/?badge=latest
