<!--
# Pietro is a god

# Content
## Project Description
## Showcase best
### Best 2D + 3D
## Abstract + Motivation
## 2D Results
### Model Comparison
## 3D Results
### Model Comparison
## Augmentation Effect
## Summary of high level findings + Future improvements
-->

## The Team
Five students at Imperial College London following the third year of Biomedical Engineering. The project has been developed under the supervision of Dr. Neal Bangerter.

## Best 2D + 3D volume & slice pics as header

### 3D Segmentation plot
{% include segmentation_plotly.html %}


### Talbe plotly
{% include plotly_table.html %}

## Our Project
Cartilage segmentation plays a crucial role in tracking through time the effectiveness of drug treatment on osteoarthritis. For this purpose, Magnetic Resonance Imaging (MRI) is commonly used [1], allowing for a non-invasive approach.  However, manual segmentation of the latter is a labor-intensive process [2]. Automating this task would alleviate the practical obstacles to acquiring patient data and may soon become reality as novel deep learning approaches increasingly facilitate automatic image segmentation, potentially saving hospitals valuable resources [2, 3].

## Why we do it
This will work as motivation

## Training 
We crop the dataset to a standard size of (160, 288, 288) to remove the redundant background class region and artifacts. From this volume, the dataset is cropped to match the models input dimensions and geometric transformations are applied. We input the MRI scans and their corresponding ground-truth labels and compare the performance of our models using metrics shown in Figure 1 and model architectures shown in Figure 2. Following training, the predictions (slices or sub-volumes) are stitched back together to provide a prediction across whole volume. Multi-class segmentation entails the classification of multiple cartilage types: femoral, medial tibial, lateral tibial and patellar cartilage and lateral and medial meniscus. Binary segmentation merges these cartilages into one class, so the model is predicting if a voxel belongs to Cartilage or Background. 



## Segmentation requires specific architectures
Here we can show the various architectures we have used and their diagrams

Architecture specs figures + captions
### UNet
### UNet++
### VNet
### TIRAMISU
### DEEPLABV
(Failed:)
### R2-UNet

---

| 2D Models Implemented  | 3D Models Implemented |
|------------------------|-----------------------|
| Vanilla UNet           | 3D UNet               |
| Attention UNet         | Relative 3D UNet      |
| Multi-res UNet         | Slice 3D UNet         |
| R2_UNet                | VNet                  |
| R2_Attention UNet      | Relative VNet         |
| 100-layer Tiramisu     | Slice VNet            |
| DeepLabv3+             |                       |


---

## We are proud of our Results (preview... leave em hanging till the end)
We can place here the 
- bar graphs
- 3D plotly volume with slider over model evolution


## Comparison of performance
### Confusion matrices

## Discussion of augmentation methods (Analysis from poster)




## Conclusion + Key takeaways (from poster)



## Potentially cool but need update
### Baseline Comparision of 3D Methods

| Model                     | Input Shape       | Loss  | Val Loss | Duration / Min  |
|---------------------------|-------------------|-------|----------|-----------------|
| Small Highwayless 3D UNet | (160,160,160)     |       |          |                 |
| Small 3D UNet             | (160,160,160)     |       |          |                 |
| Small Relative 3D UNet    | (160,160,160),(3) |       |          |                 |
| Small VNet                | (160,160,160)     |       |          |                 |

#### Small 3D Unet Highwayless (160,160,160)

Training Loss | Training Progress
:------------:|:---------------------------:
![small-highway-less-loss](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_highwayless_train_result_2020_03_17-08_07_29.png?raw=True) | ![small-highway-less-progress](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_highwayless_progress.gif?raw=True)


<br />

#### Small 3D Unet (160,160,160)

Training Loss | Training Progress
:------------:|:---------------------------:
![small-3d-unet-loss](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_3dunet_train_result_2020_03_17-09_34_10.png?raw=True "Small 3D Unet Loss") | ![small-3d-unet-progress](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_3dunet_progress.gif?raw=True "Small 3D Unet Progress")


