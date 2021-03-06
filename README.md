# Picture-Framer-AI

## Introduction
This project arises as a real need for businesses that sell different types of paintings and frame images. In a simple way, so that a client can decide between one or another, only the corners of the picture are taken and compared.
By using **Deep Learning**, integrated into a mobile application, it is possible to take a photo, choose a frame and apply it to the image. In this way it is possible to see it completely and quickly, adding value to the business.

In this case, to make the problem a little easier I have chosen a single applicable picture design. Other designs could be easily used by adding a label (which indicates what type of picture will be applied) together with the transfer learning technique: we would not need as much data as at the beginning.


## Development
For this task, we have used the **pix2pix model** which is a conditional generative adversary network (conditional Gan, cGan) used in Images Translation tasks. It requires a large number of pairs of photos, which is really complicated if done by hand with a camera. Therefore, I have made in a simulated way in the video game development program Unity. This has allowed the **procedural generation** of hundreds of examples that allow the network to learn the transformation of an image without a frame to one with a frame.

![In a single picture](https://raw.githubusercontent.com/danielallhoff/Picture-Framer-AI/master/raw_images/synthetic_transformation.PNG)


Specifically, in this simulation, the angle and distance to the image have been modified, including changes in the size of the frame so that it can be correctly generalized. To test it and to prove if it has achieved it correctly, I have made a real photo: an image with a real background. 


## Results

When trying the first training with a lack of data with only 10 samples of background and picture images, the results were really bad.

![In a single picture](https://raw.githubusercontent.com/danielallhoff/Picture-Framer-AI/master/raw_images/first_results/0.png)

However, as I started recollecting more backgrounds and pictures, the results on the synthetic images started to being promising. For example:

![In a single picture](https://raw.githubusercontent.com/danielallhoff/Picture-Framer-AI/master/raw_images/synthetic_test_transformation.jpg)

Finally, after the training on synthetic data, I recorded some real samples and tested the performance on real world data. The best result I got is:

![In a single picture](https://raw.githubusercontent.com/danielallhoff/Picture-Framer-AI/master/raw_images/real_test_transformation.PNG)



## Problems
At first, when I trained for a while, I didn't get good results. It seems that between the overfitting that has occurred and the little variability of background / image (I used at first only 10 images for the background and 10 for the image approximately) I have not managed to get good results: the transformation between artificiall images is learned. However, when trying it with images of the real world, the results were poor. One posible solution is the **combination of synthetic and real data pairs to the pix2pix model**. The problem is the time required to prepare the real data pairs.

Another problem in the project is with the use of the memory. When processing a lot of images in unity the RAM memory is overflown. It is required to efficiently manage the memory and sequently processing the images and not as the last step.



