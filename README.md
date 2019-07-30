# Semantic Segmentation
### Introduction
In this project, the pixels of a road in images are labelled using a Fully Convolutional Network (FCN).

### Setup
##### GPU
`main.py` will check to make sure a GPU is used. 
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)

You may also need [Python Image Library (PIL)](https://pillow.readthedocs.io/) for SciPy's `imresize` function.

##### Dataset
The [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) is downloaded from [here](http://www.cvlibs.net/download.php?file=data_road.zip) and extracted into the `data` folder.  This will create the folder `data_road` with all the training a test images. I have not uploaded those images here.

### Start
##### Run
Run the following command to run the project:
```
python main.py
```

### Submission
1. All the unit tests have passed.
3. I have submitted the following files in the repo.
 - `helper.py`
 - `main.py`
 - `project_tests.py`
 - Newest inference videos in `results` folder [here](/results)
 
 
### Tips
- The link for the frozen `VGG16` model is hardcoded into `helper.py`.  The model can be found [here](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/vgg.zip).
- The model is not vanilla `VGG16`, but a fully convolutional version, which already contains the 1x1 convolutions to replace the fully connected layers. Please see this [post](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/forum_archive/Semantic_Segmentation_advice.pdf) for more information.  A summary of additional points, follow. 
- The original FCN-8s was trained in stages. The authors later uploaded a version that was trained all at once to their GitHub repo.  The version in the GitHub repo has one important difference: The outputs of pooling layers 3 and 4 are scaled before they are fed into the 1x1 convolutions.  As a result, some students have found that the model learns much better with the scaling layers included. The model may not converge substantially faster, but may reach a higher IoU and accuracy. 
- When adding l2-regularization, setting a regularizer in the arguments of the `tf.layers` is not enough. Regularization loss terms must be manually added to your loss function. Otherwise regularization is not implemented.
