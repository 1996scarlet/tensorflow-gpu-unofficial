# tensorflow-gpu-unofficial
Building tesorflow wheels with CUDA 10.0 and CUDNN 7.3.1

### 获取Ubuntu上的python3预编译wheel
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

### 安装CUDNN-dev
* `sudo dpkg -i libcudnn7-dev_7.3.1.20-1+cuda10.0_amd64.deb`

### GET keras and bazel
* pip3 install keras
* [bazel releases](https://github.com/bazelbuild/bazel/releases)
* get `bazel-X.X.X-installer-linux-x86_64.sh`
* chmod +x bazel-X.X.X-installer-linux-x86_64.sh
* ./bazel-X.X.X-installer-linux-x86_64.sh --user
* source /home/humanmotion/.bazel/bin/bazel-complete.bash

### BUILD tensorflow
* bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
* bazel-bin/tensorflow/tools/pip_package/build_pip_package tensorflow_pkg
