---
id: 4543
name: "dynverse/ti_wishbone"
branch: "master"
tag: "latest"
commit: "bcfaafed092961e54ceba4b91d8c44b93e96ae5f"
version: "a655a4aa55946ffea2d40051276dd3fa"
build_date: "2018-10-29T20:59:12.981Z"
size_mb: 1462
size: 568385567
sif: "https://datasets.datalad.org/shub/dynverse/ti_wishbone/latest/2018-10-29-bcfaafed-a655a4aa/a655a4aa55946ffea2d40051276dd3fa.simg"
url: https://datasets.datalad.org/shub/dynverse/ti_wishbone/latest/2018-10-29-bcfaafed-a655a4aa/
recipe: https://datasets.datalad.org/shub/dynverse/ti_wishbone/latest/2018-10-29-bcfaafed-a655a4aa/Singularity
collection: dynverse/ti_wishbone
---

# dynverse/ti_wishbone:latest

```bash
$ singularity pull shub://dynverse/ti_wishbone:latest
```

## Singularity Recipe

```singularity
#######################################################################################
## DO NOT EDIT THIS FILE! This file was automatically generated from the dockerfile. ##
## Run babelwhale::convert_dockerfile_to_singularityrecipe() to update this file.    ##
#######################################################################################

Bootstrap: shub

From: dynverse/dynwrap:py3.6

%labels
    version 0.1.6

%files
    . /code

%post
    chmod -R 755 '/code'
    pip install git+https://github.com/dynverse/pywishbone --upgrade --upgrade-strategy only-if-needed

%runscript
    exec python /code/run.py
```

## Collection

 - Name: [dynverse/ti_wishbone](https://github.com/dynverse/ti_wishbone)
 - License: None
