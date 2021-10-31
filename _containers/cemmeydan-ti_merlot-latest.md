---
id: 8207
name: "cemmeydan/ti_merlot"
branch: "master"
tag: "latest"
commit: "8e1568ac6d1992faa723a01e5c991ca7ef6eafc3"
version: "add7a2ec945ba53fbcee024ce339c7dc"
build_date: "2019-04-04T22:58:11.761Z"
size_mb: 2783
size: 1017856031
sif: "https://datasets.datalad.org/shub/cemmeydan/ti_merlot/latest/2019-04-04-8e1568ac-add7a2ec/add7a2ec945ba53fbcee024ce339c7dc.simg"
url: https://datasets.datalad.org/shub/cemmeydan/ti_merlot/latest/2019-04-04-8e1568ac-add7a2ec/
recipe: https://datasets.datalad.org/shub/cemmeydan/ti_merlot/latest/2019-04-04-8e1568ac-add7a2ec/Singularity
collection: cemmeydan/ti_merlot
---

# cemmeydan/ti_merlot:latest

```bash
$ singularity pull shub://cemmeydan/ti_merlot:latest
```

## Singularity Recipe

```singularity
#######################################################################################
## DO NOT EDIT THIS FILE! This file was automatically generated from the dockerfile. ##
## Run dynwrap:::.container_dockerfile_to_singularityrecipe() to update this file.   ##
#######################################################################################

Bootstrap: shub

From: dynverse/dynwrap:bioc

%labels
    version 0.1.0

%post
    R -e 'devtools::install_cran("destiny")'
    apt-get update && apt-get install -y libcgal-dev libglu1-mesa-dev libglu1-mesa-dev
    apt-get install -y python3 python3-tk python3-pip
    apt-get install -y python3-scipy python3-numpy python3-pandas
    pip3 install cython
    pip3 install git+https://github.com/soedinglab/csgraph_mod
    apt-get -y install libudunits2-dev
    Rscript -e 'devtools::install_cran("udunits2", configure.args =  c(udunits2 = "--with-udunits2-include=/usr/include/udunits2"))'
    R -e "devtools::install_github('soedinglab/merlot')"

%files
    . /code

%runscript
    exec Rscript /code/run.R
```

## Collection

 - Name: [cemmeydan/ti_merlot](https://github.com/cemmeydan/ti_merlot)
 - License: None