<br />

#### Small Relative 3D Unet (160,160,160),(3)

Training Loss | Training Progress
:------------:|:---------------------------:
![small-relative-3d-unet-loss](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_relative_3dunet_train_result_2020_03_17-11_03_20.png?raw=True "Small Relative 3D Unet Loss") | ![small-relative-3d-unet-progress](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_relative_3dunet_progress.gif?raw=True "Small Relative 3D Unet Progress")


<br />

#### Small VNet (160,160,160)

Training Loss | Training Progress
:------------:|:---------------------------:
![small-vnet-loss](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_vnet_train_result_2020_03_17-12_37_32.png?raw=True "Small VNet Loss") | ![small-vnet-progress](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/blob/master/results/3unet_vs_vnet_baseline/small_vnet_progress.gif?raw=True "Small VNet Progress")


---

### Comparison of VNet Methods

|      Model     |      Input Shape  |        Loss   |      Val Loss  |     Roll Loss | Roll Val Loss |Duration / Min|
|:--------------:|:-----------------:|:-------------:|:--------------:|:-------------:|:-------------:|:------------:|
|      Tiny      |     (64,64,64)    | 0.627 ± 0.066 |  0.684 ± 0.078 | 0.652 ± 0.071 | 0.686 ± 0.077 |  61.5 ± 5.32 |
|      Tiny      |    (160,160,160)  | 0.773 ± 0.01  |  0.779 ± 0.019 | 0.778 ± 0.007 | 0.787 ± 0.016 | 101.8 ± 2.52 |
|      Small     |    (160,160,160)  | 0.648 ± 0.156 |  0.676 ± 0.106 | 0.656 ± 0.152 | 0.698 ± 0.076 | 110.1 ± 4.64 |
| Small Relative | (160,160,160),(3) | 0.653 ± 0.168 |  0.639 ± 0.176 | 0.659 ± 0.167 | 0.644 ± 0.172 | 104.6 ± 9.43 |
|      Slice     |     (160,160,5)   | 0.546 ± 0.019 |  0.845 ± 0.054 | 0.559 ± 0.020 | 0.860 ± 0.072 |  68.6 ± 9.68 |
|      Small     |    (240,240,160)  | 0.577 ± 0.153 |  0.657 ± 0.151 | 0.583 ± 0.151 | 0.666 ± 0.149 | 109.7 ± 0.37 |
|      Large     |    (240,240,160)  | 0.505 ± 0.262 |  0.554 ± 0.254 | 0.508 ± 0.262 | 0.574 ± 0.243 | 129.2 ± 0.50 |
| Large Relative | (240,240,160),(3) | 0.709 ± 0.103 |  0.880 ± 0.078 | 0.725 ± 0.094 | 0.913 ± 0.081 | 148.6 ± 0.20 |

```
Baseline results from training VNet models for 50 epochs, exploring how quick models converge. Models optimized for dice loss using a scheduled Adam optimizier. Start learning rate: $5e^{-5}$, Schedule drop: $0.9$, Schedule drop epoch frequency: $3$. Z-Score normalisation and replacement of outliers with mean pixel was applied to inputs. Subsamples were selected normally distributed from the centre. Github commit: cb39158

Optimal training session is choosen for each visulation.
```

#### Tiny VNet (64,64,64)

Training Loss | Training Progress
:------------:|:---------------------------:
![tiny_vnet_646464_loss](results/3d_50_epoch_baseline/archer/train_session_2020_03_24-19_12_02_tiny/train_result_2020_03_24-19_12_02.png) | ![tiny_vnet_646464_progress](results/3d_50_epoch_baseline/archer/train_session_2020_03_24-19_12_02_tiny/progress.gif)

#### Tiny VNet (160,160,160)

