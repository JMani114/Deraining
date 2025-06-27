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

<p align="center">
  <img src="images/Network_Training_Accuracy.png" alt="Network Training - Accuracy" />
  <br>
  <em>Fig. 1. Training accuracy graph.</em>
</p>

<p align="center">
  <img src="images/Network_Training_Loss.png" alt="Network Training - Loss" />
  <br>
  <em>Fig. 2. Training loss graph.</em>
</p>


<p align="justify">
The LHP-Rain dataset is divided into training, testing, and validation folders, which enables the evaluation of accuracy and loss metrics during training. This allows measuring the network’s generalization capability on previously unseen data. These results are shown in Figures 3 and 4.
</p>

<p align="center">
  <img src="images/Network_Training_Validation_Accuracy.png" alt="Network Validation - Accuracy" />
  <br>
  <em>Fig. 3. Accuracy validation graph.</em>
</p>

<p align="center">
  <img src="images/Network_Training_Validation _Loss.png" alt="Network Validation - Loss" />
  <br>
  <em>Fig. 4. Loss validation graph.</em>
</p>

<p align="justify">
The validation folder, which contains 600 rainy images and 600 non-rainy images, was processed by the model. A sample of these images is shown in Fig. 5, where the comparisons between rainy and non-rainy images from this dataset are presented. Finally, Table 1 displays the accuracy and error rates achieved by each network.
</p>

<p align="center">
  <img src="images/Compative_of the_images.png" alt="Compative of the images" />
  <br>
  <em>Fig. 5. Image comparison, a) image with rain and b) image without rain.</em>
</p>

**Table 1: Classification accuracy on rainy vs. clean images.**

| Model           | Accuracy | Error   |
|-----------------|---------:|--------:|
| VGG16           |   75.33% |  24.67% |
| ResNet50        |   79.07% |  20.93% |
| ConvNeXtSmall   |   89.85% |  10.15% |
| EfficientNetB0  |   81.74% |  18.26% |
| Xception        |   68.81% |  31.19% |

## Patch Deraining in ECNet

<p align="justify">
In this section, a visual comparison of the results obtained by the different neural networks will be presented, showing the original rainy image, the clean reference image, and the inferred image.
</p>

### DRSformer

<p align="center">
  <img src="images/DRSformer.png" alt="DRSformer" />
  <br>
  <em>Fig. 6. Inference using the DRSformer network. a) Clean image (no rain); b) Image inferred by the network;c) Rainy image.</em>
</p>

<p align="center">
  <img src="images/MPRNet.png" alt="MPRNet" />
  <br>
  <em>Fig. 6. Inference using the MPRNet network. a) Clean image (no rain); b) Image inferred by the network;c) Rainy image.</em>
</p>

<p align="center">
  <img src="images/ECNet.png" alt="ECNet" />
  <br>
  <em>Fig. 6. Inference using the ECNet network. a) Clean image (no rain); b) Image inferred by the network;c) Rainy image.</em>
</p>

<p align="center">
  <img src="images/3x3.png" alt="3x3" />
  <br>
  <em>Fig. 6. Inference using the proposed 9-patch method. a) Clean image (no rain); b) Image inferred by the network;c) Rainy image.</em>
</p>

<p align="center">
  <img src="images/4x4.png" alt="4x4" />
  <br>
  <em>Fig. 6. Inference using the proposed 16-patch method. a) Clean image (no rain); b) Image inferred by the network;c) Rainy image.</em>
</p>

<p align="center">
  <img src="images/8x5.png" alt="8x5" />
  <br>
  <em>Fig. 6. Inference using the proposed 40-patch method. a) Clean image (no rain); b) Image inferred by the network;c) Rainy image.</em>
</p>
