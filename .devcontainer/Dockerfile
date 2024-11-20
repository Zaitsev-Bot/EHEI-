# Use Ubuntu 20.04 as the base image
FROM mcr.microsoft.com/vscode/devcontainers/base:0-focal

# Install dependencies for building Octave
RUN apt-get update && apt-get install -y \
    build-essential \
    gfortran \
    libblas-dev \
    liblapack-dev \
    libpcre3-dev \
    libreadline-dev \
    libarpack2-dev \
    libcurl4-gnutls-dev \
    libfftw3-dev \
    libfltk1.3-dev \
    libfreetype6-dev \
    libgl2ps-dev \
    libglpk-dev \
    libhdf5-dev \
    libncurses5-dev \
    libopenblas-dev \
    libqhull-dev \
    libqrupdate-dev \
    libsuitesparse-dev \
    libxft-dev \
    libxrandr-dev \
    wget && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Set the default working directory
WORKDIR /workspace

# Copy and extract Octave source code
COPY ./octave-8.3.0.tar.gz /workspace/
RUN tar -xzf /workspace/octave-8.3.0.tar.gz

# Build and install Octave
RUN cd /workspace/octave-8.3.0 && \
    ./configure && \
    make -j$(nproc) && \
    make install && \
    rm -rf /workspace/octave-8.3.0

# Add Octave to the PATH
ENV PATH="/usr/local/bin:${PATH}"
