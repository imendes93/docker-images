FROM continuumio/miniconda3@sha256:456e3196bf3ffb13fee7c9216db4b18b5e6f4d37090b31df3e0309926e98cfe2

# Metadata
LABEL software="pcgr" \
      software.version="0.9.1" \
      about.home="https://github.com/sigven/pcgr" \
      about.summary="Personal Cancer Genome Reporter (PCGR) - variant interpretation for precision cancer medicine" \
      about.documentation="https://pcgr.readthedocs.io/en/latest/?badge=latest" \
      about.license="https://github.com/sigven/pcgr/blob/master/LICENSE"


RUN apt-get update \
  && apt-get install zip procps -y

# Install PCGR Python depency
RUN pip install toml

# Install PCGR from conda
RUN conda install -c conda-forge -c bioconda -c pcgr pcgr=0.9.1
ENV PATH /opt/conda/envs/base/bin:$PATH

# Install PCGR from source - Git
#RUN wget https://github.com/sigven/pcgr/archive/refs/tags/v0.9.1.zip
#RUN unzip v0.9.1.zip && rm v0.9.1.zip

# Install PCGR dependencies - conda
#RUN conda install conda-build
#RUN conda build -c conda-forge -c bioconda -c pcgr -c defaults pcgr-0.9.1/install_no_docker/conda_pkg/pcgr
#RUN conda install --use-local -c conda-forge -c bioconda -c pcgr -c defaults pcgr
