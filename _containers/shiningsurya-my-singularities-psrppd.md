---
id: 14565
name: "shiningsurya/my-singularities"
branch: "main"
tag: "psrppd"
commit: "f56ae96e484a0a8e5759e62af27088de4828a399"
version: "7d6c08b0f5dc604dfd4ed7d28d700d00b5086ef5b5f8d4e0186057a4c1e4e5cb"
build_date: "2021-04-16T08:55:09.577Z"
size_mb: 1612.33203125
size: 1690652672
sif: "https://datasets.datalad.org/shub/shiningsurya/my-singularities/psrppd/2021-04-16-f56ae96e-7d6c08b0/7d6c08b0f5dc604dfd4ed7d28d700d00b5086ef5b5f8d4e0186057a4c1e4e5cb.sif"
url: https://datasets.datalad.org/shub/shiningsurya/my-singularities/psrppd/2021-04-16-f56ae96e-7d6c08b0/
recipe: https://datasets.datalad.org/shub/shiningsurya/my-singularities/psrppd/2021-04-16-f56ae96e-7d6c08b0/Singularity
collection: shiningsurya/my-singularities
---

# shiningsurya/my-singularities:psrppd

```bash
$ singularity pull shub://shiningsurya/my-singularities:psrppd
```

## Singularity Recipe

