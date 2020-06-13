Methods
========================

CNN architecture
--------------------------

Our CNN architecture has the following characteristics:

 - Small receptive field
 - Pooling layers were replaced by a convolutional layer with increased stride.
 - Introduced 1x1 Conv layers to increase number of feature maps.
 - Adam was used as the optimization algorithms.
 - Cross-entropy loss was used as criterion.
 - Used lr_scheduler.ReduceLROnPlateau class to dynamically adjust the learning rate.

.. note:: 1. There is no need for a large receptive field because the small input patch size and less texture features in water bodies.
          2. No pooling layers because I want to weaken the effect of spatial texture relationship and emphasize the importance of spectral information.

.. csv-table:: CNN architecture
   :header: "Process", "Parameters", "Description"
   :widths: 20, 20, 40

   Input,(40 40 12),Input patches size
   Conv2D,(64 3 3),Number of filters and filter size
   Stride,2,Size of stride
   BatchNorm, ,Accelerate convergence
   Activation,ReLU,Activation function
   Dropout,0.5,Fraction of the input units to drop
   Output,(20 20 64),Output size
    , ,
   Conv2D,(128 3 3),Number of filters and filter size
   Stride,2,Size of stride
   BatchNorm, ,Accelerate convergence
   Activation,ReLU,Activation function
   Dropout,0.5,Fraction of the input units to drop
   Output,(10 10 128),Output size
    , ,
   Conv2D,(256 3 3),Number of filters and filter size
   Stride,2,Size of stride
   BatchNorm, ,Accelerate convergence
   Activation,ReLU,Activation function
   Dropout,0.5,Fraction of the input units to drop
   Output,(5 5 256),Output size
    , ,
   Conv2D,(512 1 1),Number of filters and filter size
   BatchNorm, ,Accelerate convergence
   Activation,ReLU,Activation function
   Output,(5 5 512),Output size
    , ,
   Dense,2048,Fully connected layer size
   Activation,ReLU,Activation function
   Dense,6,Number of classes
   Activation,Softmax,Activation function

The network was implemented by Pytorch and training on Titan 2080ti GPU.

LightGBM(LGB)
---------------------------------
LightGBM is a relatively new gradient boosting framework. Compare to the other gradient classifier,
LightGBM train much faster because of its distributed design and easy to get high accuracy with the following characteristics:
 - Decision tree algorithm based on Histogram
 - Histogram subtraction for further speedup
 - Leaf-wise growth strategy with depth limitation
 - Sparse Optimization

https://github.com/microsoft/LightGBM


Hyperopt
-------------------
Hyperopt is a hyperparameters optimization function which can find the best value in a range of searching space.
By providing more information about where your function is defined, and where you think the best values are, you allow algorithms in hyperopt to search more efficiently.

https://github.com/hyperopt/hyperopt

In the LGB official documentation, optuna is recommended as the hyperparameters optimization packages. Compared with the
hyperopt method, they use the same strategy based on a Bayesian optimization algorithm. Optuna introduce pruned trials method
which can early stop the attempts with poor results to accelerate the training process.

Optuna will be tested in this project in the future. Here we still use Hyperopt package for hyperparameters optimization.

