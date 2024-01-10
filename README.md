# SAM-CD
Pytorch codes of **Adapting Segment Anything Model for Change Detection in HR Remote Sensing Images** [[paper](http://arxiv.org/abs/2309.01429)]

![alt text](https://github.com/ggsDing/SAM-CD/blob/main/flowchart.png)

The SAM-CD adopts [FastSAM](https://github.com/CASIA-IVA-Lab/FastSAM) as the visual encoder with some modifications.


## How to Use
1. Installation
   * Install [FastSAM](https://github.com/CASIA-IVA-Lab/FastSAM) following the instructions.
   * Modify the Ultralytics source files following the instructions at: ['SAM-CD/models/FastSAM/README.md'](https://github.com/ggsDing/SAM-CD/blob/main/models/FastSAM/README.md). 

2. Dataset preparation.
   * Please split the data into training, validation and test sets and organize them as follows:
```
      YOUR_DATA_DIR
      ├── ...
      ├── train
      │   ├── A
      │   ├── B
      │   ├── label
      ├── val
      │   ├── A
      │   ├── B
      │   ├── label
      ├── test
      │   ├── A
      │   ├── B
      │   ├── label
```

   * Find change line 13 in [SAM-CD/datasets/Levir_CD.py](https://github.com/ggsDing/SAM-CD/blob/main/datasets/Levir_CD.py) (or other data-loading .py files), change `/YOUR_DATA_ROOT/` to your local dataset directory.

3. Training
   
   classic CD training:
   `python train_CD.py`
   
   training CD with the proposed task-agnostic semantic learning:
   `python train_SAM_CD.py`
   
   line 16-45 are the major training args, which can be changed to load different datasets, models and adjust the training settings.

5. Inference and evaluation
   
   inference on test sets: set the chkpt_path and run
   
   `python pred_CD.py`
   
   evaluation of accuracy: set the prediction dir and GT dir, and run
   
   `python eval_CD.py`
   
(More details to be added...)


## Dataset Download

In the following, we summarize links to some frequently used CD datasets:

* [LEVIR-CD](https://justchenhao.github.io/LEVIR/)
* [WHU-CD](https://study.rsgis.whu.edu.cn/pages/download/) [(baidu)](https://pan.baidu.com/s/1A0_xbV4ZktWCbL3j94CInA?pwd=WHCD )
* [CLCD (Baidu)](https://pan.baidu.com/s/1iZtAq-2_vdqoz1RnRtivng?pwd=CLCD)
* [S2Looking](https://github.com/S2Looking/Dataset)
* [SYSU-CD](https://github.com/liumency/SYSU-CD)

## Pretrained Models

For readers to easily evaluate the accuracy, we provide the trained weights of the SAM-CD.

[Drive](https://drive.google.com/drive/folders/14tNtID43o-LHs8VaMK5jai1Uf8NqMDAW?usp=sharing)  
[Baidu](https://pan.baidu.com/s/1V25TFGL5V05ZB5ttFXFSEA?pwd=SMCD) (pswd: SMCD)


## Cite SAM-CD

If you find this work useful or interesting, please consider citing the following BibTeX entry.

```
@article{ding2023adapting,
title={Adapting Segment Anything Model for Change Detection in HR Remote Sensing Images},
author={Ding, Lei and Zhu, Kun and Peng, Daifeng and Tang, Hao and Yang, Kuiwu and Lorenzo, Bruzzone},
journal={arXiv preprint arXiv:2309.01429},
year={2023}
}
```
