# Learning Geometry-Disentangled Representation for Complementary Understanding of 3D Object Point Cloud.
This repository is built for the paper:

__Learning Geometry-Disentangled Representation for Complementary Understanding of 3D Object Point Cloud (_AAAI2021_)__ [[arXiv](https://arxiv.org/abs/2012.10921)]
<br>
by [Mutian Xu*](https://mutianxu.github.io/), [Junhao Zhang*](https://junhaozhang98.github.io/), Zhipeng Zhou, Mingye Xu, Xiaojuan Qi and Yu Qiao.


## Overview
Geometry-Disentangled Attention Network for 3D object point cloud classification and segmentation (GDANet):
<img src = './imgs/GDANet.jpg' width = 800>

## Citation
If you find the code or trained models useful, please consider citing:

    @inproceedings{xu2021gdanet,
      title={Learning Geometry-Disentangled Representation for Complementary Understanding of 3D Object Point Cloud}, 
      author={Mutian Xu and Junhao Zhang and Zhipeng Zhou and Mingye Xu and Xiaojuan Qi and Yu Qiao},
      booktitle={AAAI},
      year={2021}
    }


## Installation


### Requirements
* Linux (tested on Ubuntu 14.04/16.04)
* Python 3.5+
* PyTorch 1.0+

### Dataset
* Create the folder to symlink the data later:

    `mkdir -p data`

* __Object Classification__:

    Download and unzip [ModelNet40](https://shapenet.cs.stanford.edu/media/modelnet40_ply_hdf5_2048.zip) (415M), then symlink the path to it as follows (you can alternatively modify the path [here](https://github.com/mutianxu/GDANet/blob/main/util/data_util.py#L12)) :

    `ln -s /path to modelnet40/modelnet40_ply_hdf5_2048 data`

* __Shape Part Segmentation__:

    Download and unzip [ShapeNet Part](https://shapenet.cs.stanford.edu/media/shapenetcore_partanno_segmentation_benchmark_v0_normal.zip) (674M), then symlink the path to it as follows (you can alternatively modify the path [here](https://github.com/mutianxu/GDANet/blob/main/util/data_util.py#L70)) :

    `ln -s /path to shapenet part/shapenetcore_partanno_segmentation_benchmark_v0_normal data`

## Usage

### Object Classification on ModelNet40
* Train:

    `python main_cls.py`

* Test:
    * Run the voting evaluation script, after this voting you will get an accuracy of 93.8% if all things go right:

        `python voting_eval_modelnet.py --model_path 'pretrained/GDANet_ModelNet40_93.4.t7'`

    * You can also directly evaluate our pretrained model without voting to get an accuracy of 93.4%:

        `python main.py --eval True --model_path 'pretrained/GDANet_ModelNet40_93.4.t7'`

### Shape Part Segmentation on ShapeNet Part
* Train:
    * Training from scratch:

        `python main_ptseg.py`

    * If you want resume training from checkpoints, specify `resume` in the args:

        `python main_ptseg.py --resume True`

* Test:

    You can choose to test the model with the best instance mIoU, class mIoU or accuracy, by specifying `eval` and `model_type` in the args:

    * `python main_ptseg.py --eval True --model_type 'insiou'` (best instance mIoU, default)

    * `python main_ptseg.py --eval True --model_type 'clsiou'` (best class mIoU)

    * `python main_ptseg.py --eval True --model_type 'acc'` (best accuracy)

    **Note**: This works only after you trained the model or if you have the checkpoint in `checkpoints/GDANet`. If you run the training from scratch the checkpoints will automatically be generated there.
 

## Performance
The following tables report the current performances on different tasks and datasets.

### Object Classification on ModelNet40

| Method | OA |
| :--- | :---: |
| GDANet      | **93.8%** |

### Object Classification under Corruptions on ModelNet-C.
| Method |  mCE | Clean OA |
| :--- | :---: | :---: |
| GDANet    | **0.892** | **0.934** |

### Object Classification against Common Corruptions on ModelNet40-C.
| Method |  Corruption Error Rate (%) | Clean Error Rate (%) |
| :--- | :---: | :---: |
| GDANet    | **25.6** | **7.5** |


### Shape Part Segmentation on ShapeNet Part
| Method |  Class mIoU | Instance mIoU |
| :--- | :---: | :---: |
| PAConv _(*DGCNN)_    | **85.0%** | **86.5%** |

## Other information

Please contact Mutian Xu (mino1018@outlook.com) or Junhao Zhang (junhaozhang98@gmail.com) for further discussion.

## Acknowledgement
This code is is partially borrowed from [DGCNN](https://github.com/WangYueFt/dgcnn) and [PointNet++](https://github.com/charlesq34/pointnet2).  

## Update

20/05/2022:

GDANet gains competitive performance on both [ModelNet-C](https://github.com/jiawei-ren/ModelNet-C) and [ModelNet40-C](https://github.com/jiachens/ModelNet40-C) datasets for object classification under corruptions.
