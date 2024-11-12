# Image-Colourization-Using-Pix2Pix-GAN


## Task
The task was to color Black and White Manga images using Deep Learning. So for this task I used Pix2Pix Unet Genrative Adverserial Networks (GAN) which has shown great results in the field of Image Colourization and Image Segmentation.


## Dataset
For this task I used Comic Style Manga Images, which was collected from the internet using python and web scapping. Since these images have copyright so I have not provided link to these images in this repository. The dataset consisted of 76,000 Coloured Manga Images.


## Procedure
* The first part is importing the libraries. For this task I used Keras Deep Learning Library because of its easy interface.

* Since the size of the Dataset is huge, so it is not possible to load the whole dataset in the memory at the same time. So I put all the images in one folder and stored the path to all the images in a list.

* Since the input to the model must be of the same size but out imges were of different sizes. So I defined a crop function which would first take a 1024x1024 crop from any random part of the image and then scale it down to 512x512, which can be fed as input to the model. 
      Problem with just taking a crop of size 512x512 is that the Manga images contain text block and if we take a crop of size 512x512 then in some of the images most part of the images consist of the text black, which is black and white and thus it will not provide any usefull training and only act as noice to the model.

* Then we define our Discriminator model with an input size of 512x512 and an output (patch size) of 16x16.
      The structure of out Discriminator is as below:
      
<img src='discriminator_model_plot.png' width=500 />
      
* Then we define our Generator model which is a U-Net model, which has an input size of 512x512x1 and an output size of 512x512x2.
      The Structure of out Generator model is a show below:
      
<img src='generator_model_plot.png' width=500 />
      
* Now we define our GAN model Combining both the discriminator and the generator models.
      Its Structure is as show below:
      
<img src='gan_model_plot.png' width=500 />
      
* Now I defined some custom fuction of loading the images as input and output as well as to summarize our results and also a custom training function to train our model. For the model instead of taking the grayscale as input and RGB image as output, I converted the RGB image to LAB image and then used the "L" part as input and "AB" part as the ouput of out model.

* Then we trained of our model on Nividia GPU for 4,00,000 iterations with a batch size of 1. (This training approxiamately took me 7 days on my Laptop's GPU)


## Results

<img src='Output Images/1.png' width=1000 />


<img src='Output Images/2.png' width=1000 />


<img src='Output Images/3.png' width=1000 />


<img src='Output Images/4.png' width=1000 />

