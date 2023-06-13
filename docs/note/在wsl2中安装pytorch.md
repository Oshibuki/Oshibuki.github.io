---
lang: zh-CN
title: 在wsl2中安装pytorch的注意事项
description: 在wsl2中安装pytorch的注意事项
---

# 在wsl2中安装pytorch的注意事项

## wslg 与wsl 安装
在wsl中运行像PyTorch这样的深度学习框架的关键是WSLg扩展。此扩展允许 WSL2 使用你的 GPU。这适用于英特尔，AMD和Nvidia GPU。它仍处于预览状态，因此可能包含错误。
https://github.com/microsoft/wslg
```
wsl --update
wsl --shutdown
```

## 在wsl中安装cuda工具包
https://developer.nvidia.com/cuda-11-7-1-download-archive?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local

此处需要格外注意，**官网给出的命令顺序有误**。

```
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pinsudo 
mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.7.1/local_installers/cuda-repo-wsl-ubuntu-11-7-local_11.7.1-1_amd64.deb
sudo dpkg -i cuda-repo-wsl-ubuntu-11-7-local_11.7.1-1_amd64.deb
sudo cp /var/cuda-repo-wsl-ubuntu-11-7-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get updatesudo apt-get -y install cuda
```
直接运行第四行`sudo dpkg -i cuda-repo-wsl-ubuntu-11-7-local_11.7.1-1_amd64.deb`会报错：
```The public CUDA GPG key does not appear to be installed.
To install the key, run this command:
sudo cp /var/cuda-repo-wsl-ubuntu-11-7-local/cuda-96193861-keyring.gpg /usr/share/keyrings/
```
此处的cuda-96193861-keyring.gpg可能和实际文件名称不符，应先运行第五行安装密钥：

`sudo cp /var/cuda-repo-wsl-ubuntu-11-7-local/cuda-*-keyring.gpg /usr/share/keyrings/`

再运行第四行即可。

## 安装pytorch
```pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118```