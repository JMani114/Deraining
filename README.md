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

## Encoder Modification

<p align="justify">
Images are split into patches; each patch passes through a pretrained network truncated before the final tensor. Intermediate tensors are reassembled spatially and forwarded through the remaining blocks to yield a 7 × 7 × C tensor show in Fig. 6.
</p>

<p align="center">
  <img src="images/MOdified_encoder.png" alt="Modified_encoder" />
  <br>
  <em>Fig. 6. Modified encoder with patch processing..</em>
</p>

<p align="justify">
Patch processing raised validation accuracy and reduced epoch time versus classical scaling, notably for ConvNeXtSmall and EfficientNetB0 shown in Table 2.
</p>

**Table 2: Configuration comparison for different models.**

| Setup           |  VGG16  | ConvNeXtBase | ResNet50V2 |
|-----------------|--------:|-------------:|-----------:|
| VGG16           |  75.33% |    24.67%    |
| ResNet50        |  79.07% |    20.93%    |
| ConvNeXtSmall   |  89.85% |    10.15%    |
| EfficientNetB0  |  81.74% |    18.26%    |
| Xception        |  68.81% |    31.19%    |
