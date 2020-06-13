Background
===================

The land cover classification is vary important for trace the source of pollution.
Especially the bare land and factory recognition. Bare land could be the main source of the dust
and factory without filter equipments could be the main source of air pollution of local area.

In 2019, Professor Gong from Tsinghua university cooperated with experts from multiple institutions published
"Stable classification with limited sample: transferring a 30-m resolution sample set collected in 2015 to mapping 10-m resolution global land cover in 2017"
https://www.sciencedirect.com/science/article/pii/S2095927319301380
开发出了世界首套10-m分辨率的全球土地覆盖产品——FROM-GLC10
The data is available with the following link
http://data.ess.tsinghua.edu.cn/

Based on sentinel-2 dataset instead of Landsat8, the classification spatial resolution increase from 30m to 10m.
对卫星遥感来说，对ground truth的选取也是非常的费时费力。不同时间，不同季节的均需要选取出一定量的训练样本。才能基本保证分类的准确性。
加上由landsat8到sentinel2采用传感器不同，波段中心波长和波谱范围有少量差异，能够成功基于landsat8之前的训练样本迁移到新的训练数据中
十分不易。加上全球数据量庞大，处理起来也是十分困难。
其中地物类别主要集中于植被，包括草地，森林，农作物，水，Impervious （不可渗透的）等方面，对于城市中的地物分类较少。
所以采用相对传统的random forest分类器能够在保证一定精度的前提下加强一部分训练速度.

但是随着近两年卷积神经网络的兴起，加上高分辨率卫星的广泛应用。对城市中不同地物的细分类成为可能。
一篇论文中利用航测数据基于ResUNet-a对城市中的不同地物进行了分类，
__把论文ref

这其中航测数据的范围相对卫星来说相对较小，分辨率较高。也少受云层干扰，预处理相对简单。如果用来分类多个城市的成本相对较高。
但是深度学习方法的介入一定程度上提高了遥感图像的分类精度。

为了城市中结合我们的地面监测站，对一些环境污染（PM10，气体污染指标）问题进行精准溯源，我们需要对一些特定城市进行精细的地物分类。
所以本次实验结合两种论文的思想，提出了一种相对快速针对局部区域的城市分类方法。

1.数据采用两米分辨率的高分影像，由供应商直接提供RGB图像，可以直接使用，省去预处理所需时间
2.结合Res—Unet模型进行预测

In the high resolution of satellite image, the pixel-based classification still fail to satisfy
the accuracy requirements because of the following reasons:

1. The influence of atmosphere -- cloud cover.
多光谱数据对大气层的影响非常敏感，因此如何祛除大气层的影响一直是一个比较棘手的问题。采用合适的模型补偿大气影响
是非常重要的数据预处理步骤。即使经过严格的数据预处理，最终每一景影像的最终成像效果还是会有一些差异，这些差异对于
卫星图像的分类来说也是一种挑战。


2. 卫星图像不同于航测图像，两者拍摄方法和成图原理不同。高分辨率遥感卫星大多采用线阵列CCD传感器，按照推帚视扫描成像。

Gaofen 2 satellite is chinese second satellite of gaofen series.
2D Semantic Labeling Contest - Potsdam 航测数据源


