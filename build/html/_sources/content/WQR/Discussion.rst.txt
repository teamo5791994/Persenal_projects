Discussion
=============================

Discussion
--------------------
The water classification results are generally verifiable, which demonstrates that the model has capability of distinguishing
different water quality levels.
However, there are still some results of water-quality classification are not well-correlated with monitoring site water-quality levels.

There are several possible reasons:

1. Landsat-8 images are various from scene to scene. Image quality is decided by the radiation intensity, imaging time, wind,
   cloud cover, etc. Scenes with same path are imaged in one day, but imaging time between adjacent paths is 7 days apart.
   Therefore, the predictions of water quality in the adjacent eastern and western overlapping area may have large difference.
2. The number of training samples are uneven distribution. III, IV, V and Inferior V samples are far more than I and II samples.
   Resulting in worse level prediction in some good water quality lakes. Data augmentation was used to expand I and II samples
   but not solve this issue.
3. Some uncertain monitoring sites with GCJ-02 coordinate system have coordinate offset of several meters to several hundred meters.
   This will bring extra errors and outliers to samples which make model training more difficult to converge.


Future Study
----------------------------

Transfer learning
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are mainly seven major river systems in China. We can freeze the base layers of the model
and test the transfer learning at other river systems.

Water bodies in same river systems have strong inner correlation because of similar geographic location
and surrounding environment.

.. figure:: ./imgs/water_basin.jpg
   :width: 550px
   :align: center


GaoFen 5 dataset
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Explore the relationship between hyper-spectral dataset and water quality.
GaoFen 5 hyperspectral images are currently processing for exploring the connection between spectral resolution and multi-water-quality parameters.
Band selection and compression of hyperspectral data are challenging tasks.

.. figure:: ./imgs/gaofen5.png
   :width: 550px
   :align: center

