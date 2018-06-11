# RoboND-Follow-Me-Project

## Network Architecture
In this project we train a Fully Convolutional Network (FCN) to be able to identify a target in a simulated drone environment. A FCN is similar to a Convolutional Neural Network (CNN) but adds Skip Connections which allow us to view the convolutional filters at different dimensions. This gives us a better spacial understanding of the inputs at higher resolutions.

### Skip Connections
Skip Connections are what give the FCN the ability to retain information from previous layers. With Skip Connections we can use the output from an encoder layer as the input for a decoder layer. This allows the model to learn from multiple resolutions which helps it retain details that could have been lost. Thus increasing our accuracy on our segmentation!

## Model

I decided to use a filter of 24 and created 3 encoder layers, 1 convolutional layer, and 3 decoder layers. I created 3 encoder and decoder layers because I felt that a size of 40x40 would be to large to catch some of the finer features. So this brought down the output size to 20x20. 

![Model](/images/FCN_model.jpg)
![Shape Data](/images/FCN_model_shape.jpg)

## Network Parameters

I lost the data I had on some of the models, including some images, but I initially started by tweeking the learning rate. The initial learning_rate was 0.01 and after manually testing it a few times I got 0.004 and 0.003 to be the most accurate. I started the batch_size at 32 and settled on 128 as being big enough for a stable amount of data. I felt that the smaller batch sizes would be less consistent in training and increase the validation loss. I initially set the number of epochs to 400 but quickly realized that it would take to long to iterate that many times, as well as after about 100 epochs it starts to stagnate and you see very little change. I set the steps_per_epoch to be the number of images / batch size. I increased the number of workers to 8 just to speed up the learning time.

These are the current parameters I got to.

learning_rate = 0.004  
batch_size = 128  
num_epochs = 100  
steps_per_epoch = 32  
validation_steps = 50  
workers = 8

![Training Curve](/images/training_curve.png)

## Training

I trained my network using the AWS Udacity Robotics EC2 instance. This network was only trained on humans and able to target the specific person that we trained. If we should images of animals or vehicles it would not be able to detect them accurately. We would have to retrain the model to look for these objects. We would also want to change the model to be able to tell us what we are identifying.
