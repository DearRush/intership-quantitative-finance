# 研究报告--基于卷积神经网络的股价走势分类

## 背景

实习期间我最主要的任务就是研报的阅读分析和复现。本Github代码库主要复现了广发证券研究报告：《基于卷积神经网络的股价走势AI识别与分类》。

其主要思路如下：

![](./Background.png)

## 代码库介绍

### mpl_guidance.ipynb

为了绘制图像，需要使用到mplfinance这一金融图像绘制Python包。该notebook文件使用了一个示例csv文件，探索了该程序包能够完成的各项任务。该文件是我在学习该程序包用法过程中的整理记录。

### /data

绘图和图片标签需要的原始数据文件示例。Ret.h5是股票五日收益率，2006.h5是该年份股票的基本面信息。

### /CNN/drawing_function

真正用于项目中的绘图代码。在项目中实际上需要将大量股票的2006~2023年数据转换为图像，最终的图片数量至少有数百万张。因此，除了限制图片分辨率之外，还使用了并行手段加快绘图速度。

一个长期的示例：（项目中只需要20日）

![](./intership-quantitative/Work/example.png)

### /CNN/image、/CNN/log、/CNN/shell、/CNN/result

存储图片、输出记录、辅助脚本、输出结果文件的文件夹

### /CNN/dataset.py

自定义的图像装载类，进而实现了通过指定起始时间点获取指定时间段内图片的功能。

### /CNN/calculate.py

为了实现CNN的输入标准化，我们需要计算数据集图片各通道的均值、方差。该文件用于实现该功能。

### /CNN/model.py

神经网络架构和参数的定义文件，我们尝试过VGG、Resnet等结构

### /CNN/training.py

网络训练的全流程，同时包括了获得因子的评价、输出过程。
