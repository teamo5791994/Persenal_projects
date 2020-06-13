Background
===================

1. Synthetic aperture radar (SAR) contains a wealth of information about sea ice conditions.
#. It is difficult to develop reliable algorithms to calculate or predict sea ice information.
#. SIC products can be derived from MWR data automatically, with highest 3-5 km resolution (89Hz).
   https://uwaterloo.ca/vision-image-processing-lab/publications/sea-ice-concentration-estimation-satellite-sar-imagery-using
#. Early research used CNNs to predict SIC based on SAR images and Ice charts (Lei Wang 2017).
   However, it is time-consuming to collect the corresponding Ice charts for the training datasets.

The main target of this experiment is to develop and test an automatically
high-resolution SIC estimation method based on SAR data and MWR products.