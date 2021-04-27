# jetson-nano-setup
Helper commands to get started with using machine learning libraries on Nvidia Jetson Nano

### Install pytorch on jetson nano

**Note:** It will take more time than usual (e.g. ~30 mins for pandas) to install packages using pip in jetson nano as most of them are built from source (Ref: [https://forums.developer.nvidia.com/t/jetson-nano-for-data-science/112805](https://forums.developer.nvidia.com/t/jetson-nano-for-data-science/112805))

### Install pytorch

W**arning!!!** - your casual `pip3 install torch torchvision torchaudio` won't work gave an error: package directory 'torch/cuda' does not exist. 
helper link - [https://forums.developer.nvidia.com/t/pytorch-for-jetson-version-1-8-0-now-available/72048#5331080](https://forums.developer.nvidia.com/t/pytorch-for-jetson-version-1-8-0-now-available/72048#5331080)

```bash
#install pytorch 
wget [https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl](https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl) -O torch-1.8.0-cp36-cp36m-linux_aarch64.whl
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev
pip3 install Cython
pip3 install numpy torch-1.8.0-cp36-cp36m-linux_aarch64.whl
```

**Numpy install issue requires** - `sudo apt-get install python3-dev`

### Install scipy

```bash
sudo apt-get install git cmake
sudo apt-get install libatlas-base-dev gfortran
sudo apt-get install libhdf5-serial-dev hdf5-tools
sudo apt-get install python3-dev
pip3 install scipy-
```

### Install sounfile, librosa

```bash
sudo pip3 install --upgrade setuptools
sudo pip3 install cython
sudo apt-get install llvm-7
sudo pip3 install llvmlite #this might get an error
sudo apt-get install libblas-dev liblapack-dev libatlas-base-dev gfortran

#Incase if this installation throws LLVM_CONFIG not found, then create the ln for the llvm-config-7 as below. 
#Just ensure that you have llvm-config under /usr/bin path
/usr/bin$ sudo ln -s llvm-config-7 llvm-config

pip3 install sounfile
pip3 install librosa

```

**Make sure you have** 
`pip uninstall setuptools`
`pip install setuptools`

**Get cuda version** 
`cat /usr/local/cuda-10.2/version.txt` 

**Unable to install torchaudio tried -** 

- `pip3 install torchaudio`
- bulding from source
- A workaround has been mentioned here - [https://github.com/pytorch/audio/issues/658](https://github.com/pytorch/audio/issues/658)
