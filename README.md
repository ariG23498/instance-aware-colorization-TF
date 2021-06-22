# Instance-aware Colorization in TensorFlow

A minimal reproduction of [Instance-aware Image Colorization](https://arxiv.org/abs/2005.10825) in TensorFlow. In this repository we have tried encapsulating all the main featurs of the training process as suggested in the paper. The repository consists of jupyter notebook only, this was done to help readers with reading the code better and also execute and experiment on it. 

You can also check this Weights and Biases report for [quick paper summary](http://wandb.me/instcolorization-report). For inference using official model weights try out this [colab notebook](http://wandb.me/instcolorization-colab). 

What we have covered:
- The three stage training process
  - Stage 1: Learn to colorize full (total) image using UNet-like architecture.
  - Stage 2: Learn to colorize Instance (where an object of interest is available) using same UNet-like architecture (different weights).
  - Stage 3: Fusion model which fuses the total and instance colorization models
- Ablating on the following color spaces
  - RGB
  - L\*a\*b\*

## Directory Structure
- **RGB_Instance_aware_Image_Colorization.ipynb**: This notebook holds the end to end training process on the RGB color space.
- **rgb_lab_color_space.ipynb**: This notebook helps in understanding the rgb and lab color space. It also has the APIs that one would need to jump from one color space to another.
- **pascal_od_api.ipynb**: This notebook holds the inference of an object detection model (Mask-RCNN here) to showcase the tensorflow hub API. The authors in their paper have used an OD model for the bounding boxes for instances. In this repository we have used the training bbox provided and did not use the OD for that (infering on the OD takes time and in inefficient for a minimal implementation).
- **LAB_Instance_aware_Image_Colorization.ipynb**: This notebook hold the end to end training process on the L\*a\*b\* color space.

## Dataset
We have use the [PASCAL VOC](https://paperswithcode.com/dataset/pascal-voc) dataset. It is a small dataset which had bounding boxes along with images. We needed the bounding boxes because we ommited the use of an object detector in the training process. Owing to the small dataset the training process was considerable easy and we could train the entire model end to end on a colab notebook.

## Results
Here we provide the results from both the color space training (rgb and lab). The reader needs to keep this in mind that it is a minimal implementation where we have trained the entire model from scratch with a small dataset. The images have the structural integrity but lag good colors. We see here that the lab space results are better than the rgb results.

| RGB Color Space | LAB Color Space |
| :---: | :---: |
| ![image](https://user-images.githubusercontent.com/36856589/122922365-2a5e5800-d381-11eb-992c-3a5e39acb194.png) | ![image](https://user-images.githubusercontent.com/36856589/122922401-334f2980-d381-11eb-9aaf-a72b7519aec6.png) |



This is a collaborative effort of:
- [Aritra Roy Gosthipaty](https://twitter.com/ariG23498)\* (PyImageSearch)
- [Ayush Thakur](https://twitter.com/ayushthakur0)\* (Weights and Biases)

\* Equal Contribution
