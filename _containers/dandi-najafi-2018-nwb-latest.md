---
id: 10341
name: "dandi/najafi-2018-nwb"
branch: "master"
tag: "latest"
commit: "50095382b51e1094c497153680f28132312fd789"
version: "a37f0c27ba0ac79d577cb71cb705659b"
build_date: "2019-08-13T22:27:28.216Z"
size_mb: 2367.0
size: 737775647
sif: "https://datasets.datalad.org/shub/dandi/najafi-2018-nwb/latest/2019-08-13-50095382-a37f0c27/a37f0c27ba0ac79d577cb71cb705659b.sif"
url: https://datasets.datalad.org/shub/dandi/najafi-2018-nwb/latest/2019-08-13-50095382-a37f0c27/
recipe: https://datasets.datalad.org/shub/dandi/najafi-2018-nwb/latest/2019-08-13-50095382-a37f0c27/Singularity
collection: dandi/najafi-2018-nwb
---

# dandi/najafi-2018-nwb:latest

```bash
$ singularity pull shub://dandi/najafi-2018-nwb:latest
```

## Singularity Recipe

```singularity
# Generated by Neurodocker version 0.5.0-3-gd983e72
# Timestamp: 2019-08-13 17:15:17 UTC
# 
# Thank you for using Neurodocker. If you discover any issues
# or ways to improve this software, please submit an issue or
# pull request on our GitHub repository:
# 
#     https://github.com/kaczmarj/neurodocker

Bootstrap: docker
From: neurodebian:buster

%post
apt-get update -qq
apt-get install -y -q --no-install-recommends neurodebian-freeze
nd_freeze  20190724
apt-get clean
rm -rf /var/lib/apt/lists/*

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
rm -rf /var/lib/apt/lists/*
sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen
dpkg-reconfigure --frontend=noninteractive locales
update-locale LANG="en_US.UTF-8"
chmod 777 /opt && chmod a+s /opt
mkdir -p /neurodocker
if [ ! -f "$ND_ENTRYPOINT" ]; then
  echo '#!/usr/bin/env bash' >> "$ND_ENTRYPOINT"
  echo 'set -e' >> "$ND_ENTRYPOINT"
  echo 'export USER="${USER:=`whoami`}"' >> "$ND_ENTRYPOINT"
  echo 'if [ -n "$1" ]; then "$@"; else /usr/bin/env bash; fi' >> "$ND_ENTRYPOINT";
fi
chmod -R 777 /neurodocker && chmod a+s /neurodocker

apt-get update -qq
apt-get install -y -q --no-install-recommends \
    vim \
    wget \
    strace \
    time \
    ncdu \
    gnupg \
    curl \
    procps \
    pigz \
    virtualenv \
    python-pytest \
    dcmtk \
    python-pip \
    python-wheel \
    python-setuptools
apt-get clean
rm -rf /var/lib/apt/lists/*

test "$(getent passwd neuro)" || useradd --no-user-group --create-home --shell /bin/bash neuro
su - neuro

export PATH="/opt/miniconda-latest/bin:$PATH"
echo "Downloading Miniconda installer ..."
conda_installer="/tmp/miniconda.sh"
curl -fsSL --retry 5 -o "$conda_installer" https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash "$conda_installer" -b -p /opt/miniconda-latest
rm -f "$conda_installer"
conda update -yq -nbase conda
conda config --system --prepend channels conda-forge
conda config --system --set auto_update_conda false
conda config --system --set show_channel_urls true
sync && conda clean --all && sync
conda create -y -q --name nwb
conda install -y -q --name nwb \
    "python=3.7" \
    "pynwb" \
    "datalad" \
    "jupyter" \
    "jupyterlab" \
    "jupyter_contrib_nbextensions" \
    "matplotlib" \
    "seaborn" \
    "tqdm"
sync && conda clean --all && sync
bash -c "source activate nwb
  pip install --no-cache-dir  \
      "duecredit" \
      "python-dateutil""
rm -rf ~/.cache/pip/*
sync
sed -i '$isource activate nwb' $ND_ENTRYPOINT


mkdir -p ~/.jupyter && echo c.NotebookApp.ip = \"0.0.0.0\" > ~/.jupyter/jupyter_notebook_config.py

cd /home/neuro

echo '{
\n  "pkg_manager": "apt",
\n  "instructions": [
\n    [
\n      "base",
\n      "neurodebian:buster"
\n    ],
\n    [
\n      "ndfreeze",
\n      {
\n        "date": "20190724"
\n      }
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
\n        "vim",
\n        "wget",
\n        "strace",
\n        "time",
\n        "ncdu",
\n        "gnupg",
\n        "curl",
\n        "procps",
\n        "pigz",
\n        "virtualenv",
\n        "python-pytest",
\n        "dcmtk",
\n        "python-pip",
\n        "python-wheel",
\n        "python-setuptools"
\n      ]
\n    ],
\n    [
\n      "user",
\n      "neuro"
\n    ],
\n    [
\n      "miniconda",
\n      {
\n        "conda_install": [
\n          "python=3.7",
\n          "pynwb",
\n          "datalad",
\n          "jupyter",
\n          "jupyterlab",
\n          "jupyter_contrib_nbextensions",
\n          "matplotlib",
\n          "seaborn",
\n          "tqdm"
\n        ],
\n        "pip_install": [
\n          "duecredit",
\n          "python-dateutil"
\n        ],
\n        "create_env": "nwb",
\n        "activate": true
\n      }
\n    ],
\n    [
\n      "run",
\n      "mkdir -p ~/.jupyter && echo c.NotebookApp.ip = \\\"0.0.0.0\\\" > ~/.jupyter/jupyter_notebook_config.py"
\n    ],
\n    [
\n      "workdir",
\n      "/home/neuro"
\n    ]
\n  ]
\n}' > /neurodocker/neurodocker_specs.json

%environment
export LANG="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"
export ND_ENTRYPOINT="/neurodocker/startup.sh"
export CONDA_DIR="/opt/miniconda-latest"
export PATH="/opt/miniconda-latest/bin:$PATH"

%runscript
/neurodocker/startup.sh "$@"
```

## Collection

 - Name: [dandi/najafi-2018-nwb](https://github.com/dandi/najafi-2018-nwb)
 - License: [MIT License](https://api.github.com/licenses/mit)
