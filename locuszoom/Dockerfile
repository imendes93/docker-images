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
    libgomp1 \
    zlib1g-dev \
    build-essential

# Install Python and R dependencies through miniconda
COPY environment.yml ./
RUN  conda env create -f /environment.yml && \
     conda clean -a
ENV PATH /opt/conda/envs/locuszoom/bin:$PATH

# Install software dependencies
#  - new_fugue
RUN wget http://www.sph.umich.edu/csg/abecasis/downloads/generic-new_fugue-2010-06-02.tar.gz && \
    tar -xf generic-new_fugue-2010-06-02.tar.gz && \
    cd generic-new_fugue && \
    make install
RUN rm generic-new_fugue-2010-06-02.tar.gz

# - PLINK
RUN wget https://zzz.bwh.harvard.edu/plink/dist/plink-1.07-x86_64.zip && \
    unzip plink-1.07-x86_64.zip && \
    rm plink-1.07-x86_64.zip
ENV PATH /plink-1.07-x86_64:$PATH

# - tabix
RUN wget https://sourceforge.net/projects/samtools/files/tabix/tabix-0.2.6.tar.bz2 && \
    tar -xf tabix-0.2.6.tar.bz2 && \
    cd tabix-0.2.6 && \
    make
RUN rm tabix-0.2.6.tar.bz2
ENV PATH /tabix-0.2.6:$PATH

# Install locuszoom
RUN wget https://statgen.sph.umich.edu/locuszoom/download/locuszoom_1.4_srconly.tgz && \
    tar -xf locuszoom_1.4_srconly.tgz
RUN rm locuszoom_1.4_srconly.tgz
ENV PATH /locuszoom/bin:$PATH