# Making a custom conda environment for Jupyter Notebook Server

Author: Chuner Guo  
Date: 2024-12-03

How I created a conda virtual environment to install the packages I want and run interactive python-based analysis in Jupyter Notebook on Stanford's SCG cluster (part of the **[Stanford Research Computing Center](https://srcc.stanford.edu)**).


## Use conda to create new virtual environment
We will start by creating a new environment using conda named `custom_jupyter_env`. We will use python version 3.12.
```
conda create -n custom_jupyter_env python=3.12
```

## Activate environment
```
conda activate custom_jupyter_env
which python
# ~/.conda/envs/custom_jupyter_env/bin/python
python -V
# Python 3.12.7
```

## Install ipykernel
```
conda install ipykernel
```

## Install other required packages
Whatever your heart desires. For example **[scanpy](https://scanpy.readthedocs.io/en/stable/installation.html)** and **[scvi-tools](https://docs.scvi-tools.org/en/stable/installation.html)**:
```
conda install -c conda-forge scanpy python-igraph leidenalg 
pip install -U scvi-tools
```

## Register the virtual env as a jupyter kernel
```
python -m ipykernel install --user --name=custom_jupyter_env
# Installed kernelspec custom_jupyter_env in /home/ceguo/.local/share/jupyter/kernels/custom_jupyter_env
```
The kernel is now ready to use with SCG's Jupyter Notebook Server.

## Sharing virtual environment
Start by exporting the environment:
```
conda env export > custom_jupyter_env.yml
```
This environment can then be imported via:
```
conda env create -f custom_jupyter_env.yml
```