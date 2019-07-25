# DCGAN - just for kicks (as the cool kids tend to say)
## A deep convolutional generative adversarial network that produces plausible images of basketball shoes

This is an experiment for producing completely artificial images or shoes through a DCGAN, based on [the wonderful repo](https://github.com/CShorten/BballShoesDCGANs/blob/master/Kicks_DCGAN.ipynb) and [blog post](https://medium.com/@connorshorten300/generating-basketball-shoes-with-dcgans-6cd72d521c01) by Dr. Connor Shorten (Github: [@CShorten](https://github.com/CShorten)). Rather than use the shipped datasets like MNIST and CIFAR-10, Connor uses a custom dataset of basketball shoes, which I sneakily found [hiding on his profile page](https://github.com/CShorten/NIKE_vs_ADIDAS) in [training](https://github.com/CShorten/NIKE_vs_ADIDAS/tree/master/TRAIN) and [testing](https://github.com/CShorten/NIKE_vs_ADIDAS/tree/master/TEST) sets. 

His project uses a number of shoe images based on the same general style, with varying colors, which he trains a DCGAN on to produce custom designs. It's a really neat concept, and a much more practical example for grabbing real-world data that needs to be preprocessed and massaged. The source images also were larger and in color, as opposed to MNIST's (50000 28, 28, 1) shape. It wasn't at all hard.

So as a clever twist to get the bespoke dataset into a format that the DCGAN expects - a NumPy shape of (140, 45, 45, 3) - the images needed to be decomposed to their raw pixel values, and then persisted by storing them as an array in NumPy's uncompressed NPZ format. The 140 images Connor uses with both the testing and training sets combined come out to 1.6MB on disk.

I upscaled the demo to Google Colab to make use of cloud GPUs and make the machine learning run consist of many more epochs, hopefully to get both the DCGAN's generator and discriminator models to converge (or get close to it). I used Google Drive File Stream to access the .npz file on disk in my share space. 
