# STViT-R for Detection
This is an official implementation for [Making Vision Transformers Efficient from A Token Sparsification View](https://arxiv.org/pdf/2303.08685.pdf). It is based on [Swin Transformer](https://github.com/SwinTransformer/Swin-Transformer-Object-Detection).

**Notes:**
We will further clean the code and release the checkpoints in the future.

## Results on COCO
| Model | $AP^b$ | $AP^b_{50}$ | $AP^b_{75}$ | $AP^b_s$ | $AP^m$  | $AP^m_{50}$  | $AP^m_{75}$ | $AP^m_{s}$ | log |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |:---: |
| STViT-R-Swin-S | 51.8 | 70.6 | 56.1 | 36.7 | 44.7 | 67.8 | 48.6 | 29.0 | [Link](https://github.com/changsn/STViT-R/blob/main/log/20220503_175914.log) |
| STViT-R-Swin-B | 52.2 | 70.8 | 56.8 | 36.5 | 45.2 | 68.3 | 49.1 | 29.5 | [Link](https://github.com/changsn/STViT-R/blob/main/log/20220506_143719.log) |
## Usage
### Installation

Please refer to [MMDetection](https://github.com/open-mmlab/mmdetection/blob/master/docs/en/get_started.md) for installation and dataset preparation.

We use apex for mixed precision training by default. To install apex, run:
```
git clone https://github.com/NVIDIA/apex
cd apex
pip install -v --disable-pip-version-check --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
```


### Training
To train a Cascade Mask R-CNN model with a `STVIT-R-Swin-S` backbone and 8 gpus, run:
```
tools/dist_train.sh configs/swin/cascade_mask_rcnn_swin_small_patch4_window7_mstrain_480-800_giou_4conv1f_adamw_3x_coco.py 8 --cfg-options model.pretrained=<PRETRAIN_MODEL> 
```

To train a Cascade Mask R-CNN model with a `STVIT-R-Swin-B` backbone and 8 gpus, run:
```
tools/dist_train.sh configs/swin/cascade_mask_rcnn_swin_base_patch4_window7_mstrain_480-800_giou_4conv1f_adamw_3x_coco.py 8 --cfg-options model.pretrained=<PRETRAIN_MODEL> 
```

## Citing STViT-R
```
@article{chang2023making,
  title={Making Vision Transformers Efficient from A Token Sparsification View},
  author={Chang, Shuning and Wang, Pichao and Lin, Ming and Wang, Fan and Zhang, David Junhao and Jin, Rong and Shou, Mike Zheng},
  journal={arXiv preprint arXiv:2303.08685},
  year={2023}
}
```
