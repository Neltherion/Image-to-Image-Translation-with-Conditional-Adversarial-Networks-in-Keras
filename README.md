# Image-to-Image-Translation-in-Keras

This is an attempt to code the [Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004) paper in Keras.

It's already been [implemented in Torch/Lua](https://github.com/phillipi/pix2pix) but since I'm on Windows and can't use that environment I ended up trying to write it in Keras/Theano.

## Issues

1. Since Deconvolutions have some problems in the Theano/Keras Implementation (which have been discussed [here](https://github.com/fchollet/keras/issues/3371)) I had to use something else and simpler (Memory constraints) and ended up using UpSampling2D. This seems to have harsh effects on the Generation process.

2. For the cGAN network which has 2 terms in its Objective I ended up implementing a 2-Output Discriminator, one of which outputs the usual `binary_crossentropy` loss and the other outputs an `MAE` L1 loss. I'm not sure if this is the best way to model the network but I couldn't find any other way to model the Objecitve. Here's the Objective:

![alt text](https://github.com/Neltherion/Image-to-Image-Translation-in-Keras/blob/master/Images/ObjectiveFunction.PNG "Objective Function for the Paper")

3. Somehow the network seems to not function properly as it should. the &#955; which is 100 seems to result in a network which emphasizes `L1` loss more than the `binary_crossentropy` loss and results in unreal images.

## Output

The model's output is not promising. here's what the paper's code generates:

![alt text](https://github.com/Neltherion/Image-to-Image-Translation-in-Keras/blob/master/Images/PaperOutput.png?raw=true "The Paper's Output")

and here's the Model's output:

![alt text](https://github.com/Neltherion/Image-to-Image-Translation-in-Keras/blob/master/Images/OurModelOutput.png?raw=true "The Model's Output")

I'm open to every advice on how to improve this model and make it a useful cGAN.
Unfortunately there aren't many other cGAN implementations in Keras around and I'm not even sure if this model is properly designed.



