---
id: 8867
name: "ReproNim/containers"
branch: "master"
tag: "bids-antscorticalthickness--2.2.0-1"
commit: "697f419c659db6088f9fb810afdf14b3cf0d3ac2"
version: "f23ae1b4684696696de37d1d6878e89f"
build_date: "2021-03-19T23:51:53.847Z"
size_mb: 1036
size: 359763999
sif: "https://datasets.datalad.org/shub/ReproNim/containers/bids-antscorticalthickness--2.2.0-1/2021-03-19-697f419c-f23ae1b4/f23ae1b4684696696de37d1d6878e89f.simg"
url: https://datasets.datalad.org/shub/ReproNim/containers/bids-antscorticalthickness--2.2.0-1/2021-03-19-697f419c-f23ae1b4/
recipe: https://datasets.datalad.org/shub/ReproNim/containers/bids-antscorticalthickness--2.2.0-1/2021-03-19-697f419c-f23ae1b4/Singularity
collection: ReproNim/containers
---

# ReproNim/containers:bids-antscorticalthickness--2.2.0-1

```bash
$ singularity pull shub://ReproNim/containers:bids-antscorticalthickness--2.2.0-1
```

## Singularity Recipe

```singularity
#
# Automagically prepared for ReproNim/containers distribution.
# See http://github.com/ReproNim/containers for more info
#
Bootstrap: docker
From: bids/antscorticalthickness:v2.2.0-1

%post

# Create commonly present root directories to avoid need in overlays not supported
# on older systems
mkdir -p /ihome /data /data2 /zfs /isi /dartfs /dartfs-hpc

%environment
export LANG="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"

# TODO: Take advantage of the fact that it is a bids-app somehow?
```

## Collection

 - Name: [ReproNim/containers](https://github.com/ReproNim/containers)
 - License: [Apache License 2.0](https://api.github.com/licenses/apache-2.0)
