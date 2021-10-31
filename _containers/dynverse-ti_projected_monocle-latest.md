---
id: 4498
name: "dynverse/ti_projected_monocle"
branch: "master"
tag: "latest"
commit: "44389e0096ce9d367b5379919995f04c7afaa605"
version: "16a849cba5fa8eb3fdb1056720e5fbec"
build_date: "2019-01-16T07:21:12.893Z"
size_mb: 2200
size: 867426335
sif: "https://datasets.datalad.org/shub/dynverse/ti_projected_monocle/latest/2019-01-16-44389e00-16a849cb/16a849cba5fa8eb3fdb1056720e5fbec.simg"
url: https://datasets.datalad.org/shub/dynverse/ti_projected_monocle/latest/2019-01-16-44389e00-16a849cb/
recipe: https://datasets.datalad.org/shub/dynverse/ti_projected_monocle/latest/2019-01-16-44389e00-16a849cb/Singularity
collection: dynverse/ti_projected_monocle
---

# dynverse/ti_projected_monocle:latest

```bash
$ singularity pull shub://dynverse/ti_projected_monocle:latest
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
    version 0.1.5

%files
    . /code

%post
    chmod -R 755 '/code'
    R -e 'devtools::install_cran("monocle")'

%runscript
    exec Rscript /code/run.R
```

## Collection

 - Name: [dynverse/ti_projected_monocle](https://github.com/dynverse/ti_projected_monocle)
 - License: None
