# Patch-Based Local Deraining for High-Resolution Images

## Abstract
<p align="justify">
This project focuses on the development of a method to process high-resolution images (HD, Full HD, 4K, and 8K) using neural networks dedicated to deraining. Its goal is to reduce or eliminate the distortions present in images captured under rainy conditions. Although there are currently numerous neural models—from convolutional neural networks (CNNs) and generative adversarial networks (GANs) to transformers—they all face challenges when working with very high-resolution images due to the substantial computational power required. While images can be downscaled to lower resolutions, doing so results in the loss of relevant information. Therefore, a method has been devised that consists of dividing the image into patches, processing each patch with the network to remove rain, and then recombining them to reconstruct the original image.
</p>

## Objetive
<p align="justify">
Develop a deep network for single-image deraining (SID) at high resolution, significantly improving visual quality while matching or surpassing state-of-the-art performance with-out relying on costly hardware.
</p>

## Rain Classification
<p align="justify">
Most convolutional neural networks dedicated to deraining adopt an autoencoder structure, consisting of an encoder and a decoder. Therefore, it was essential to select a feature extractor (encoder) capable of detecting rain. To this end, well-established architectures—VGG16, ResNet50, ConvNeXtSmall, EfficientNetB0, and Xception—were evaluated to determine which one best detects rain disturbances.
Below are the training graphs for the selected networks, showing the Accuracy and Loss metrics. All were trained on the same LHP-Rain dataset.
</p>
![Network Training - Accuracy](Deraining/images/Network_Training_Accuracy.png)

