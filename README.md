# Image_Denoising_autoencoder

## About:
This project is build with convolutional autoencoder using Keras on Tensorflow. MNIST dataset of hand written digits is used.

## Data:
* Since MNIST dataset of hand written digits has clean images, we generate synthetic gausian noise through np.random.normal, add it to the images.
* After adding the noise, values in image matrix are no longer between 0 & 1. Hence, we clip the images between 0, 1

![Noise Induced Images](/Images/Noice_Images.png)

## Autoencoder:

Autoencoder create a bottle neck effect which result in compression of the data and then restores back to its original data. There may be loss in data in this process which can be seen in the smoothened images at the end of this project.

### Model Summray:

~~~
                Model: "model_1"
                _________________________________________________________________
                Layer (type)                 Output Shape              Param #   
                =================================================================
                input_1 (InputLayer)         (None, 28, 28, 1)         0         
                _________________________________________________________________
                conv2d_1 (Conv2D)            (None, 28, 28, 32)        320       
                _________________________________________________________________
                max_pooling2d_1 (MaxPooling2 (None, 14, 14, 32)        0         
                _________________________________________________________________
                conv2d_2 (Conv2D)            (None, 14, 14, 32)        9248      
                _________________________________________________________________
                max_pooling2d_2 (MaxPooling2 (None, 7, 7, 32)          0         
                _________________________________________________________________
                conv2d_3 (Conv2D)            (None, 7, 7, 32)          9248      
                _________________________________________________________________
                up_sampling2d_1 (UpSampling2 (None, 14, 14, 32)        0         
                _________________________________________________________________
                conv2d_4 (Conv2D)            (None, 14, 14, 32)        9248      
                _________________________________________________________________
                up_sampling2d_2 (UpSampling2 (None, 28, 28, 32)        0         
                _________________________________________________________________
                conv2d_5 (Conv2D)            (None, 28, 28, 1)         289       
                =================================================================
                Total params: 28,353
                Trainable params: 28,353
                Non-trainable params: 0
~~~

## Denoised Images:

* As mentioned earlier the restored images has some bluriness to it which is due to loss of data from autoencoders.

![Noise Removed](/Images/Noice_Restored.png)


