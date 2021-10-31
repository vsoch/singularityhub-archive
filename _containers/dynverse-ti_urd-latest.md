---
id: 4538
name: "dynverse/ti_urd"
branch: "master"
tag: "latest"
commit: "3958fd801201e31ccefc7885c3e299c29ebd218d"
version: "082f9809acdfb59b14bd4bd5f8129f90"
build_date: "2019-01-16T07:21:13.021Z"
size_mb: 2151
size: 835731487
sif: "https://datasets.datalad.org/shub/dynverse/ti_urd/latest/2019-01-16-3958fd80-082f9809/082f9809acdfb59b14bd4bd5f8129f90.simg"
url: https://datasets.datalad.org/shub/dynverse/ti_urd/latest/2019-01-16-3958fd80-082f9809/
recipe: https://datasets.datalad.org/shub/dynverse/ti_urd/latest/2019-01-16-3958fd80-082f9809/Singularity
collection: dynverse/ti_urd
---

# dynverse/ti_urd:latest

```bash
$ singularity pull shub://dynverse/ti_urd:latest
```

## Singularity Recipe

```singularity
#######################################################################################
## DO NOT EDIT THIS FILE! This file was automatically generated from the dockerfile. ##
## Run babelwhale::convert_dockerfile_to_singularityrecipe() to update this file.    ##
#######################################################################################

Bootstrap: shub

From: dynverse/dynwrap:bioc

%labels
    version 0.1.4.1

%files
    . /code

%post
    chmod -R 755 '/code'
    apt-get update && apt-get install -y libudunits2-dev
    R -e 'devtools::install_github("farrellja/URD")'

%runscript
    exec Rscript /code/run.R
```

## Collection

 - Name: [dynverse/ti_urd](https://github.com/dynverse/ti_urd)
 - License: None
