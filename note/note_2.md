# 建議的課前小工作 20230308

安裝 FATE 範例 1.10 的 Docker

```
docker pull federatedai/standalone_fate:1.10.0
```

可以事先建立好目錄掛載目錄

```
D:\docker\fate-share
```

```
# 掛載目錄寫法範例
docker run -it -v D:\docker\fate-share:/share dbe096af397a19d210b24230f23e5147298964f99fb05ca25814603e9348840f /bin/bash

# 官方版本範例
docker run -it --name standalone_fate -p 8080:8080 federatedai/standalone_fate:${version}

# 官方版本範例 1.10.0
docker run -it --name standalone_fate -p 8080:8080 federatedai/standalone_fate:1.10.0
```

最終版本

```
docker run -it -v D:\docker\fate-share:/share -p 8080:8080 federatedai/standalone_fate:1.10.0 /bin/bash
docker container start standalone_fate
```