## White Blood Cell Classification

### Overview

Frequently medical tests need to count the number and type of white blood cells present in a blood sample.  It would be advantageous to build a computer algorithm that could identify the type of white blood cell from an image.  This project will look to write a computer algorithm to identify the cell type. 

White bloods cells can be classified as one of the following:  

<table>
  <tr>
    <th>Family:</th>
    <th colspan="3">Granulocyte</th>
    <th>Lymphocyte</th>
    <th>Monocyte</th>
  </tr>
  <tr>
    <th>Subtype:</th> 
    <th>Basophil</th>
    <th>Eosinophil</th>
    <th>Neutrophil</th>
    <th></th>
    <th></th>
  </tr>
  <tr>
    <td></td>
    <td><img src="Presentation/images/besophil.jpg" width=200px></td>
    <td><img src="Presentation/images/eosinophil.jpg" width=200px></td>
    <td><img src="Presentation/images/neutrophil.jpg" width=200px></td>
    <td><img src="Presentation/images/lymphocyte.jpg" width=200px></td>
    <td><img src="Presentation/images/monocyte.jpg" width=200px></td>
  </tr>
  <tr>
    <td></td>
    <td>Nucleus divided into 2-5 segments.</td>
    <td>Nucleus divided into 2 segments.</td>
    <td>Nucleus divided into 2-5 segments.</td>
    <td>Nucleus large, round or oval.</td>
    <td>Nucleus single segment, <p>shaped as kidney bean.</td>
  </tr>
</table>

### Business Problem
Does a **pretrained convolutional layer** with a **neural net** improve the classification of white blood cell types over **manual feature extraction** with a **decision tree**?

### Results

The neural net offers a mixed improvement over the manual feature extraction.  Both have roughly the same F1 scores, but the neural net is successfully able to classify images by more specific type.  The classification has more meaning as a result.  

When using **manual feature extraction** with a **decision tree**, the overall **F1 score** was **87%**.  The two smaller classes, lymphocytes and monocytes had an F1 average of 48%.

When using the **pretrained convolutional layer** with a **neural net**, the overall **F1 score** is **78%**.  The two smaller classes, lymphocytes and monocytes have an F1 average of 60%.

#### **Classification Report**: Pretrained Convolution Layer + Neural Net  
<img src="Presentation/images/classification_report_cnn.png">  

#### **Confusion Matrix**: Pretrained Convolution Layer + Neural Net   
<img src="Presentation/images/confusion_matrix_CNN.png" width = 600px>

### Data Understanding

The data set consists of 1056 photos of blood samples.  The white blood cells are centered, and have a dark purple nucleus (due to staining) surrounded by a lighter purple cytoplasm.  The red blood cells appear small and gray.  

The distribution of whiteblood cell types are:
- **Basophil**: 213 images  
- **Eosinophil**: 745 images
- **Neutrophil**: 6232 images
- **Lymphocyte**: 2428 images
- **Monocyte**: 562 images

### Data Preparation
Load the images into training and validation sets.  Shift and flip images to augment the data set with additional images.

### Analysis
Construct a convolutional neural net, using the VGG16 convolution layers attached to two additional layers of nodes.  The VGG16 layers will be frozen, so only the additional layers will be trained on the data.

### Visualizations
Plot model accuracy and loss vs. training time.

### Conclusions
The neural net offers a mixed improvement over the manual feature extraction.  Both have roughly the same F1 scores, but the neural net is successfully able to classify images by more specific type.  The classification has more meaning as a result.  

When using **manual feature extraction** with a **decision tree**, the overall **F1 score** was **87%**.  The two smaller classes, lymphocytes and monocytes had an F1 average of 48%.

When using the **pretrained convolutional layer** with a **neural net**, the overall **F1 score** is **78%**.  The two smaller classes, lymphocytes and monocytes have an F1 average of 60%.

#### **Classification Report**: Pretrained Convolution Layer + Neural Net  
<img src="Presentation/images/classification_report_cnn.png">  

#### **Confusion Matrix**: Pretrained Convolution Layer + Neural Net   
<img src="Presentation/images/confusion_matrix_CNN.png" width = 600px>

### Next Steps
There are additional pretrained convolution nets, such as Resnet50, which may offer improvements over the one used in this network.  For an equal comparison between the two classifiers, the decision tree and neural net, the decision tree classification should be used to classify images by types.

## Reference
- "White Blood Cell Data Set," Kaggle: https://www.kaggle.com/datasets/masoudnickparvar/white-blood-cells-dataset/  
- ImageDataGenerator Technique, "ResNet50 White Blood Cells Classification" https://www.kaggle.com/code/arifrizqy/resnet50-white-blood-cells-classification