```singularity
Bootstrap:           library
From:                ubuntu:20.04

%setup

%labels
	Author             shiningsurya
	Hosting            Github
	Version            v0.0.1


%help
	This is a singularity container which installs three pulsar softwares. 
	PRESTO, PSRCHIVE, and DSPSR and all its dependencies.


%post
	apt-get -y update 
	apt-get -y install build-essential binutils-dev
	apt-get -y install software-properties-common
	apt-get -y install ftp wget curl dkms
	apt-get -y install autoconf automake libtool autotools-dev
	apt-get -y install pkg-config
	add-apt-repository universe
	add-apt-repository multiverse
	apt-get -y update 
	apt-get -y install csh tcsh
	apt-get -y install make man mc mlocate lsof

	# GNU compiler collections
	apt-get -y install gcc g++ gfortran fort77 f2c
	apt-get -y install libboost-all-dev

	# other closely related stuff
	apt-get -y install flex bison swig libbison-dev
	apt-get -y install cmake m4
	apt-get -y install hwloc libhwloc-dev
	apt-get -y install gsl-bin libgsl-dev 

	# X11
	apt-get -y install libx11-dev libxext-dev libxext-doc
	apt-get -y install default-jre default-jdk

	# Qt5
	apt-get -y install qt5-default 

	# ssh numa nfs
	apt-get -y install openssh-server numactl
	apt-get -y install libssl-dev libsocket++-dev libsocket++1
	apt-get -y install nfs-common

	# essential libraries
	apt-get -y install libblas64-dev liblapack64-dev liblapacke64-dev libxext-dev
	apt-get -y install libeigen3-dev libxml2-dev libxml2-doc
	apt-get -y install libopenblas-base libopenblas-dev
	apt-get -y install libpng++-dev libpng-dev libpnglite-dev 
	apt-get -y install libgsl-dev libgmp-dev
	apt-get -y install libfftw3-bin libfftw3-dev
	apt-get -y install libglib2.0-dev libglib2.0-bin libbsd-dev
	apt-get -y install libreadline-dev 
	apt-get -y install libhealpix-cxx-dev libhealpix-cxx2
	apt-get -y install libyaml-cpp-dev

	# unittest
	# ghost
	apt-get -y install libcppunit-dev libcppunit-subunit-dev
	apt-get -y install ghostscript dvipng gv


	# HDF5
	apt-get -y install h5utils hdf5-helpers hdf5-tools hdfview
	apt-get -y install libhdf5-dev libhdf5-serial-dev

	# Lua
	apt-get -y install liblua5.1-0 liblua5.1-0-dev liblua5.2-0 liblua5.2-dev liblua5.3-0 liblua5.3-dev

	# MPI
	apt-get -y install openmpi-bin libopenmpi-dev mpich libmpich-dev
	apt-get -y install libhdf5-openmpi-dev libhdf5-mpich-dev

	# PGPLOT-ing
	# pdf 
	# groff
	apt-get -y install pgplot5
	apt-get -y install libpoppler-dev libpoppler-glib-dev
	apt-get -y install poppler-utils
	apt-get -y install xterm imagemagick

	# GNU plotting
	# that silly interactive stuff
	# apt-get -y install gnuplot 

	# cfitsio
	apt-get -y install libcfitsio-bin libcfitsio-dev libcfitsio-doc
	# multitask
	apt-get -y install tmux screen
	# can not do anything without you
	apt-get -y install rsync parallel

	# misc
	apt-get -y install htop
	apt-get -y install cvs git subversion
	apt-get -y install sed grep gawk
	apt-get -y install vim emacs nano
	apt-get -y install groff worker

	# ldconfig
	ldconfig

	# python
	apt-get -y install python cython python3
	apt-get -y install python3-notebook jupyter jupyter-core 
	apt-get -y install python3-numpy python3-numpydoc  python3-matplotlib python3-pip 

	# pip my image
	# installing pip via pip3 installs pip and I never got the hang
	# of it
	pip3 install -U setuptools datetime pytz bitstring
	pip3 install -U numpy scipy pandas 
	pip3 install -U matplotlib APLpy
	pip3 install -U six h5py nose
	pip3 install -U mpi4py schwimmbad joblib
	pip3 install -U scikit-learn scikit-video scikit-image
	pip3 install -U bokeh corner seaborn
	pip3 install -U paramz peakutils
	pip3 install -U splinter tqdm
	pip3 install -U emcee ChainConsumer
	pip3 install -U setuptools_scm pep517 
	
	# astropy
	pip3 install -U astropy astroplan astropy_helpers astroquery

	# ipython
	pip3 install -U ipython

	# random?
	pip3 install -U pyfits lmfit statsmodels 
	pip3 install -U pyephem psrqpy

	# sigpyproc
	pip3 install -U git+https://github.com/FRBs/sigpyproc3

	# update alternatives
	update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1
	update-alternatives --install /usr/bin/python python /usr/bin/python2.7 2
	update-alternatives --set python /usr/bin/python3.8

	# ldconfig
	ldconfig

	#################################################################
	######### GOING TO SOFTWARES
	#################################################################
	np=2

	wget "http://www.atnf.csiro.au/people/pulsar/psrcat/downloads/psrcat_pkg.tar.gz"
	git clone https://github.com/SixByNine/psrxml.git 
	git clone https://github.com/SixByNine/sigproc.git 
	#git clone https://github.com/ewanbarr/sigpyproc.git 
	git clone https://github.com/nextgen-astrodata/DAL.git
	git clone https://git.code.sf.net/p/psrchive/code psrchive 
	git clone https://git.code.sf.net/p/dspsr/code dspsr 
	git clone https://github.com/scottransom/presto.git 
	git clone git://git.code.sf.net/p/psrdada/code psrdada
	git clone https://github.com/straten/epsic.git
	git clone https://github.com/scottransom/pyslalib.git


	CTIME=`date`
	echo "export CTIME=\"${CTIME}\"" >> $SINGULARITY_ENVIRONMENT
	### and the process begins
	tar xvzf psrcat_pkg.tar.gz 
	cd psrcat_tar 
	./makeit && cp psrcat /usr/bin
	cd ../

	# this causes a weird linking error when building psrchive
	#cd psrxml 
	#autoreconf --install --warnings=none
	#./configure
	#make -j ${np}
	#make install
	#cd ../

	cd sigproc && ./bootstrap
	./configure FC=gfortran F77=gfortran CC=gcc CXX=g++ --enable-shared CFLAGS=-fPIC FFLAGS=-fPIC
	make -j ${np} && make install && make install
	make install
	cd ../

	cd DAL
	sed -i 's/2.7/3.7/' CMakeLists.txt
	mkdir -p build && cd build
	cmake ..
	make -j ${np} && make install && make install
	make install
	cd ../
	cd ../

	cd pyslalib
	python setup.py install
	cd ../

	cd presto
	P=${PWD}
	cd src
	make prep
	sed -i "s/ifdef USEMMAP/if 1/" accel_utils.c
	PRESTO=${P} PGPLOT_DIR=/usr/lib/pgplot5 make -j ${np} libpresto
	PRESTO=${P} PGPLOT_DIR=/usr/lib/pgplot5 make -j ${np} binaries
	PRESTO=${P} PGPLOT_DIR=/usr/lib/pgplot5 make mpi 
	PRESTO=${P} PGPLOT_DIR=/usr/lib/pgplot5 make libsla.so
	cd ../
	#PRESTO=${P} PGPLOT_DIR=/usr/lib/pgplot5 python setup.py install
	PRESTO=${P} PGPLOT_DIR=/usr/lib/pgplot5 pip3 install .
	cd ../

	cd epsic/src
	./bootstrap
	./configure 
	make -j ${np} && make install && make install 
	cd ../..

	cd psrdada
	./bootstrap
	./configure --enable-shared 
	make -j ${np} && make install && make install 
	cd ../

	cd psrchive
	./bootstrap 
	UI="/usr/include/x86_64-linux-gnu"
	./configure PYTHON=/usr/bin/python3.8 F77=gfortran \
  		--enable-shared --enable-static --with-eigen-include-dir=/usr/include/eigen3 \
		CFLAGS="-fPIC -I/usr/include -I/usr/include/healpix_cxx " FFLAGS="-fPIC -I/usr/include -I/usr/include/healpix_cxx " CXXFLAGS="-fPIC -I/usr/include " \
		LDFLAGS="-L/usr/lib/x86_64-linux-gnu/ -L/lib/x86_64-linux-gnu/ "
	make -j ${np} && make install && make install 
	make install
	cd ../

	cd dspsr
	UI="/usr/include/x86_64-linux-gnu"
	UL="/usr/lib/x86_64-linux-gnu"
	./bootstrap
	echo "apsr asp bcpm bpsr caspsr cpsr cpsr2 dummy dada fits kat lbadr lbadr64 lump lwa vdif gmrt puma2 sigproc ska1" > backends.list
	# ignore mpi because it needs "stdmpi.h,portable_mpi.h"
	# ignore hdf5 because it can not link against libraries anyways
	./configure PYTHON=/usr/bin/python3.8 F77=gfortran \
		--enable-shared --enable-static \
		CFLAGS="-fPIC -I/usr/include -I/usr/include/healpix_cxx" FFLAGS="-fPIC -I/usr/include" CXXFLAGS="-fPIC -I/usr/include -I/usr/include/healpix_cxx " \
		LDFLAGS="-L/usr/lib/x86_64-linux-gnu/ -L/lib/x86_64-linux-gnu/"
	make -j ${np} && make install && make install && make clean
	cd ../ 

	#########################################################
	# clean apt
	apt-get clean

%environment
	export PRESTO=/presto
	export PATH=${PATH}:${PRESTO}/bin
	export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/lib:${PRESTO}/lib
	export PYTHONPATH=${PYTHONPATH}:/usr/local/lib/python3.8/site-packages:/usr/local/lib/python3.8/dist-packages:${PRESTO}/python

	# PGPLOT
	export PGPLOT_DIR=/usr/lib/pgplot5
	export PGPLOT_FONT=/usr/lib/pgplot5/grfont.dat
	export PGPLOT_INCLUDES=/usr/include
	export PGPLOT_BACKGROUND=white
	export PGPLOT_FOREGROUND=black
	export PGPLOT_DEV=/ps
	
	# alias
	alias rm='rm -i'
	alias cp='cp -i'
	alias mv='mv -i'

	# prompt
	export PS1=" Singularity:::PsrPPD \u \w> \n$ "


%runscript
	echo "-------------------------------------"
	echo "--- PRESTO --- PSRCHIVE --- DSPSR ---"
	echo "-------------------------------------"
	echo " Name :  PsrPPD                      "
	echo "This container was created $CTIME"
```

## Collection

 - Name: [shiningsurya/my-singularities](https://github.com/shiningsurya/my-singularities)
 - License: [BSD 3-Clause "New" or "Revised" License](https://api.github.com/licenses/bsd-3-clause)
