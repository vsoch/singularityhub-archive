---
id: 4479
name: "dynverse/ti_mpath"
branch: "master"
tag: "latest"
commit: "0bb89066cc4896bd8c394204d519d9b9549fa169"
version: "afb9be4868eeb7d1e5428292c0a4f6a8"
build_date: "2018-10-29T20:59:12.628Z"
size_mb: 2123
size: 832778271
sif: "https://datasets.datalad.org/shub/dynverse/ti_mpath/latest/2018-10-29-0bb89066-afb9be48/afb9be4868eeb7d1e5428292c0a4f6a8.simg"
url: https://datasets.datalad.org/shub/dynverse/ti_mpath/latest/2018-10-29-0bb89066-afb9be48/
recipe: https://datasets.datalad.org/shub/dynverse/ti_mpath/latest/2018-10-29-0bb89066-afb9be48/Singularity
collection: dynverse/ti_mpath
---

# dynverse/ti_mpath:latest

```bash
$ singularity pull shub://dynverse/ti_mpath:latest
```

## Singularity Recipe

```singularity
#######################################################################################
## DO NOT EDIT THIS FILE! This file was automatically generated from the dockerfile. ##
## Run babelwhale::convert_dockerfile_to_singularityrecipe() to update this file.    ##
#######################################################################################

Bootstrap: shub

From: dynverse/dynwrap:r

%labels
    version 0.1.5

%files
    . /code

%post
    chmod -R 755 '/code'
    R -e 'devtools::install_github("dynverse/Mpath")'

%runscript
    exec Rscript /code/run.R
```

## Collection

 - Name: [dynverse/ti_mpath](https://github.com/dynverse/ti_mpath)
 - License: None
