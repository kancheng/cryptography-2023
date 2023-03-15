# 建議的課前小工作 20230315

本次課前二選一，第一個是根據 Windows 的文件設定好 WSL。若本身電腦操作系統(作業系統)非 Windows 則進行 Dockerfile 的練習。

## WSL 安裝

在 Windows Docker 需要

https://learn.microsoft.com/zh-tw/windows/wsl/install

### WSL Ubuntu & openSUSE

開啟 Windows 虛擬化設定，去 MS 商店進行安裝

openSUSE Leap 15.4 : https://www.microsoft.com/store/productId/9PJPFJHRM62V

Ubuntu 22.04.2 LTS : https://www.microsoft.com/store/productId/9PN20MSR04DW

本地端電腦，可以跟 WSL 之間的掛載可以在 mnt 下找到。

```
cd /mnt/c/Users/用户名/Downloads/ 
```

## Docker 的 Dockerfile 與基本操作

Test Ubuntu

```
docker run -it -v D:\docker\ubuntu-share:/share [映像名] /bin/bash
```

在單一個目錄下建立起名為 dockerfile 的檔案，內容如下 : 完成後的映像檔則會是已經安裝好 Vim 工具的 Ubuntu 容器。

```
# 基礎映像檔
FROM ubuntu:latest

# 維護者
MAINTAINER Kan

# 操作指令
RUN apt-get update -y\
    && apt-get install vim -y

# 設定運行時容器提供服務的通道
EXPOSE 80

```

指令

```
# 將 Dockerfile 用成 image ，ubunvim 是測試名稱
docker build -t ubunvim .

# 檢視 image
docker images

# 執行
docker run -d -p 80:80 --name [容器名] [映像檔名]
docker run -it -v D:\docker\ubuntu-share:/share ubunvim /bin/bash

# 關閉
docker container stop [容器名]

# 開啟
docker container start [容器名]

# 檢視容器
docker ps -a
```

### Docker exec 命令 - 進入與離開

```
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```

EX :

```
docker exec -it fe8dc /bin/bash
```

-d :分离模式: 在后台运行

-i :即使没有附加也保持STDIN 打开

-t :分配一个伪终端

如果要退出就：Ctrl-D or `exit`