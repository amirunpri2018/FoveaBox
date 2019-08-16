# FoveaBox: Beyond Anchor-based Object Detector

This repo is a official implementation of "FoveaBox: FoveaBox: Beyond Anchor-based Object Detector" on COCO object detection based on open-mmlab's mmdetection. Many thanks to mmdetection for their simple and clean framework.

FoveaBox is a state-of-the-art visual object detection system for object detection framework, as presented in our paper [https://arxiv.org/abs/1904.03797](https://arxiv.org/abs/1904.03797):

    FoveaBox: Beyond Anchor-based Object Detector;
    Tao Kong, Fuchun Sun, Huaping Liu, Yuning Jiang, Jianbo Shi;
    arXiv preprint arXiv:1904.03797.

## Introduction
FoveaBox is an accurate, flexible and completely anchor-free framework for object detection. 
Different from previous anchor-based methods, FoveaBox directly learns the object existing possibility and the bounding box coordinates without anchor reference. This is achieved by: (a) predicting category-sensitive semantic maps for the object existing possibility, and (b) producing category-agnostic bounding box for each position that potentially contains an object.

## For a installation 
This FoveaBox implementation is based on [mmdetection](https://github.com/open-mmlab/mmdetection). Therefore the installation is the same as original mmdetection.

Please check [INSTALL.md](INSTALL.md) for installation instructions.


## Inference
The inference command line on coco minival split:

    # multi-gpu testing
    ./tools/dist_test.sh configs/foveabox/fovea_xxx.py ${CHECKPOINT_FILE} ${GPU_NUM} [--out ${RESULT_FILE}] [--eval bbox] 


## Main Results
### Results on R50-FPN with backbone

| Backbone  | Style   | align  | Lr schd | Mem (GB) | Train time (s/iter) | Inf time (fps) | box AP | Download |
|:---------:|:-------:|:-------:|:-------:|:--------:|:-------------------:|:--------------:|:------:|:--------:|
| R-50      | pytorch   | N      | 1x      | 5.7      | 0.450               | 13.5           | 36.5   | [model](https://drive.google.com/file/d/19eQNnctoC1VTcP2AKdCryQGjb6Dzq62r/view?usp=sharing) |
| R-50      | pytorch   | N      | 2x      | -        | 0.396               | 13.5           | 36.9   | [model](sss) |
| R-50      | pytorch   | Y      | 2x      | -        | -                   | -              | 36.9   | [model](sss) |
| R-101     | pytorch   | N      | 1x      | 9.4      | 0.712               | 11.5           | 38.5   | [model](https://drive.google.com/file/d/1Xb6hDUquGKB8ad7DigrF8K9sX8xoZigh/view?usp=sharing) |
| R-101     | pytorch   |        | 2x      | -        | -                   | -              | 39.1   | [model](sss) |
| R-101     | pytorch   | N      | 1x      | -        | 0.558               | 11.6           | 39.1   | [model](sss) |

[1] *1x and 2x mean the model is trained for 12 and 24 epochs, respectively.* \
[2] *Align means utilizing deformable convolution to align the cls branch.* \
[3] *All results are obtained with a single model and without any test time data augmentation.* \

Any pull requests or issues are welcome.

## Citations
Please consider citing our paper in your publications if the project helps your research. BibTeX reference is as follows.
```
@article{kong2019foveabox,
  title={FoveaBox: Beyond Anchor-based Object Detector},
  author={Kong, Tao and Sun, Fuchun and Liu, Huaping and Jiang, Yuning and Shi, Jianbo},
  journal={arXiv preprint arXiv:1904.03797},
  year={2019}
}
```


## License

For academic use, this project is licensed under the 2-clause BSD License - see the LICENSE file for details. For commercial use, please contact the authors. 
