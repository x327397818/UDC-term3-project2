[//]: # (Image References)

[Loss_Epochs]: ./result/Loss_Epoch.PNG "Loss_Epochs"

# Semantic Segmentation
### Introduction
In this project, the tasl os tp label the pixels of a road in images using a Fully Convolutional Network (FCN).

### Setup

##### Frameworks and Packages
Packages needed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
 - [Python Image Library (PIL)](https://pillow.readthedocs.io/)

##### Dataset
[Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Implement
A pre-trained VGG-16 network is used. Skip layers are added by following steps,

 - 2x upsampled layer 7 (with a stride 2 transposed convolution)
 - Add above with layer 4 and then do 2x unsample(with a stride 2 transposed convolution)
 - Add above with layer 3 and then do 8x unsample(with a stride 8 transposed convolution)

#### Optimizer
Adam optimizer is used.

#### Training hyperparameters
 - keep_prob: 0.5
 - learning_rate: 0.00001
 - epochs: 8, 16, 32, 64, 128
 - batch_size: 5
 
#### Result
Video made from test result images can be found [here](https://github.com/x327397818/UDC-term3-project2/blob/master/result/128.mp4)

Here is the charts shows the relationship of loss over epochs.

![alt text][Loss_Epochs]

From the chart above, it is easy to tell loss decrease over epochs. But after around epochs 60, the decreasing speed is very low.

### Run 
Run the following command to run the project:
```
python main.py
```
Run the following command to generate video from test result images:
```
python video.py [test result folder]
```
