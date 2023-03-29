# 建議的課前小工作 20230329

兩個小練習擇一， Google 的聯邦學習方案環境架設，跟 FedAvg 的復現。

# TFF install

根據 Python 、 TensorFlow 版本， 來安裝 TensorFlow Federated，同時 CUDA 的版本也要注意。

```
sudo apt update
sudo apt install python3-dev python3-pip  # Python 3

python3 -m venv "venv"
source "venv/bin/activate"

pip install --upgrade "pip"

# pip install --upgrade tensorflow

# pip install --upgrade tensorflow-federated

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple --upgrade tensorflow

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple --upgrade tensorflow-federated

python -c "import tensorflow_federated as tff; print(tff.federated_computation(lambda: 'Hello World')())"

python -c "import tensorflow as tf;print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
```

```
import tensorflow as tf
import tensorflow_federated as tff
tf.test.is_gpu_available()
print(tf.__version__)
print(tff.__version__)
```

## 付現 FedAvg

- 文獻 -  Communication-Efficient Learning of Deep Networks from Decentralized Data : https://arxiv.org/abs/1602.05629

- https://github.com/AshwinRJ/Federated-Learning-PyTorch

- https://towardsdatascience.com/federated-learning-a-simple-implementation-of-fedavg-federated-averaging-with-pytorch-90187c9c9577

