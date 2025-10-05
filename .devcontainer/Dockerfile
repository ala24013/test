FROM mcr.microsoft.com/devcontainers/python:3.11-bullseye

# Install system dependencies for PyCBC
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    build-essential \
    pkg-config \
    libfftw3-dev \
    libgsl-dev \
    libhdf5-dev \
    liblapack-dev \
    libopenmpi-dev \
    git \
    wget \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Upgrade pip and install Python build tools
RUN pip install --no-cache-dir --upgrade pip setuptools wheel

# Install NumPy and Cython first (required for PyCBC)
RUN pip install --no-cache-dir numpy cython

# Install PyCBC
RUN pip install --no-cache-dir pycbc

# Install additional useful packages for gravitational wave analysis
RUN pip install --no-cache-dir \
    matplotlib \
    scipy \
    h5py \
    jupyter \
    ipykernel \
    pandas \
    black

# Verify installation
RUN python -c "import pycbc; print(f'PyCBC {pycbc.__version__} installed successfully')"
