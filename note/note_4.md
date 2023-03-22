# 建議的課前小工作 20230322


玩玩看 gpu-jupyter、 FATE 跟 TensorFlow 的 Docker

1.  gpu-jupyter 的 Docker，內涵 TensorFlow 跟 PyTorch 的方案，同時必要時可選擇 R, Julia, Python 或者單一只有 Python 的方案。

2. TensorFlow 的 Docker，為官方所提供的 Docker。

3. FATE 則為聯邦學習平台的 Docker。

## gpu-jupyter

```
docker run --gpus all nvidia/cuda:11.6.2-cudnn8-runtime-ubuntu20.04 nvidia-smi

# EX :
docker run --gpus all -d -it -p 8848:8888 -v $(pwd)/data:/home/jovyan/work -e GRANT_SUDO=yes -e JUPYTER_ENABLE_LAB=yes --user root cschranz/gpu-jupyter:v1.4_cuda-11.6_ubuntu-20.04_python-only

# 只有 Python
docker run --gpus all -d -it -p 8848:8888 -v D:/docker/gpu-share:/home/jovyan/work -e GRANT_SUDO=yes -e JUPYTER_ENABLE_LAB=yes --user root cschranz/gpu-jupyter:v1.4_cuda-11.6_ubuntu-20.04_python-only

# 包含 Python, R, Julia
docker run --gpus all -d -it -p 8848:8888 -v D:/docker/gpu-share:/home/jovyan/work -e GRANT_SUDO=yes -e JUPYTER_ENABLE_LAB=yes --user root cschranz/gpu-jupyter:v1.4_cuda-11.6_ubuntu-20.04
```

默認密碼是 `gpu-jupyter` 。如果圖像被拉取，你必須第一次指定你從 `docker exec -it [container-name/ID] jupyter server list` 獲得的 jupyter-token。

After some time, GPU Jupyter will be available on localhost:8848 in the Web browser. In case you are new to the Jupyter project, click here for a nice summary. The default password is gpu-jupyter and should be updated as described in the last section. If the image is pulled, you have to specify for the first time the jupyter-token that you get from docker exec -it [container-name/ID] jupyter server list)

```
docker exec -it [container-name/ID] jupyter server list
```

## TensorFlow 

- https://github.com/tensorflow/federated/blob/main/docs/install.md

```
docker pull tensorflow/tensorflow:latest  # Download latest stable image

# EX :
docker run -it -p 8888:8888 tensorflow/tensorflow:latest-jupyter  # Start Jupyter server 
docker run -it -p [本地 IP]:[容器 IP] tensorflow/tensorflow:latest-jupyter  # Start Jupyter server 

docker run -it -p 9478:8888 -v D:/docker/tensorflow-share:/share tensorflow/tensorflow:latest-jupyter  # Start Jupyter server 

docker run -it --name=tf-init -p 9478:8888 -v D:/docker/tensorflow-share:/share -v D:/docker/tensorflow-tf-share:/tf/share tensorflow/tensorflow:latest-jupyter
```

```
docker exec -it tf-init /bin/bash
```

## FATE

- https://github.com/kancheng/FATE/blob/master/deploy/standalone-deploy/README.zh.md

FATE 範例 1.10

```
docker pull federatedai/standalone_fate:1.10.0
```

可以事先建立好目錄

```
D:\docker\fate-share
```

```
# 掛載目錄寫法
docker run -it -v D:\docker\fate-share:/share dbe096af397a19d210b24230f23e5147298964f99fb05ca25814603e9348840f /bin/bash

# 官方版本
docker run -it --name standalone_fate -p 8080:8080 federatedai/standalone_fate:${version}

# 官方版本 1.10.0
docker run -it --name standalone_fate -p 8080:8080 federatedai/standalone_fate:1.10.0
```

最終版本

```
docker run -it -v D:\docker\fate-share:/share -p 8897:8080 federatedai/standalone_fate:1.10.0 /bin/bash
docker container start standalone_fate
```
