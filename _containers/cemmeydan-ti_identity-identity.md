---
id: 8200
name: "cemmeydan/ti_identity"
branch: "master"
tag: "identity"
commit: "b026864114bdb5db34fb334a6a197a4b6cfed3de"
version: "0597ee1fd1fcea0c4ca8b2144fd465fa"
build_date: "2019-04-04T22:58:11.690Z"
size_mb: 2149
size: 824754207
sif: "https://datasets.datalad.org/shub/cemmeydan/ti_identity/identity/2019-04-04-b0268641-0597ee1f/0597ee1fd1fcea0c4ca8b2144fd465fa.simg"
url: https://datasets.datalad.org/shub/cemmeydan/ti_identity/identity/2019-04-04-b0268641-0597ee1f/
recipe: https://datasets.datalad.org/shub/cemmeydan/ti_identity/identity/2019-04-04-b0268641-0597ee1f/Singularity
collection: cemmeydan/ti_identity
---

# cemmeydan/ti_identity:identity

```bash
$ singularity pull shub://cemmeydan/ti_identity:identity
```

## Singularity Recipe

```singularity
########################################################################
##                      DO NOT EDIT THIS FILE!                        ##
##     This file was automatically generated from the dockerfile.     ##
## Run dynmethods/data-raw/convert_dockerfiles.R to update this file. ##
########################################################################

Bootstrap: shub

From: dynverse/dynwrap:r

%labels
    version 0.1.0.1

%files
    . /code

%runscript
    exec /code/run.sh
```

## Collection

 - Name: [cemmeydan/ti_identity](https://github.com/cemmeydan/ti_identity)
 - License: None
