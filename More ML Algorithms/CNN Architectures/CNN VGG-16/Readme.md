## Architecture
-The input to the network is an image of dimensions (224, 224, 3).
-The first two layers have 64 channels of 3*3 filter size and same padding. Then after a max pool layer of stride (2, 2), two layers have convolution layers of 256 filter size and filter size (3, 3).
-This followed by a max-pooling layer of stride (2, 2) which is same as the previous layer. Then there are 2 convolution layers of filter size (3, 3) and 256 filter.
-After that, there are 2 sets of 3 convolution layer and a max pool layer. Each has 512 filters of (3, 3) size with the same padding.
-This image is then passed to the stack of two convolution layers.
-In these convolution and max-pooling layers, the filters we use are of the size 3*3 instead of 11*11 in AlexNet and 7*7 in ZF-Net. In some of the layers, it also uses 1*1 pixel which is used to manipulate the number of input channels. There is a padding of 1-pixel (same padding) done after each convolution layer to prevent the spatial feature of the image.
-After the stack of convolution and max-pooling layer, we got a (7, 7, 512) feature map. We flatten this output to make it a (1, 25088) feature vector.
-After this there are 3 fully connected layer, the first layer takes input from the last feature vector and outputs a (1, 4096) vector, the second layer also outputs a vector of size (1, 4096) but the third layer output a 1000 channels for 1000 classes of ILSVRC challenge, then after the output of 3rd fully connected layer is passed to softmax layer in order to normalize the classification vector

### Loading 8 sample images from the disk
-Converting the image to array and then reshaping it.
-After performig the above steps, we are pre-process it and then predicting the output.
-top=2 in decode_predictions() function means which we are taking top 2 probability values for the particular prediction.

