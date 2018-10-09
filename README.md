# tensorflow-gpu-unofficial
Build tesorflow wheel with CUDA 10.0 and CUDNN 7.3.1

### 获取CUDA和CUDNN
*  [link to CUDA](https://developer.nvidia.com/cuda-downloads)
*  [link to CUDNN](https://developer.nvidia.com/cudnn)

### 安装CUDA
1. `sudo dpkg -i cuda-repo-ubuntu1804_10.0.130-1_amd64.deb`
2. `sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub`
3. `sudo apt-get update`
4. `sudo apt-get install cuda`
