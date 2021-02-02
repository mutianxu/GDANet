# Learning Geometry-Disentangled Representation for Complementary Understanding of 3D Object Point Cloud. AAAI 2021
Learning Geometry-Disentangled Representation for Complementary Understanding of 3D Object Point Cloud

## Overview

<img src = './imgs/GDANet.jpg' width = 800>

Futher information please contact Mutian Xu (mino1018@outlook.com)

## Citation
If you find the code or trained models useful, please consider citing:

    @misc{xu2021learning,
      title={Learning Geometry-Disentangled Representation for Complementary Understanding of 3D Object Point Cloud}, 
      author={Mutian Xu and Junhao Zhang and Zhipeng Zhou and Mingye Xu and Xiaojuan Qi and Yu Qiao},
      year={2021},
      eprint={2012.10921},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}


## Installation


### Requirements
* Linux (tested on Ubuntu 14.04/16.04)
* Python 3.5+
* PyTorch 1.0+

## Usage

### 3D Object Classification on ModelNet40
* Run the training script:

``` 
python main.py 
```

* Run the evaluation script:
```
python main.py --eval True --model_path 'pretrained/GDANet_ModelNet40_93.4.t7'
```

## Other information
We will release classification model on ScanObjectNN and part segmentation code later. 

## Acknowledgement
This code is based on [DGCNN](https://github.com/WangYueFt/dgcnn).  