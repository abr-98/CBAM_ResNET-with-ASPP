# CBAM_ResNET-with-ASPP
Convolutional Block Attention Module with ResNet block with interleaved Atrous Pyramidal Pooling for multiple dimension feature


Dataset: https://www.kaggle.com/c/rsna-pneumonia-detection-challenge/data

### Architecture

The proposed model has 4 layers followed by a dense layer and then the prediction layer. The layers has been devised with the ideas of convolutional block attention module combined with a ResNet block to avoid the vanishing gradient problem. The Convolutional block attention module has two different modules: Channel attention followed by Spatial Attention.

![CBAM_resnet](https://raw.githubusercontent.com/abr-98/CBAM_ResNET-with-ASPP/main/Models/Resnet%20CBAM%20block.png)

The above diagram represents the CBAM-Resnet unit

Following the CBAM block, the maxpooling layer for downsampling has been replaced by a more combination of maxpooling and average pooling layer. The maxpooling is responsible preserving the edge and border characteristics or sharper parts of the image features, while the average pooling carries forward a smoother and richer piece of information, even after downsampling. The feature maps so obtained are concatenated. The concatenated feature maps are passed through (1x1) convolutions, to reduce the number of channels to half, and carry the most important parts of the information forward. So, the final output after the layer is same as a Maxpool layer but it should me more robust analytically.

![Pooling_Layer](https://raw.githubusercontent.com/abr-98/CBAM_ResNET-with-ASPP/main/Models/Pooling%20Layer.png)

The above digram represents the pooling layer.

Apart from the pooling layers, ASPP or Atrous Spatial Pyramidal Pooling introduced in deeplabv2 has also been used in order to provide a multi-scale receptive field with reduced parameters, for robust feature extraction. The used dilation rates are: 2, 4, and 8.

![ASPP](https://raw.githubusercontent.com/abr-98/CBAM_ResNET-with-ASPP/main/Models/ASPP%20Block.png)

The final architecture:

![Final_module](https://github.com/abr-98/CBAM_ResNET-with-ASPP/blob/main/Models/Model%20.png)

The architecture has been trained with data augmentation in order to produce better results.



