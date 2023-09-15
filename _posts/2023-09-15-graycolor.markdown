---
layout: single
title:  "Gray2Color"
date:   2023-09-15 11:21:00 -0600
categories: projects
permalink: /projects/graycolor
read_time: true
---
Gray2Color (I know, a very originally name) is a convolutional neural network that is tasked with colorizing grayscale images. It was built in Python using the Pytorch and Numpy libraries.
The [dataset](https://www.kaggle.com/datasets/aayush9753/image-colorization-dataset) I used came from Kaggle and consisted of many color images and their grayscale counterparts. I resized these
images to a *224x224* resolution for use in my network. 

### Spacing Out

When you are working with digital images, it is important to consider how you want to represent the colors in the images (or the "color space"). At first I used the usual RGB color space,
where each pixel's red, green, and blue values were stored. However some of my initial testing with RGB did not give good results. I did some further research and discovered and different color space,
CIELAB was often used in neural network tasks. CIELAB represents colors using three channels: ** L **(black-white), ** a ** (green-purple), and **b** (blue-yellow). As the **L** channel was already given,
my neural network would only need to predict two channels, as opposed to three if I were using the RGB color space. I hoped this would mean the training time on the neural network would be
reduced while its accuracy would increase.



### Data Transfer

I tried many different CNN architectures varying the size of each layer, the number of layers, the activation function between layers, etc. While they gave okay-ish results, training all these
models took a lot of time and the results weren't as spectacular as I hoped they would be. Additionally I was running into issues where my model was getting too big. Juypter Notebook was having trouble
fitting all of the data into my GPU's 6GB of VRAM. This lead to frequent crashes from out of memory errors!

At this point I deicded to try using *Transfer Learning*, modifying and specializing another pretrained network, for my task. After looking at the pretrained networks provided by the PyTorch library 
I decided on using [ResNet](https://arxiv.org/abs/1512.03385) as it had good accuracy while also being fairly lightweight. As a result my final model consisted of a "adapter" to convert the image
data into a format that ResNet could expect, a small portion of ResNet that I finetuned for my task, and finally a "decoder" that converted ResNet's output back into a format that could be
used to represent digital images in the CIELAB color space.

{% include figure image_path="/assets/images/graycolor/architecture.png" alt="Gray2Color architecture" caption="A simplified represention of what the Gray2Color network looks like"%}

### Colorful Results

Even though the final results of my network weren't as good as I expected, I still found them to be pretty interesting. The network did a good job at colorizing large sections of the
image that had similar colors such as foliage, water, or the sky. However it did worse on small details and on objects with many possible colors such as cars, clothing, etc.

---

{% include figure image_path="/assets/images/graycolor/average_example.png" alt="A typical result" caption="An average result. While the sky was partially colored, the skater was not"%}
{% include figure image_path="/assets/images/graycolor/bad_example.png" alt="A bad result" caption="A bad colorization. I think the model mistook bread for grass in this one"%}
{% include figure image_path="/assets/images/graycolor/good_example.png" alt="A good result" caption="A good colorization. Sky and trees are easy for my model to colorize"%}

---

I've noticed that the model often selects to color parts of the image it "doesn't understand" a beige color. I believe this is a result of neural network training teaching the model
to minimize loss. Essentially the model wants to be as close as possible, mathmatically speaking, to the true result. As such the model will choose a mathmatically average beige
color so it can be as "least wrong" as possible, even though it isn't the correct color.

### Further Specialization

As an experiment, I wanted to see what would happen if I further specialized my network. This meant instead of having it colorize general images, I would have it colorize images
of a specific type of object. I downloaded [another dataset](https://www.kaggle.com/datasets/jorgebailon/fruits-vegetables) from Kaggle, this time of fruit. I then took only the images
of apples from this dataset, resized them, generated grayscale versions, and used this to train the network.

---

{% include figure image_path="/assets/images/graycolor/apple_red.PNG" alt="Colorizing red apples" caption="The apple colorizing network does a good job with red apples"%}
{% include figure image_path="/assets/images/graycolor/apple_green.png" alt="Colorizing green apples" caption="But not so much with green apples..."%}

---

Again the results here were quite interesting. The model learned that apples are red, and colorized red apple successfully. However, it also "believes" that *all* apples are red, even
if they are green or yellow apples. As such it will color all apples red regradless of their actual color. It also had a tendency to color non-apple objects with a red tint, making
the results somewhat reminiscent of a style transfer neural network.

