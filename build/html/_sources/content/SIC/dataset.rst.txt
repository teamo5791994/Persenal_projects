Dataset
==============================

MWR SIC product
------------------------
Here we use sea ice map calculated from AMSR2 19,37GHz data using Comiso bootstrap and Bristol algorithm.
This product is the daily average of SIC map with 25km resolution and can be download from
http://data.ceda.ac.uk/neodc/esacci/sea_ice/data/sea_ice_concentration/L4/amsr/25km/v2.1/NH

An example of SIC product is shown below:

.. figure:: ./images/SIC_prod.png
    :width: 550px
    :align: center

This product shows the ice percentage distribution of the Arctic area.

Passive microwave radiometer data can automatically generate the product but limited by its coarse resolution.
To show more details in the sea ice map, SAR data has been used in sea ice monitoring.

SAR Data
----------------

The Dual (HH and HV) PolSAR (Extra Wide)EW (Ground Range Detective Medium resolution)GRDM
data with 40m x 40m pixel spacing is used in this study, which can be downloaded from
https://scihub.copernicus.eu/dhus/#/home

.. figure:: ./images/SAR_exp.png
    :width: 550px
    :align: center

There are some small problems of origin data, such as speckle noise, incidence angle dependence in HH polarization,
scalloping, banding effects in HV polarization, etc. This series of data problems can be partially removed by
such as speckle filtering, thermal noise reduction and other data pre-processing methods.

The origin SAR images were cut the upper part to remove the scalloping effect.

.. csv-table:: Sample Table
   :header: "Sample", "Scene ID", "Image Size"
   :widths: 15, 40, 20

   training,20160711T161822_20160711T161922,9600x6000
   training,20160712T165903_20160712T170003,9000x6600
   training,20160714T164226_20160714T164326,9600x7200
   training,20160715T172314_20160715T172414,9600x7200
   training,20160716T162628_20160716T162728,9600x6600
   training,20160723T161823_20160723T161923,9000x6000
   training,20160724T165904_20160724T170004,9600x5400
   training,20160726T164226_20160726T164326,9000x6600
    , ,
   validation,20160727T172314_20160727T172414,9600x6000
   validation,20160705T072014_20160705T072114,9000x6600
    , ,
   test,20160706T080114_20160706T080214,9000x5400
   test,20160722T072926_20160722T073026,9000x7200




