


<div align="center">

# Lane Detection for CCTV-cameras using CLRNet: Cross Layer Refinement Network 

</div>

## Introduction

- Lane Detection method for CCTV-cameras based on CLRNet: Cross Layer Refinement Network

## Installation

Refer to README_CLRNEt.md

## Getting Started

### Training and Evaluate CLRNet using Tusimple and CULane

```Shell
python main.py [configs/path_to_your_config] --gpus [gpu_num]
```
For example, run
```Shell
python main.py configs/clrnet/clr_resnet18_culane.py --gpus 0
```

For testing, run
```Shell
python main.py [configs/path_to_your_config] --[test|validate] --load_from [path_to_your_model] --gpus [gpu_num]
```

For example, run
```Shell
python main.py configs/clrnet/clr_dla34_culane.py --validate --load_from culane_dla34.pth --gpus 0
```

### Prepare CCTV-Camera Dataset

Contact administrator for dataset.

For CCTV-Camera, the folder structure is like this:

```
$CCTV-CameraROOT/Suwon    # data folders
$CCTV-CameraROOT/list      # data lists
```

### Run inference for CCTV-Camera Dataset

Download the "clr_resnet101_tusimple.pth" weight from [trained-weights]

```Shell
python main.py configs/clrnet/clr_resnet101_tusimple_cctv.py --test --load_from clr_resnet101_tusimple.pth --gpus 0 --view
```


## Results

[trained-weights]: https://drive.google.com/drive/folders/1N3EUMyaFJnCrAWhJkmEpeWx39gCa3Mo_?usp=share_link


### Reproduce results using F1 score metric. 

| Backbone                                                |    CULane     |   Tusimple    |
|:--------------------------------------------------------|:-------------:|:-------------:|
| CLRNet-Resnet18  / [CLRNet-Resnet18*][trained-weights]  | 79.58 / 79.49 | 97.89 / 97.82 |
| CLRNet-Resnet34  / [CLRNet-Resnet34*][trained-weights]  | 79.73 / 79.44 | 97.82 / 97.97 |
| CLRNet-Resnet101 / [CLRNet-Resnet101*][trained-weights] | 80.13 / 79.92 | 97.62 / 97.71 |


'F1@50' refers to the official metric, 
i.e., F1 score when IoU threshold is 0.5 between the gt and prediction. 'F1@75' is the F1 score when IoU threshold is 0.75.

'*' method is the reproduced results.
## Acknowledgement
<!--ts-->
* [open-mmlab/mmdetection](https://github.com/open-mmlab/mmdetection)
* [pytorch/vision](https://github.com/pytorch/vision)
* [Turoad/lanedet](https://github.com/Turoad/lanedet)
* [ZJULearning/resa](https://github.com/ZJULearning/resa)
* [cfzd/Ultra-Fast-Lane-Detection](https://github.com/cfzd/Ultra-Fast-Lane-Detection)
* [lucastabelini/LaneATT](https://github.com/lucastabelini/LaneATT)
* [aliyun/conditional-lane-detection](https://github.com/aliyun/conditional-lane-detection)
<!--te-->

