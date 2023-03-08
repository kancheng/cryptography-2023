# 建議的課前小工作 20230301

大家可以優先安裝 Docker

https://www.docker.com/

1. 隨意拉一個 Docker images 下來執行。如果 Windows 可能要處裡 WSL 問題。

所謂的 WSL 就是 MS 公司在 OS 中做了一個 Linux 核心的東西，WSL 可以讓 Windows 可以用一些 Linux 的功能。

2. Docker 外掛目錄讓本地電腦可以連進去。

在本地建立一個名為 docker-save 目錄。

> docker images
> docker run -it -v D:\docker-save:/share python /bin/bash
> docker run -it -v [本地端目錄]:[Docker 目錄] [Docker 映像的名稱] /bin/bash

EX : docker run -it -v D:\docker\fate-share:/share dbe096af397a19d210b24230f23e5147298964f99fb05ca25814603e9348840f /bin/bash