# **Captioning of Remote Sensing Images**

## Abstract

The inspiration for this project is from DALL-E. Albeit, we are not trying to generate image from text but rather we generate text for the given image or in other words, caption images .Here, we build a transformer consisting of a CNN encoder and a RNN decoder. We focus on captionning Remote Sensing Images, mainly due to the fact that they have a wider use case. For instance, Warning about a forest fire. Though we can achieve that by just using a classifier, this is much more fun. 

## Dataset

The dataset which we use here is the [RSICD](https://github.com/201528014227051/RSICD_optimal). RSICD is used for remote sensing image captioning task. More than ten thousands remote sensing images has been collected from Google Earth, Baidu Map, MapABC, Tianditu. The images are fixed to 224X224 pixels with various resolutions. The total number of remote sensing images are 10921, with five sentences descriptions per image.

## Preprocessing

The prepping of data is minimal, due to the fact that all the images are in a standard size of (224,224,3). But due to the large amount of data, we build a TensorFlow input pipeline to prevent any sort of disk overloading. As for the text, standard stemming is done, any sort of punctuations are removed. We also transform it into a standard form of "**<start>** *the sentence* **<end>**". 
