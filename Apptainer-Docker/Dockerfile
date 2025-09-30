
FROM condaforge/mambaforge:latest

# Set labels
LABEL maintainer="KIR-Research Computing"
LABEL description="Container image for Panpipes - multimodal single cell pipelines"

# Copy requirements file
COPY requirements.txt /opt/requirements.txt

# Update base system
RUN apt-get update && apt-get install -y \
        build-essential \
        wget \
        git \
    && rm -rf /var/lib/apt/lists/*

# Initialize conda and create environment
RUN . /opt/conda/etc/profile.d/conda.sh && \
    conda create -n pipeline_env python=3.10.16 -y && \
    conda activate pipeline_env && \
    conda install -c conda-forge mamba -y && \
    mamba install -c conda-forge -c bioconda -c defaults -y \
        _libgcc_mutex=0.1 \
        _openmp_mutex=4.5 \
        _r-mutex=1.0.1 \
        binutils_impl_linux-64=2.43 \
        bwidget=1.10.1 \
        bzip2=1.0.8 \
        c-ares=1.34.4 \
        ca-certificates=2025.1.31 \
        cairo=1.18.0 \
        curl=8.12.1 \
        font-ttf-dejavu-sans-mono=2.37 \
        font-ttf-inconsolata=3.000 \
        font-ttf-source-code-pro=2.038 \
        font-ttf-ubuntu=0.83 \
        fontconfig=2.15.0 \
        fonts-conda-ecosystem=1 \
        fonts-conda-forge=1 \
        freetype=2.12.1 \
        fribidi=1.0.10 \
        gcc_impl_linux-64=14.2.0 \
        gettext=0.23.1 \
        gettext-tools=0.23.1 \
        gfortran_impl_linux-64=14.2.0 \
        glpk=5.0 \
        gmp=6.3.0 \
        graphite2=1.3.13 \
        gxx_impl_linux-64=14.2.0 \
        harfbuzz=8.3.0 \
        hdf5=1.14.3 \
        icu=73.2 \
        kernel-headers_linux-64=3.10.0 \
        keyutils=1.6.1 \
        krb5=1.21.3 \
        ld_impl_linux-64=2.43 \
        lerc=4.0.0 \
        libaec=1.1.3 \
        libblas=3.9.0 \
        libcurl=8.12.1 \
        libdeflate=1.23 \
        libedit=3.1.20250104 \
        libev=4.33 \
        libexpat=2.6.4 \
        libffi=3.4.6 \
        libgcc=14.2.0 \
        libgfortran=14.2.0 \
        libgomp=14.2.0 \
        libjpeg-turbo=3.0.0 \
        liblapack=3.9.0 \
        libopenblas=0.3.28 \
        libpng=1.6.46 \
        libtiff=4.7.0 \
        libxml2=2.12.7 \
        libzlib=1.3.1 \
        mkl=2024.2.2 \
        ncurses=6.5 \
        openssl=3.4.1 \
        pandoc=3.6.3 \
        pango=1.52.1 \
        pcre2=10.42 \
        readline=8.2 \
        zlib=1.3.1 \
        r-base=4.3.2 && \
    mamba install -c conda-forge -c bioconda -y \
        r-tidyverse=2.0.0 \
        r-ggplot2=3.5.1 \
        r-dplyr=1.1.4 \
        r-seurat \
        r-data.table=1.16.4 \
        r-hdf5r=1.3.12 \
        r-clustree=0.5.1 \
        r-ggraph=2.2.1 \
        r-ggrepel=0.9.6 \
        r-cowplot=1.1.3 \
        r-optparse=1.7.5 && \
    pip install --no-cache-dir -r /opt/requirements.txt && \
    conda clean -afy && \
    rm -rf /root/.cache/pip

# Set environment variables
ENV PATH=/opt/conda/envs/pipeline_env/bin:$PATH \
    CONDA_DEFAULT_ENV=pipeline_env \
    CONDA_PREFIX=/opt/conda/envs/pipeline_env

# Set working directory
WORKDIR /data

# Default command
CMD ["/bin/bash"]
