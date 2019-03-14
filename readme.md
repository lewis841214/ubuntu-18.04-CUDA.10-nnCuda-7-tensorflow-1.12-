#ubuntu-18.04 CUDA.10 nnCuda-7 tensorflow-1.12 installation

1. Goto miniconda website download miniconda linux python3.7 64-bit
https://docs.conda.io/en/latest/miniconda.html
2. open terminal and go to download folder and install miniconda
```
chmod 775 Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh
```
After that, you can try to open jupyter notebook,
but no metter it's openable or not
we are going to install tensorflow, where tensorflow-gpu can't be installed on python37,
so we should create a new environment with python 35

```
conda create --name python35 python=3.5
conda activate python35
```
where the --name variable is depends on you, so you can change it like
```
conda create --name mylab python=3.5
conda activate mylab
```
And after that, 
type
```
conda create --name mylab python=3.5
conda activate mylab
```
And now you'll see base changes to mylab
```
(base) lewis@ailab-830-ubuntu:~$ 
(mylab) lewis@ailab-830-ubuntu:~$ 
```
And then, install tensorflow-gpu version and keras
```
pip install tensorflow-gpu keras # 安装 gpu 版本的 tensorflow 和 keras
```

Then the installation should be complete,
try running this file to find out whether the installation complete or not.

```
import tensorflow as tf
print('tf version = ', tf.__version__)
with tf.device('/gpu:0'):
    a = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[2, 3], name='a')
    b = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[3, 2], name='b')
    c = tf.matmul(a, b)
with tf.Session() as sess:
    print (sess.run(c))
```
