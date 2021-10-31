---
id: 3128
name: "ReproNim/ohbm2018-training"
branch: "master"
tag: "fsl"
commit: "2026209cba2a8ecbcc37b524894c5b40bb21349d"
version: "4887b3cd8e71a317cb153a3949772fe1"
build_date: "2018-10-17T23:52:16.100Z"
size_mb: 856
size: 362700831
sif: "https://datasets.datalad.org/shub/ReproNim/ohbm2018-training/fsl/2018-10-17-2026209c-4887b3cd/4887b3cd8e71a317cb153a3949772fe1.simg"
url: https://datasets.datalad.org/shub/ReproNim/ohbm2018-training/fsl/2018-10-17-2026209c-4887b3cd/
recipe: https://datasets.datalad.org/shub/ReproNim/ohbm2018-training/fsl/2018-10-17-2026209c-4887b3cd/Singularity
collection: ReproNim/ohbm2018-training
---

# ReproNim/ohbm2018-training:fsl

```bash
$ singularity pull shub://ReproNim/ohbm2018-training:fsl
```

## Singularity Recipe

```singularity
# Generated by Neurodocker version 0.4.0rc1
# Timestamp: 2018-06-10 03:00:33 UTC
# 
# Thank you for using Neurodocker. If you discover any issues
# or ways to improve this software, please submit an issue or
# pull request on our GitHub repository:
# 
#     https://github.com/kaczmarj/neurodocker

Bootstrap: docker
From: neurodebian:stretch-non-free

%post
export ND_ENTRYPOINT="/neurodocker/startup.sh"
apt-get update -qq
apt-get install -y -q --no-install-recommends \
    apt-utils \
    bzip2 \
    ca-certificates \
    curl \
    locales \
    unzip
apt-get clean
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen
dpkg-reconfigure --frontend=noninteractive locales
update-locale LANG="en_US.UTF-8"
chmod 777 /opt && chmod a+s /opt
mkdir -p /neurodocker
if [ ! -f "$ND_ENTRYPOINT" ]; then
  echo '#!/usr/bin/env bash' >> "$ND_ENTRYPOINT"
  echo 'set -e' >> "$ND_ENTRYPOINT"
  echo 'if [ -n "$1" ]; then "$@"; else /usr/bin/env bash; fi' >> "$ND_ENTRYPOINT";
fi
chmod -R 777 /neurodocker && chmod a+s /neurodocker

apt-get update -qq
apt-get install -y -q --no-install-recommends \
    fsl-5.0-core \
    fsl-mni152-templates
apt-get clean
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

apt-get update -qq
apt-get install -y -q --no-install-recommends \
    make \
    gcc \
    sqlite3 \
    libsqlite3-dev \
    python3-dev \
    libc6-dev \
    python3-pip \
    python3-setuptools \
    python3-wheel
apt-get clean
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

pip3 install --system reprozip reprounzip

sed -i '$isource /etc/fsl/5.0/fsl.sh' $ND_ENTRYPOINT

echo '{
\n  "pkg_manager": "apt",
\n  "instructions": [
\n    [
\n      "base",
\n      "neurodebian:stretch-non-free"
\n    ],
\n    [
\n      "_header",
\n      {
\n        "version": "generic",
\n        "method": "custom"
\n      }
\n    ],
\n    [
\n      "install",
\n      [
\n        "fsl-5.0-core",
\n        "fsl-mni152-templates"
\n      ]
\n    ],
\n    [
\n      "install",
\n      [
\n        "make",
\n        "gcc",
\n        "sqlite3",
\n        "libsqlite3-dev",
\n        "python3-dev",
\n        "libc6-dev",
\n        "python3-pip",
\n        "python3-setuptools",
\n        "python3-wheel"
\n      ]
\n    ],
\n    [
\n      "run",
\n      "pip3 install --system reprozip reprounzip"
\n    ],
\n    [
\n      "add_to_entrypoint",
\n      "source /etc/fsl/5.0/fsl.sh"
\n    ]
\n  ]
\n}' > /neurodocker/neurodocker_specs.json

%environment
export LANG="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"
export ND_ENTRYPOINT="/neurodocker/startup.sh"

%runscript
/neurodocker/startup.sh "$@"
```

## Collection

 - Name: [ReproNim/ohbm2018-training](https://github.com/ReproNim/ohbm2018-training)
 - License: None
