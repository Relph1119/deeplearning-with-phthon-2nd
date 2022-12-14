# 《Python深度学习（第2版）》代码及笔记
&emsp;&emsp;Francois Chollet的《Python深度学习（第2版）》介绍了用Python和Keras进行深度学习的探索实践，解决从计算机视觉到自然语言处理等现实世界的诸多问题，包括图像分类、图像分割、时间序列预测、文本分类、机器翻译、文本生成等应用。书中包含30多个代码示例，逐步讲解各类深度学习场景的解决方法与步骤。  

原书项目代码：https://github.com/fchollet/deep-learning-with-python-notebooks

## 安装环境

1. 基础环境
- Python版本：Windows Python 3.8.10
- [CUDA安装包下载地址](链接：https://pan.baidu.com/s/1rlX8ErIYYY8F_rFdEe5IgA?pwd=iwa5)

2. 安装CUDA
- 安装cuda_11.8.0_522.06_windows.exe
- 解压cudnn-windows-x86_64-8.5.0.96_cuda11-archive.zip包，将bin、include、lib下的文件分别拷贝到`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8`的各个目录下，其中`lib`的内容放到`lib\x64`目录下
- 配置环境变量（PATH下面一共有5个NVIDIA的配置）
```shell
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\extras\CUPTI\lib64;%PATH%
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\include;%PATH%
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\lib\x64;%PATH%
```
- 解压zlib123dllx64.zip包，将相关路径添加到PATH中
```shell
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\zlib123dllx64\dll_x64;%PATH%
```
以上安装步骤可参考[《cuDNN安装指南》](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html#prerequisites-windows)

3. 安装GPU版本的Tensorflow

- 安装tensorflow-gpu
```shell
pip install tensorflow-gpu
```

- 验证环境是否安装正常
```python
import tensorflow as tf

tf.config.list_physical_devices('GPU')
```

4. 安装notebook
```shell
pip install notebook jupyter_nbextensions_configurator
```

5. 安装matplotlib
```shell
pip install matplotlib
```

6. 安装pydot和graphviz
```shell
pip install pydot graphviz
```

7. 安装scipy
```shell
pip install scipy
```

## 相关数据集

使用说明：下载数据集，将其解压到`data`目录下即可。

数据集下载地址：链接：https://pan.baidu.com/s/1hu8YFaqfDTMuSJBJtK-csA?pwd=eucs

- cats_vs_dogs_small：第8.2节使用，已完成图像复制的猫狗分类数据集，包含训练目录、验证目录和测试目录
- pets：第9.2节使用，Oxford-IIIT宠物数据集
- celeba_gan：第12.5节使用，大规模名人脸部属性数据集
- spa-eng：第11.5节使用，英语到西班牙语的翻译数据集
- aclImdb：第11.3节、第12.1节使用，IMDB影评数据集
- jena_climate_2009_2016.csv：第10.2节使用，耶拿天气时间序列数据集

## 总结

1. 如果本地显存低于12G，建议从第9章开始，使用Google Colaboratory进行书中的实验
2. CUDNN具有专门加速LSTM和GRU层的功能，这些GRU/LSTM层只有在满足特定标准时才能加速，否则训练会非常慢（第10.4.2节），条件如下：
    - activation为tanh
    - recurrent_activation为sigmoid
    - recurrent_dropout为0
    - unroll为False
    - use_bias为True
3. 由于GAN网络训练耗费的时间很长，笔者没有运行第12.5节的实验