# 《Python深度学习（第2版）》代码及笔记
&emsp;&emsp;Francois Chollet的《Python深度学习（第2版）》介绍了用Python和Keras进行深度学习的探索实践，涉及计算机视觉、自然语言处理、生成式模型等应用。书中包含30多个代码示例，步骤讲解详细透彻。  

## 使用说明
1. 关于本笔记中的代码，本书中的源码是基于keras的，但是后端用的是tensorflow1.X的引擎，所以在tensorflow2上面会有很多报错，比如第8章的代码中，就有很多Tensorflow的广播方法报错。  
2. 本笔记中的有些代码采用了TensorFlow2重写（代码目录：tensorflow_V2_src），主要还是动态图的问题，导致有些代码重写难度大。
3. 关于python包的版本问题，请详见requirements.txt文件，笔者采用的tensorflow-gpu==2.0.0，可以使用cpu版本，但是运行会特别慢。
4. 相关数据集见百度网盘的下载地址：链接：https://pan.baidu.com/s/1XdkibXpL-UNG0dXk1w5fNw 提取码：u8pn
5. keras模型与数据下载地址：链接：https://pan.baidu.com/s/1Rt6KYWUAQ8MWKY9UVVDtmQ 提取码：wedp  
6. 由于笔者的电脑配置不行，推荐大家租用GPU服务器来运行示例代码，租用方式链接：https://mp.weixin.qq.com/s?__biz=MzU0NjczNTg2NQ==&mid=2247486813&idx=2&sn=93e72cdf73675df69bcbe32de057f6dc&chksm=fb585ecbcc2fd7ddf3858cff26be550e37b578fb522446e7fcf1b71f2f0788231f730cc9f03c&token=1693266535&lang=zh_CN#rd

## 安装环境

1. 安装CUDA
- 安装cuda_11.8.0_522.06_windows.exe
- 解压cudnn-windows-x86_64-8.5.0.96_cuda11-archive.zip包，将bin、include、lib下的文件分别拷贝到`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8`的各个目录下，其中`lib`的内容放到`lib\x64`目录下
- 配置环境变量（PATH下面一共有5个NVIDIA的配置）
```shell
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\extras\CUPTI\lib64;%PATH%
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\include;%PATH%
SET PATH=C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\lib\x64;%PATH%
SET PATH=C:\tools\cuda\bin;%PATH%
```

2. 安装GPU版本的Tensorflow

- 安装tensorflow-gpu
```shell
pip install tensorflow-gpu
```

- 测试环境
```python
import tensorflow as tf

tf.config.list_physical_devices('GPU')
```

3. 安装notebook
```shell
pip install notebook jupyter_nbextensions_configurator
```

4. 安装matplotlib
```shell
pip install matplotlib
```