# RoboND-Follow-Me-Project

# Network Architecture
In this project we train a Fully Convolutional Network (FCN) to be able to identify a target in a simulated drone environment. A FCN is similar to a Convolutional Neural Network (CNN) but adds Skip Connections which allow us to view the convolutional filters at different dimensions. This gives us a better spacial understanding of the inputs at higher resolutions.

## Skip Connections
Skip Connections are what give the FCN the ability to retain information from previous layers. With Skip Connections we can use the output from an encoder layer as the input for a decoder layer. This allows the model to learn from multiple resolutions which helps it retain details that could have been lost. Thus increasing our accuracy on our segmentation!

# Model

I decided to use a filter of 24 and created 3 encoder layers, 1 convolutional layer, and 3 decoder layers. I created 3 encoder and decoder layers because I felt that a size of 40x40 would be to large to catch some of the finer features. So this brought down the output size to 20x20. 
