#continuumio/miniconda2:4.7.12
FROM continuumio/miniconda2@sha256:c1c84747f3ed7c4eca1f59c2c2ea954565249853b791b0c8fbf9fc866b715f4f
LABEL description="Docker image containing locuszoom standalone to generate regional plots from genome-wide association studies." \
    version="1.4.0"

RUN apt-get update && apt-get install -y \
    git \
    procps \
    wget \
    zip \
    libxt6 \
    libgomp1

# Install Python and R dependencies through miniconda
COPY environment.yml /
RUN  conda env create -f /environment.yml && conda clean -a 
ENV PATH /opt/conda/envs/locuszoom/bin:$PATH

# Install software dependencies
#  - new_fugue
RUN wget http://www.sph.umich.edu/csg/abecasis/downloads/generic-new_fugue-2010-06-02.tar.gz