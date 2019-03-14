# Ubuntu-18.04 CUDA.10 nnCuda-7 tensorflow-1.13 installation

# Ubuntu-18.04 CUDA.10 nnCuda-7 tensorflow-1.13 installation
1. Goto miniconda website download miniconda linux python3.7 64-bit
2. https://docs.conda.io/en/latest/miniconda.html
3. open terminal and go to download folder and install miniconda
    chmod 775 Miniconda3-latest-Linux-x86_64.sh
    ./Miniconda3-latest-Linux-x86_64.sh

And then type

    conda create --name py37 
    conda activate py37

In case you open jupyter notebook and find out that, 500 internal error
type

    python3 -m pip install ipykernel
    python3 -m ipykernel install --user

And then, install tensorflow-gpu version and keras

    pip install tensorflow-gpu keras # 安装 gpu 版本的 tensorflow 和 keras

Then the installation should be complete,
try running this file on jupyter notebook to find out whether the installation complete or not.

    import tensorflow as tf
    print('tf version = ', tf.__version__)
    with tf.device('/gpu:0'):
        a = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[2, 3], name='a')
        b = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[3, 2], name='b')
        c = tf.matmul(a, b)
    with tf.Session() as sess:
        print (sess.run(c))

Well done!

