# Convolutional  Neural Networks
- Used for image recognition programs, but can also be used for any data that can be represented in two (2) or more dimensions
- Designed to capture local spatial patterns, if data can't be represented as an image, CNN's, are not that usful
    - if data is just as useful after swapping any columns with each ther, then can't use CNN's
---
## Filtering
- `features`: little images that match peices of the bigger image
    - feature is lined up with each image patch
    - multiply each image pixel with corresponding feature pixel
    - add them up
    - divide by total nyumber of pixels in feature
        - creating a filtered image
        - gives an idea of how well a feature matches the image patch
    - this is done for each feature for each image patch
        - creating the respective filtered images
    - this act of convolving an image with a bunch of filters to create  stack of filtered images
        - is a convolution layer

<img src='https://www.edureka.co/blog/wp-content/uploads/2018/10/3-8.png'>

---
## Pooling
done to shrink the image stack
- pick a window size
- pick a stride
- walk window across filtered image
- from each window take the maximum value

pooling doesn't care what position in the window had the maximum value, which means it is less sensitive to position

---
## Normalization
- every negative value in filterd image is turn into a zero
    - ReLu layer

---
## Fully connected layer
- every value in the filtered stack of image gets a vote on the output nodes 

---
- All of these steps can be repeated multiple times to create many layers in the CNN

<img src='https://www.researchgate.net/publication/336805909/figure/fig1/AS:817888827023360@1572011300751/Schematic-diagram-of-a-basic-convolutional-neural-network-CNN-architecture-26.ppm'>

## Hyperparameters

| step            | params           |
|-----------------|------------------|
| Convolution     | Num of features  |
|                 | Size of features |
| Pooling         | Window size      |
|                 | Window stride    |
| Fully connected | Number of nodes  |