Training Loss | Training Progress
:------------:|:---------------------------:
![tiny_vnet_160160160_loss](results/3d_50_epoch_baseline/archer/train_session_2020_03_24-20_07_26_tiny/train_result_2020_03_24-20_07_26.png) | ![tiny_vnet_160160160_progress](results/3d_50_epoch_baseline/archer/train_session_2020_03_24-20_07_26_tiny/progress.gif)

#### Small VNet (160,160,160)

Training Loss | Training Progress
:------------:|:---------------------------:
![small_vnet_160160160_loss](results/3d_50_epoch_baseline/archer/train_session_2020_03_25-05_09_08_small/train_result_2020_03_25-05_09_08.png) | ![small_vnet_160160160_progress](results/3d_50_epoch_baseline/archer/train_session_2020_03_25-05_09_08_small/progress.gif)

#### Small Relative VNet (160,160,160),(3)

Training Loss | Training Progress
:------------:|:---------------------------:
![small_rel_vnet_160160160_loss](results/3d_50_epoch_baseline/archer/train_session_2020_03_25-06_57_15_small_relative/train_result_2020_03_25-06_57_15.png) | ![small_rel_vnet_160160160_progress](results/3d_50_epoch_baseline/archer/train_session_2020_03_25-06_57_15_small_relative/progress.gif)

#### Small Slice VNet (160,160,5)

Training Loss | Training Progress
:------------:|:---------------------------:
![small_slice_vnet_1601605_loss](results/3d_50_epoch_baseline/archer/train_session_2020_03_25-01_25_31_slice/train_result_2020_03_25-01_25_31.png) | ![small_slice_vnet_1601605_progress](results/3d_50_epoch_baseline/archer/train_session_2020_03_25-01_25_31_slice/progress.gif)

#### Small VNet (240,240,160)

Training Loss | Training Progress
:------------:|:---------------------------:
![small_vnet_240240160_loss](results/3d_50_epoch_baseline/pompeii/train_session_2020_03_25-06_39_15_small/train_result_2020_03_25-06_39_15.png) | ![small_vnet_240240160_progress](results/3d_50_epoch_baseline/pompeii/train_session_2020_03_25-06_39_15_small/progress.gif)

#### Large VNet (240,240,160)

Training Loss | Training Progress
:------------:|:---------------------------:
![large_vnet_240240160_loss](results/3d_50_epoch_baseline/pompeii/train_session_2020_03_24-13_06_17_large/train_result_2020_03_24-13_06_17.png) | ![large_vnet_240240160_progress](results/3d_50_epoch_baseline/pompeii/train_session_2020_03_24-13_06_17_large/progress.gif)

#### Large Relative VNet (240,240,160),(3)

Training Loss | Training Progress
:------------:|:---------------------------:
![large_rel_vnet_240240160_loss](results/3d_50_epoch_baseline/pompeii/train_session_2020_03_25-04_10_24_large_relative/train_result_2020_03_25-04_10_24.png) | ![large_rel_vnet_240240160_progress](results/3d_50_epoch_baseline/pompeii/train_session_2020_03_25-04_10_24_large_relative/progress.gif)

---

### Useful Code Snippets

``` Bash
Run main

python main.py --flagfile=config/train.cfg
```

``` Bash
Run 3D Train

python Segmentation/model/vnet_train.py
```

``` Bash
Unit-Testing and Unit-Test Converage

python -m pytest --cov-report term-missing:skip-covered --cov=Segmentation && coverage html && open ./htmlcov.index.html
```

## How to view these results
This can work as analysis
Compare the various models, their convergence ecc.

### Confusion Matrix

## What we have understood
Here we can put our interpretation and key takeaways

### Best models
Here we can put the best 2D and 3D models using slice and volume visualization

## What the future has to offer
What we would like to improve and continue to work on

## References



# Default stuff to keep in case we needed anything
You can use the [editor on GitHub](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.



### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Knee-Deep-in-MRI/Knee-Deep-in-MRI.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

