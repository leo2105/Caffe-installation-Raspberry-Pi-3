# Caffe installation in Raspberry Pi 3

This is a installation of caffe in raspberry pi

## Installation of dependencies

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install -y gfortran cython 

sudo apt-get install -y libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler git

sudo apt-get install --no-install-recommends libboost-all-dev

sudo apt-get install -y python-dev libgflags-dev libgoogle-glog-dev liblmdb-dev libatlas-base-dev python-skimage

sudo pip install pyzmq jsonschema pillow numpy scipy ipython jupyter pyyaml


## Install caffe

git clone https://github.com/BVLC/caffe

cd caffe

cp Makefile.config.example Makefile.config

sudo nano Makefile.config


Modify next lines

Instead of these lines

'#'CPU_ONLY := 1

/usr/lib/python2.7/dist-packages/numpy/core/include

INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include

LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib

with 

CPU_ONLY := 1

/usr/local/lib/python2.7/dist-packages/numpy/core/include

INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/

LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/arm-linux-gnueabihf/hdf5/serial/



