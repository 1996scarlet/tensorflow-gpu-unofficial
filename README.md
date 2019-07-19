# tensorflow-gpu-unofficial
Building tesorflow wheels with CUDA 10.1 and CUDNN 7.5.1

### 获取Ubuntu上的python3.6预编译wheel (for AVX2.0 GTX1080/1070/1060 Capability 6.1)
* [TensorFlow 1.12.0 & CUDA 10.0 & CUDNN 7.3.1](https://github.com/1996scarlet/tensorflow-gpu-unofficial/blob/master/python-wheel/CUDA-10.0-GTX1080/tensorflow-1.12.0-cp36-cp36m-linux_x86_64.whl)
* [TensorFlow 1.11.0 & CUDA 10.0 & CUDNN 7.3.1](https://github.com/1996scarlet/tensorflow-gpu-unofficial/blob/master/python-wheel/CUDA-10.0-GTX1080/tensorflow-1.11.0-cp36-cp36m-linux_x86_64.whl)
* [TensorFlow 1.12.0 & CUDA 9.2 & CUDNN 7.1.4](https://github.com/1996scarlet/tensorflow-gpu-unofficial/blob/master/python-wheel/CUDA-9.2-GTX1080/tensorflow-1.12.0-cp36-cp36m-linux_x86_64.whl)
* [TensorFlow 1.10.1 & CUDA 9.2 & CUDNN 7.1.4](https://github.com/1996scarlet/tensorflow-gpu-unofficial/blob/master/python-wheel/CUDA-9.2-GTX1080/tensorflow-1.10.1-cp36-cp36m-linux_x86_64.whl)

### 获取Ubuntu上的python3.6预编译wheel (for AVX2.0 RTX2080/2070 Capability 7.5)
* [TensorFlow 1.12.0 & CUDA 10.0 & CUDNN 7.3.1](https://github.com/1996scarlet/tensorflow-gpu-unofficial/blob/master/python-wheel/CUDA-10.0-RTX2080/tensorflow-1.12.0-cp36-cp36m-linux_x86_64.whl)

### 获取CUDA和CUDNN
*  [link to CUDA](https://developer.nvidia.com/cuda-downloads)
*  [link to CUDNN](https://developer.nvidia.com/cudnn)

### 安装CUDA
1. `sudo dpkg -i cuda-repo-ubuntu1804_10.0.130-1_amd64.deb`
2. `sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub`
3. `sudo apt-get update`
4. `sudo apt-get install cuda`

### 安装CUDNN和CUDNN-dev
* `sudo dpkg -i libcudnn7_7.3.1.20-1+cuda10.0_amd64.deb`
* `sudo dpkg -i libcudnn7-dev_7.3.1.20-1+cuda10.0_amd64.deb`

### GET keras and bazel
* pip3 install keras wheel six numpy mock --user
* [bazel releases](https://github.com/bazelbuild/bazel/releases)
* wget https://github.com/bazelbuild/bazel/releases/download/0.17.2/bazel-0.17.2-installer-linux-x86_64.sh
* chmod +x bazel-0.17.2-installer-linux-x86_64.sh
* ./bazel-0.17.2-installer-linux-x86_64.sh --user
* echo 'export PATH="$PATH:$HOME/bin"' >> ~/.basshrc
* source ~/.bashrc
* sudo ldconfig

### CONFIG
* gedit configure.py
* _DEFAULT_CUDA_VERSION = '10.1'
* _DEFAULT_CUDNN_VERSION = '7.5.1'
* _DEFAULT_NCCL_VERSION = '1.3'
* _DEFAULT_CUDA_COMPUTE_CAPABILITIES = '3.5,7.5'
* _DEFAULT_CUDA_PATH = '/usr/local/cuda-10.1'
* ./configure

### BUILD tensorflow
* bazel build --config=opt --config=cuda //tensorflow/tools/pip_package:build_pip_package
* bazel-bin/tensorflow/tools/pip_package/build_pip_package tensorflow_pkg
* cd tensorflow_pkg
* pip3 install tensorflow*.whl --user

### Test tensorflow
* python3
* import tensorflow as tf
* sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))

### uninstall
* sudo find / -name "*opencv*" -exec rm -rfi {} \;
* ubuntu-drivers devices
* sudo apt-get remove --purge '^nvidia-.*'
* dpkg -l | grep nvidia
* sudo dpkg -P libnvidia-compute-410
* dpkg -l | grep ^rc | cut -d' ' -f3 | sudo xargs dpkg --purge
