# Image-to-Image-Translation-in-Keras

This is an attempt to code the [Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004) paper in Keras.

It's already been [implemented in Torch/Lua](https://github.com/phillipi/pix2pix) but since I'm on Windows and can't use that environment I ended up trying to write it in Keras/Theano.

## Issues

1. Since Deconvolutions have some problems in the Theano/Keras Implementation (which have been discussed [here](https://github.com/fchollet/keras/issues/3371)) I had to use something else and simpler (Memory constraints) and ended up using UpSampling2D. This seems to have harsh effects on the Generation process.

2. For the cGAN network which has 2 terms in its Objective I ended up implementing a 2-Output Discriminator, one of which outputs the usual `binary-crossentropy` loss and the other outputs an `MAE` L1 loss. I'm not sure if this is the best way to model the network but I couldn't find any other way to model the Objecitve. Here's the Objective:

![alt text](https://github.com/Neltherion/Image-to-Image-Translation-in-Keras/blob/master/Images/Capture.PNG "Objective Function for the Paper")


3.