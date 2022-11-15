# NeuralNetworks_GestureRecognition
Project to recognize  hand gesture using state of the art neural networks.

## Team
- Manish Hemani
- Swapnil Johari

Imagine you are working as a data scientist at a home electronics company which manufactures state of the art smart televisions. You want to develop a cool feature in the smart-TV that can recognise five different gestures performed by the user which will help users control the TV without using a remote.

The gestures are continuously monitored by the webcam mounted on the TV. Each gesture corresponds to a specific command:

Thumbs up:  Increase the volume
Thumbs down: Decrease the volume
Left swipe: 'Jump' backwards 10 seconds
Right swipe: 'Jump' forward 10 seconds  
Stop: Pause the movie

Each video is a sequence of 30 frames (or images). In the next couple of lectures, our subject matter expert Snehansu will walk you through the structure of the dataset.

## Understanding the Dataset
The training data consists of a few hundred videos categorised into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames(images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use. 

## Model Overview

|    **Model**   | **Model Type** | **Batch Size** | **Epoch** | **Total Params** | **Augmented Data** | **Model Size** | **Loss** | **Acuracy** |                                                                     **Comment**                                                                     |
|:--------------:|:--------------:|:--------------:|:---------:|:----------------:|:------------------:|:--------------:|:--------:|:-----------:|:---------------------------------------------------------------------------------------------------------------------------------------------------:|
|    conv_3d1    |     Conv3D     |       40       |     15    |     1,117,061    |         No         |      13.2      |    10%   |     99%     | Overfitting model                                                                                                                                   |
|    conv_3d2    |     Conv3D     |       20       |     25    |     3,638,981    |         Yes        |      42.7      |    31%   |     89%     | Model is not over-fitting. Observed minor oscillations in loss so will   try reducing parameters, by lowering the learning rate to 0.0002            |
|    conv_3d3    |     Conv3D     |       30       |     30    |     1,762,613    |         Yes        |      20.7      |    75%   |     72%     | Results looks stable .by reducing    parameter size by half.                                                                                        |
|    conv_3d4    |     Conv3D     |       20       |     30    |     2,556,533    |         Yes        |      30.1      |    39%   |     86%     | By Adding more layers, model becomes over-fitting.                                                                                                     |
|    conv_3d5    |     Conv3D     |       20       |     22    |     2,556,533    |         Yes        |      30.1      |    38%   |     85%     | After Adding dropouts , validation accuracy is reduced as its not to   learn generalizable features and its further over-fitting                    |
|    conv_3d6    |     Conv3D     |       20       |     30    |      696,645     |         Yes        |       8.2      |    55%   |     81%     | Reducing the number of network parameters by reducing image resolution/   filter size and dense layer neurons. Comparably good validation accuracy. |
|    conv_3d7    |     Conv3D     |       20       |     25    |      504,709     |         Yes        |        6       |    59%   |     78%     |                                                                                                                                                     |
|    conv_3d8    |     Conv3D     |       20       |     30    |      230,949     |         Yes        |       2.8      |    98%   |     61%     |                                                                                                                                                     |
| rnn_cnn1_model |    CNN-LSTM    |       20       |     20    |     1,657,445    |         Yes        |      19.5      |    18%   |     95%     | Model is over-fitting.                                                                                                                              |

### Models with More Data Augmentation

|    **Model**   | **Model Type** | **Batch Size** | **Epoch** | **Total Params** | **Augmented Data** | **Model Size** | **Loss** | **Acuracy** |
|:--------------:|:--------------:|:--------------:|:---------:|:----------------:|:------------------:|:--------------:|:--------:|:-----------:|
|    conv_3d10   |     Conv3D     |       20       |     30    |     3,638,981    |         Yes        |      42.7      |    45%   |     82%     |
|    conv_3d11   |     Conv3D     |       30       |     30    |     1,762,613    |         Yes        |      20.7      |    85%   |     68%     |
|    conv_3d12   |     Conv3D     |       20       |     30    |     2,556,533    |         Yes        |      30.1      |    56%   |     80%     |
|    conv_3d13   |     Conv3D     |       20       |     25    |     2,556,533    |         Yes        |      30.1      |    87%   |     67%     |
|    conv_3d14   |     Conv3D     |       20       |     30    |      696,645     |         Yes        |       8.2      |    47%   |     84%     |
|    conv_3d15   |     Conv3D     |       20       |     25    |      504,709     |         Yes        |        6       |    54%   |     80%     |
|    conv_3d16   |     Conv3D     |       20       |     30    |      230,949     |         Yes        |       2.8      |    85%   |     68%     |
| rnn_cnn1_model |    CNN-LSTM    |       20       |     20    |     2,573,925    |         Yes        |      30.2      |    23%   |     94%     |

### ### Transfer Learning Models (CNN + RNN)
|     **Model**     |   **Model Type**  | **Batch Size** | **Epoch** | **Total Params** | **Augmented Data** | **Model Size** | **Loss** | **Acuracy** |
|:-----------------:|:-----------------:|:--------------:|:---------:|:----------------:|:------------------:|:--------------:|:--------:|:-----------:|
| rnn_cnn_tl_model  | Transfer Learning | 5              | 20        | 3,840,453        | Yes                | 19.9           | 4%       | 99%         |
| rnn_cnn_tl2_model | With GRU          | 5              | 20        | 3,693,253        | Yes                | 43.4           | 1%       | 100%        |

