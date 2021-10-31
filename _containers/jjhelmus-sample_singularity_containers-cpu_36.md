---
id: 7654
name: "jjhelmus/sample_singularity_containers"
branch: "master"
tag: "cpu_36"
commit: "59f17a08f90c63313298f371526ae12466275d18"
version: "2790f5bd2ac4698923b0fbccfd9634e6"
build_date: "2019-03-27T08:48:37.128Z"
size_mb: 5555
size: 2402934815
sif: "https://datasets.datalad.org/shub/jjhelmus/sample_singularity_containers/cpu_36/2019-03-27-59f17a08-2790f5bd/2790f5bd2ac4698923b0fbccfd9634e6.simg"
url: https://datasets.datalad.org/shub/jjhelmus/sample_singularity_containers/cpu_36/2019-03-27-59f17a08-2790f5bd/
recipe: https://datasets.datalad.org/shub/jjhelmus/sample_singularity_containers/cpu_36/2019-03-27-59f17a08-2790f5bd/Singularity
collection: jjhelmus/sample_singularity_containers
---

# jjhelmus/sample_singularity_containers:cpu_36

```bash
$ singularity pull shub://jjhelmus/sample_singularity_containers:cpu_36
```

## Singularity Recipe

```singularity
Bootstrap: docker

From: ubuntu:16.04

%environment
    export LANG=C.UTF-8
    export LC_ALL=C.UTF-8

%files
    sitecustomize.py /opt

%post
    . /environment

    # install necessary system libraries and utilities
    apt-get update --fix-missing
    apt-get install -y wget bzip2 libglib2.0-0 libxext6 libsm6 libxrender1

    # install miniconda
    mkdir -p /opt
    MINICONDA_URL=https://repo.anaconda.com/miniconda/Miniconda3-4.5.12-Linux-x86_64.sh
    wget --quiet $MINICONDA_URL -O /opt/miniconda.sh
    /bin/bash /opt/miniconda.sh -b -p /opt/conda
    rm /opt/miniconda.sh
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh
    echo ". /etc/profile.d/conda.sh" >> /etc/bash.conda
    echo "conda activate base" >> /etc/bash.conda

    # activate the base environment
    . /opt/conda/etc/profile.d/conda.sh

    # install anaconda
    conda install -y -q python=3.6 anaconda=2018.12

    # update conda
    conda install -y -q conda=4.6 anaconda=custom

    # install selected packages
    conda install -y -q -c defaults -c conda-forge -c engility \
        mpi4py \
        pydotplus \
        altair \
        hdbscan \
        datreant=1.0 \
        pymatgen \
        tpot \
        seaborn \
        nb_conda \
        libiconv \
        ipyparallel \
        mkl=2019.1=144 \
        libgcc-ng=8 \
        blas=*=mkl \
        tensorflow \
        keras \
        caffe 

    # mv sitecustomize.py file
    SP_DIR=`/opt/conda/bin/python -c "import site; print(site.getsitepackages()[0])"`
    mv /opt/sitecustomize.py $SP_DIR

%runscript
    /bin/bash --noprofile --rcfile /etc/bash.conda
```

## Collection

 - Name: [jjhelmus/sample_singularity_containers](https://github.com/jjhelmus/sample_singularity_containers)
 - License: None
