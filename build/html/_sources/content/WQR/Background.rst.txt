Background
===================

Multispectral data (Landsat-8 and Sentinel-2) contain a wealth of spectral information,
which has been widely used in water quality monitoring.
The water quality indicators such as chlorophyll-a (Chl-a), turbidity and suspended solids (TSS)
are often estimated from remote sensing data for their active optical properties. As shown in figure:

.. figure:: ./imgs/remote_sensing_data_source.png
   :width: 650px
   :align: center

`reference <../../_static/_asset/Water_quality_monitoring_and_evaluation_using_remote_sensing_techniques_in_China_a_systematic_review.pdf>`_.

However, the retrieval of other non-optical parameters, such as total nitrogen (TN), total phosphorus (TP),
chemical oxygen demand (COD), dissolved oxygen (DO), etc, is more difficult than the optical parameters.

Water quality level is a composite index for evaluating water quality based on multiple water-related parameters.
According to Chinese water quality assessing standard GB3838-2002, the surface water quality in China
can be divided into 6 levels: from the best to the worst are I, II, III, IV, V and Inferior V. Each level corresponds to a
certain range of water quality parameters.

Single-factor method is used to classify water quality, which means a parameter that exceeds its corresponding criterion
with the highest proportion is selected for water-quality-level classification. Briefly speaking, water quality level is
determined by the worst parameter content. For example, if a lake with I level in COD, TP, DO parameters and V level
in TN parameter, the water quality level of this lake is V.

.. figure:: ./imgs/GB3838-2002.png
   :width: 650px
   :align: center

If the water parameter exceeds the level V limit, the water body will be evaluated as Inferior V, including
black odorous water.

In a recent study, Fangling Pu el from Wuhan University used Landsat8 images and ground monitoring sites data, successfully
trained the water quality classification model of Chaohu lake based on CNN, then transferred learning to Erhai and achieved reasonable results.
https://www.mdpi.com/2072-4292/11/14/1674/htm

This article explored the possibility of directly categorizing water quality level using medium-resolution multispectral images.
However, it is still restrained in a small areas of inland lakes.
Here we hope to expand this idea to some extent, mainly focus on the two following directions to explore its universal possibility:
 - Not limited to specific lakes or a small amount of data for training, but extended to both large rivers and lakes.
 - Add more features such as band combinations and band ratios as input.
 - Alter CNN architecture.