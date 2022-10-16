# **Captioning of Remote Sensing Images**

## Abstract

The inspiration for this project is from DALL-E. Albeit, we are not trying to generate image from text but rather we generate text for the given image or in other words, caption images .Here, we build a transformer consisting of a CNN encoder and a RNN decoder. We focus on captionning Remote Sensing Images, mainly due to the fact that they have a wider use case. For instance, Warning about a forest fire. Though we can achieve that by just using a classifier, this is much more fun. 

## Dataset

The dataset which we use here is the [RSICD](https://github.com/201528014227051/RSICD_optimal). RSICD is used for remote sensing image captioning task. More than ten thousands remote sensing images has been collected from Google Earth, Baidu Map, MapABC, Tianditu. The images are fixed to 224X224 pixels with various resolutions. The total number of remote sensing images are 10921, with five sentences descriptions per image.

## Preprocessing

The prepping of data is minimal, due to the fact that all the images are in a standard size of (224,224,3). But due to the large amount of data, we build a TensorFlow input pipeline to prevent any sort of disk overloading. As for the text, standard stemming is done, any sort of punctuations are removed. We also transform it into a standard form of "<'start'> *the sentence* <'end'>." 

## Model

**CNN** is used as the encoder, we use the pretrained InceptionV3 model with *imagenet weights*  to extract features of the image. We change the 4 dimensional vector into 3 dimensional in order to feed it into the **RNN** decoder. We make use of **Bahdanau Attention** which is a type of a local attention.

## Results

The results for fairly simple sentences are promising, but as the sentences get more complicated. The predictions are quite different from the actual value.

For instance,

![y_1](https://user-images.githubusercontent.com/57098615/196037209-b9523ec4-22a3-40ed-8fb9-ad82f03161a6.png)

the above result is quite promising.

And here,

![y_2](https://user-images.githubusercontent.com/57098615/196037303-30bcd228-281b-4195-9894-2f637fdaa8a8.png)

the above predictions is somewhat correct.

But however,

![y_3](https://user-images.githubusercontent.com/57098615/196037362-d9c59805-21fd-43f2-b701-65f26026de9b.png)

this prediction is quite incorrect.

## Conclusion

The transformer works great for simple sentences and fairly well for intermediate sentences. But however, it struggles to accurately predict complex sentences. A main reason for this might be the fact that InceptionV3 with *imagnet weights* are used, which are trained on images quite dissimilar to remote sensing data. Hence, for future works, the CNN encoder will be completely trained on remote sensing data.
