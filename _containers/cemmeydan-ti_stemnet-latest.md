---
id: 8179
name: "cemmeydan/ti_stemnet"
branch: "master"
tag: "latest"
commit: "6240ba4470a3166df7bd8215f3e7d937a2156f3e"
version: "9d70526b406bfc92a510920650174e2d"
build_date: "2019-04-04T22:58:11.930Z"
size_mb: 2257
size: 929124383
sif: "https://datasets.datalad.org/shub/cemmeydan/ti_stemnet/latest/2019-04-04-6240ba44-9d70526b/9d70526b406bfc92a510920650174e2d.simg"
url: https://datasets.datalad.org/shub/cemmeydan/ti_stemnet/latest/2019-04-04-6240ba44-9d70526b/
recipe: https://datasets.datalad.org/shub/cemmeydan/ti_stemnet/latest/2019-04-04-6240ba44-9d70526b/Singularity
collection: cemmeydan/ti_stemnet
---

# cemmeydan/ti_stemnet:latest

```bash
$ singularity pull shub://cemmeydan/ti_stemnet:latest
```

## Singularity Recipe

```singularity
#######################################################################################
## DO NOT EDIT THIS FILE! This file was automatically generated from the dockerfile. ##
## Run dynwrap:::.container_dockerfile_to_singularityrecipe() to update this file.   ##
#######################################################################################

Bootstrap: shub

From: dynverse/dynwrap:r

%labels
    version 0.1.0

%post
    apt-get install -y libgsl-dev
    R -e 'devtools::install_git("https://git.embl.de/velten/STEMNET/")'

%files
    . /code

%runscript
    exec Rscript /code/run.R
```

## Collection

 - Name: [cemmeydan/ti_stemnet](https://github.com/cemmeydan/ti_stemnet)
 - License: None
