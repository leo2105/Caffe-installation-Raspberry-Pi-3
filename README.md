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


#### Modify next lines, instead of these

'#'CPU_ONLY := 1

/usr/lib/python2.7/dist-packages/numpy/core/include

INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include

LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib

#### with 

CPU_ONLY := 1

/usr/local/lib/python2.7/dist-packages/numpy/core/include

INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/

LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/arm-linux-gnueabihf/hdf5/serial/


#### Put in your terminal

make all

make test

make runtest

make pycaffe

./scripts/download_model_binary.py models/bvlc_googlenet

sudo nano ~/.bashrc

export PYTHONPATH=/home/pi/deepdream/caffe/python:$PYTHONPATH  // Add at the end of file


## Protobuf installation

cd ~/caffe

cd python

python setup.py build

python setup.py google_test

sudo python setup.py install


## Example Web Demo in Caffe

Thanks to Knight of Pi
http://www.knight-of-pi.org/deepdream-on-the-raspberry-pi-3-with-raspbian-jessie/
