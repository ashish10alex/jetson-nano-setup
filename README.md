# jetson-nano-setup
Get started with using machine learning libraries on Nvidia Jetson Nano

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
pip3 install scipy
```

### Install sounfile, librosa
Refs
- https://learninone209186366.wordpress.com/2019/07/24/how-to-install-the-librosa-library-in-jetson-nano-or-aarch64-module/
- https://stackoverflow.com/questions/61475274/runtimeerror-path-failed-executing-please-point-llvm-config-to-the-path-for/63501475#63501475

```bash
sudo pip3 install --upgrade setuptools
sudo pip3 install cython
#Install LLVM 9 or above to install llvmlite (dependecy for librosa)

sudo apt install llvm-10
cd /usr/bin
#create a simi-link 
sudo ln -s llvm-config-10 llvm-config
#You might get an error llvm-config already exist while creating simi-link
# In that case remove existing first - rm llvm-config
pip3 install llvmlite

sudo apt-get install libblas-dev liblapack-dev libatlas-base-dev gfortran
pip3 install sounfile
pip3 install librosa
```

### Get cuda version** 
`cat /usr/local/cuda-10.2/version.txt` 

### Unable to install torchaudio tried

`pip3 install torchaudio` wont work
Alternate bulding from source will also throw an error - 
A workaround has been mentioned here - [https://github.com/pytorch/audio/issues/658](https://github.com/pytorch/audio/issues/658)

### View gpu stats - nvidia-smi command doesnt work
https://github.com/rbonghi/jetson_stats

## Optimizing models for  for Jetson Nano
https://docs.nvidia.com/deeplearning/tensorrt/install-guide/index.html

https://github.com/NVIDIA-AI-IOT/torch2trt
Issue - Need to check cuda installation corrosposing to tensorrt version ? 
```
# https://github.com/NVIDIA-AI-IOT/torch2trt
pip install nvidia-pyindex
pip install nvidia-tensorrt

git clone https://github.com/NVIDIA-AI-IOT/torch2trt
cd torch2trt
sudo python setup.py install --plugins
```



### Use Laptop or Desktop keyboard on nano 
https://github.com/debauchee/barrier

https://www.youtube.com/watch?v=-G9IIauHOhA

**Note** - 
You will initially need a keyboard and mouse to setup your device jetson device as client. Once you are diconnect from the network you would need to connect the external mouse and keybard again to activate the barrier client. 

**Use macbook pro keyboard layout **
Keyboard setting -> Text settings -> Add `English (UK, intl, Macintosh)`


