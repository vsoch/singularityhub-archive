---
id: 3405
name: "gearslaboratory/gears-singularity"
branch: "master"
tag: "gears-lidr"
commit: "402c63481bc49a8a88ed42ed482a36ac3773c36d"
version: "f736dbe780a767209ebd6435830eb1c3"
build_date: "2019-02-19T17:41:52.639Z"
size_mb: 3650
size: 1191559199
sif: "https://datasets.datalad.org/shub/gearslaboratory/gears-singularity/gears-lidr/2019-02-19-402c6348-f736dbe7/f736dbe780a767209ebd6435830eb1c3.simg"
datalad_url: https://datasets.datalad.org?dir=/shub/gearslaboratory/gears-singularity/gears-lidr/2019-02-19-402c6348-f736dbe7/
recipe: https://datasets.datalad.org/shub/gearslaboratory/gears-singularity/gears-lidr/2019-02-19-402c6348-f736dbe7/Singularity
collection: gearslaboratory/gears-singularity
---

# gearslaboratory/gears-singularity:gears-lidr

```bash
$ singularity pull shub://gearslaboratory/gears-singularity:gears-lidr
```

## Singularity Recipe

```singularity
BootStrap: debootstrap
OSVersion: xenial
MirrorURL: http://archive.ubuntu.com/ubuntu/
Include: bash

##### GEARS Lab General-use Singularity image.  Contains R, GDAL, GRASS, and other code...

%post
  locale-gen en_US.UTF-8
  sed -i 's/main/main restricted universe/g' /etc/apt/sources.list
  echo "deb http://cran.rstudio.com/bin/linux/ubuntu xenial/" | tee -a /etc/apt/sources.list
  gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
  gpg -a --export E084DAB9 | apt-key add -
  apt-get update

  # Latest R
  apt-get install -y software-properties-common python-software-properties
  # add-apt-repository ppa:edd/r-3.5
  apt-get update
  
  # Install R, openmpi, misc. utilities:
  apt-get install -y libopenblas-dev r-base-core r-base-dev libcurl4-openssl-dev libopenmpi-dev openmpi-bin openmpi-common openmpi-doc openssh-client openssh-server libssh-dev wget vim git nano git cmake  gfortran g++ curl wget python autoconf bzip2 libtool libtool-bin libxml2-dev 

  # GRASS GIS and QGIS:
  apt-get install -y software-properties-common python-software-properties
  add-apt-repository ppa:ubuntugis/ppa
  apt-get update
  apt-get install -y grass libgdal-dev libproj-dev python-gdal python3-gdal qgis python-qgis

  # Miscellaneous other installs.
  # libudunits2-dev is needed for the package "sf"
  apt-get install -y libudunits2-dev
  
  # SVN:
  apt-get install -y subversion

  # Clean up the installations...
  apt-get clean

  # Install required R packages
  R --slave -e 'install.packages(c("doMPI","XML","raster","rgdal","rgeos","RStoolbox","devtools","sf","foreach","R.utils","spatial.tools","gdalUtils","randomForestSRC","remotes","future"), repos="https://cloud.r-project.org/")'
  
  # Install lidR:
  add-apt-repository ppa:glasen/freetype2
  apt-get update && apt-get install -y freetype2-demos
  # apt-get install -y freetype
  R --slave -e 'install.packages(c("lidR"), repos="https://cloud.r-project.org/")'
  
  # Install latest GDALUtils:
  # R --slave -e 'remotes:::install_svn("svn://r-forge.r-project.org/svnroot/gdalutils/pkg/gdalUtils")'
  
  # Install latest spatial.tools:  
  # R --slave -e 'remotes:::install_svn("svn://r-forge.r-project.org/svnroot/spatial-tools/pkg/spatial.tools")'  
  
  # ESPA tools:
  R --slave -e 'remotes:::install_svn("svn://r-forge.r-project.org/svnroot/espa-tools/pkg/espa.tools")'
  
  # Install beta of mmap for now: 
  R --slave -e 'devtools:::install_git("https://github.com/gearslaboratory/gears-singularity.git",subdir="singularity_additional_data/general_use/mmap")'  
  
  # Install pronghorn-tweaked rslurm:
  # R --slave -e 'devtools:::install_github("jgrn307/rslurm")'
  
  # wine:
  mkdir -p /APPS /PROFILES
  chmod 0777 /APPS /PROFILES
  dpkg --add-architecture i386
  apt-get update && apt-get -y install wget less vim software-properties-common python3-software-properties apt-transport-https winbind
  wget https://dl.winehq.org/wine-builds/Release.key
  apt-key add Release.key
  apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
  apt-get update && apt-get install -y winehq-stable winetricks # this installs Wine2
  apt-get clean
  
  # lastools
  cd ‾
  wget http://lastools.org/download/LAStools.zip
  unzip LAStools.zip
  mv LAStools /opt/
  # TODO: shortcuts/licensing
  
  ### SLURM FROM WITHIN THE CONTAINER VIA SSH

  echo '#!/bin/bash
ssh $USER@$HOSTNAME sacct $1' >> /usr/local/bin/sacct
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sacctmgr $1' >> /usr/local/bin/sacctmgr
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME salloc $1' >> /usr/local/bin/salloc
    
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sattach $1' >> /usr/local/bin/sattach
    
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sbatch $1' >> /usr/local/bin/sbatch
    
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sbcast $1' >> /usr/local/bin/sbcast
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME scancel $1' >> /usr/local/bin/scancel
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME scontrol $1' >> /usr/local/bin/scontrol
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sdiag $1' >> /usr/local/bin/sdiag
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sgather $1' >> /usr/local/bin/sgather
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sinfo $1' >> /usr/local/bin/sinfo
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME smap $1' >> /usr/local/bin/smap
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sprio $1' >> /usr/local/bin/sprio
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME squeue $1' >> /usr/local/bin/squeue
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sreport $1' >> /usr/local/bin/sreport
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME srun $1' >> /usr/local/bin/srun
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sshare $1' >> /usr/local/bin/sshare
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sstat $1' >> /usr/local/bin/sstat
      
  echo '#!/bin/bash
ssh $USER@$HOSTNAME strigger $1' >> /usr/local/bin/strigger
  
  echo '#!/bin/bash
ssh $USER@$HOSTNAME sview $1' >> /usr/local/bin/sview
  
  cd /usr/local/bin
  chmod 755 sacct salloc sbatch scancel sdiag sinfo sprio sreport sshare strigger sacctmgr sattach sbcast scontrol sgather smap squeue srun sstat sview    
  
  cd ‾
```

## Collection

 - Name: [gearslaboratory/gears-singularity](https://github.com/gearslaboratory/gears-singularity)
 - License: None

