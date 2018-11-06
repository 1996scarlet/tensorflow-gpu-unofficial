# tensorflow-gpu-unofficial
Building tesorflow wheels with CUDA 10.0 and CUDNN 7.3.1

### 获取Ubuntu上的python3预编译wheel (for AVX2.0)
* [TensorFlow 1.11.0 & CUDA 10.0 & CUDNN 7.3.1](https://github.com/1996scarlet/tensorflow-gpu-unofficial/blob/master/python-wheel/tensorflow-1.11.0-cp36-cp36m-linux_x86_64.whl)
* [TensorFlow 1.10.1 & CUDA 9.2 & CUDNN 7.1.4](https://github.com/1996scarlet/tensorflow-gpu-unofficial/blob/master/python-wheel/tensorflow-1.10.1-cp36-cp36m-linux_x86_64.whl)

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
* pip3 install keras
* [bazel releases](https://github.com/bazelbuild/bazel/releases)
* get `bazel-X.X.X-installer-linux-x86_64.sh`
* chmod +x bazel-X.X.X-installer-linux-x86_64.sh
* ./bazel-X.X.X-installer-linux-x86_64.sh --user
* source /home/humanmotion/.bazel/bin/bazel-complete.bash

### CONFIG
* gedit configure.py
* _DEFAULT_CUDA_VERSION = '10.0'
* _DEFAULT_CUDNN_VERSION = '7.3.1'
* _DEFAULT_NCCL_VERSION = '1.3'
* _DEFAULT_CUDA_COMPUTE_CAPABILITIES = '3.5,7.0'
* _DEFAULT_CUDA_PATH = '/usr/local/cuda-10.0'
* ./configure

### BUILD tensorflow
* bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
* bazel-bin/tensorflow/tools/pip_package/build_pip_package tensorflow_pkg
