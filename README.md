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
Most convolutional neural networks dedicated to derainization adopt an autoencoder structure, composed of an encoder and a decoder. Therefore, it was essential to select a feature extractor (encoder) capable of detecting rainfall. To do so, established architectures (VGG16, ResNet50, ConvNeXtSmall, EfficientNetB0, and Xception) were evaluated to determine which one best detects rainfall disturbances. The training graphs of the selected networks, showing the Accuracy and Loss metrics, are shown in Fig. 1 and Fig. 2 below. All of them were trained on the same LHP-Rain dataset.
</p>

![Network Training - Accuracy](images/Network_Training_Accuracy.png)

*Fig. 1.* Training accuracy graph.

![Network Training - Loss](images/Network_Training_Loss.png)

*Fig. 2.* Training loss graph.


<p align="justify">
The LHP-Rain dataset is divided into training, testing, and validation folders, which enables the evaluation of accuracy and loss metrics during training. This allows measuring the network’s generalization capability on previously unseen data. These results are shown in Figures 3 and 4.
</p>

<p align="center">
![Network Validation - Accuracy](images/Network_Training_Validation_Accuracy.png)

*Fig. 3.* Accuracy validation graph.

![Network Validation - Loss](images/Network_Training_Validation_Loss.png)

*Fig. 4.* Loss validation graph.
</p>
