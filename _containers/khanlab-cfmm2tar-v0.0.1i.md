---
id: 5246
name: "khanlab/cfmm2tar"
branch: "master"
tag: "v0.0.1i"
commit: "6cc0e88a2b2a73a5a453a0b788127418758d9552"
version: "49bba3e02394c76b70dd24fdf5da9cf1"
build_date: "2021-04-13T01:38:46.989Z"
size_mb: 599
size: 244281375
sif: "https://datasets.datalad.org/shub/khanlab/cfmm2tar/v0.0.1i/2021-04-13-6cc0e88a-49bba3e0/49bba3e02394c76b70dd24fdf5da9cf1.simg"
url: https://datasets.datalad.org/shub/khanlab/cfmm2tar/v0.0.1i/2021-04-13-6cc0e88a-49bba3e0/
recipe: https://datasets.datalad.org/shub/khanlab/cfmm2tar/v0.0.1i/2021-04-13-6cc0e88a-49bba3e0/Singularity
collection: khanlab/cfmm2tar
---

# khanlab/cfmm2tar:v0.0.1i

```bash
$ singularity pull shub://khanlab/cfmm2tar:v0.0.1i
```

## Singularity Recipe

```singularity
Bootstrap: docker
From: ubuntu:xenial
#########

%setup
#########
mkdir -p $SINGULARITY_ROOTFS/src
cp *.sh  $SINGULARITY_ROOTFS/src

mkdir -p $SINGULARITY_ROOTFS/apps/cfmm2tar
cp *.py  $SINGULARITY_ROOTFS/apps/cfmm2tar
cp cfmm2tar $SINGULARITY_ROOTFS/apps/cfmm2tar

#########
%post
#########

#needed for keytool
if [ ! -e /dev/fd ]
then
ln -s /proc/self/fd /dev/fd
fi

export DEBIAN_FRONTEND=noninteractive
apt-get update && apt-get install -y --no-install-recommends apt-utils \
    sudo \
    git \
    wget \
    curl \
    zip \
    unzip \
    python2.7 \
    python-pip \
    rsync \
    openssh-client

sudo pip install --upgrade pip
sudo pip install --upgrade setuptools

#for some unknown reason, need change the mode:
chmod a+x /apps/cfmm2tar/*.py

##install pydicom
#mkdir /opt/pydicom
#cd /opt/pydicom
#git clone https://www.github.com/pydicom/pydicom.git
#cd pydicom
#git checkout ebf6a79602348d003a1d1324c66626f9f2b05432
#python setup.py install

#dicomunwrap, will install pydicom
cd /apps
git clone https://gitlab.com/cfmm/DicomRaw
cd DicomRaw
sudo pip install -r requirements.txt

#needed when install dcm4che
apt-get install -y default-jre

#install dcm4che
cd /src
bash install_dcm4che_ubuntu.sh /opt

#For retrieving physio dicom files. without this line, all the physio series will not be retrieved with getscu
echo '1.3.12.2.1107.5.9.1:ImplicitVRLittleEndian;ExplicitVRLittleEndian' >>/opt/dcm4che-3.3.8/etc/getscu/store-tcs.properties

#allow the getscu client to download CFMM's 9.4T data.
echo 'EnhancedMRImageStorage:ImplicitVRLittleEndian;ExplicitVRLittleEndian'>>/opt/dcm4che-3.3.8/etc/getscu/store-tcs.properties

#########
%environment

#dicomunwrap
export PATH=/apps/DicomRaw/bin:$PATH

#dcm4che
export PATH=/opt/dcm4che-3.3.8/bin:$PATH

#python scripts
export PATH=/apps/cfmm2tar:$PATH
export _JAVA_OPTIONS="-Xmx2048m"

%runscript
exec cfmm2tar "$@"
```

## Collection

 - Name: [khanlab/cfmm2tar](https://github.com/khanlab/cfmm2tar)
 - License: [GNU General Public License v3.0](https://api.github.com/licenses/gpl-3.0)
