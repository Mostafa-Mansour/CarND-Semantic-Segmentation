# Semantic Segmentation
### Introduction
In this project, you'll label the pixels of a road in images using a Fully Convolutional Network (FCN).

### Setup
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
##### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

## Implementation
1. The following steps are followed to implement Fully Connected Network (FCN):
* The weights and the model of VGG16 are restored.
* The outputs of the interesting layers (layer_3,layer_4,layer_7) are saved to be used later.
* A 1X1 convolution has been implemented to the output of the interesting layers.
* Layer_7 was upsampled using a stride of (2,2) ---> upsampled_layer_7
* the upsampled_layer_7 was fused with layer_4 ----> fused_7_4
* the fused_7_4 was upsampled with stride of (2,2) --> upsampled_7_4
* The upsampled_7_4 was fused with the output of layer_3 ---> fused_7_4_3
* The output of fused_7_4_3 was upsampled with stride of (8,8) to get the final output (semantic segmented image)

2. The Network was trained using Adam optimizer with softmax cross entropy cost function.

3. The learning rate was 0.0009 and a dropout of 0.5 was used.



