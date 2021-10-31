---
id: 4460
name: "dynverse/ti_forks"
branch: "master"
tag: "latest"
commit: "828997d2d94865d16f52e394c473f07f5e7080ee"
version: "d515642addacac4a78c830e96bc0fb2d"
build_date: "2018-10-29T20:59:12.528Z"
size_mb: 1412
size: 544526367
sif: "https://datasets.datalad.org/shub/dynverse/ti_forks/latest/2018-10-29-828997d2-d515642a/d515642addacac4a78c830e96bc0fb2d.simg"
url: https://datasets.datalad.org/shub/dynverse/ti_forks/latest/2018-10-29-828997d2-d515642a/
recipe: https://datasets.datalad.org/shub/dynverse/ti_forks/latest/2018-10-29-828997d2-d515642a/Singularity
collection: dynverse/ti_forks
---

# dynverse/ti_forks:latest

```bash
$ singularity pull shub://dynverse/ti_forks:latest
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
    version 0.1.4

%files
    . /code

%post
    chmod -R 755 '/code'
    pip install seaborn hdbscan
    git clone https://github.com/macsharma/FORKS.git

%runscript
    exec python /code/run.py
```

## Collection

 - Name: [dynverse/ti_forks](https://github.com/dynverse/ti_forks)
 - License: None
