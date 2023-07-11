# Multi-Level Global Context Cross Consistency for Semi-Supervised Ultrasound Image Segmentation with Diffusion Model

[Paper](https://arxiv.org/abs/2210.13012) | [Code](https://github.com/FengheTan9/Multi-Level_Global_Context_Cross_Consistency)

a Pytorch code base for [Multi-Level Global Context Cross Consistency Model for Semi-Supervised Ultrasound Image Segmentation with Diffusion Model](https://arxiv.org/abs/2210.13012)

## Introduction
Medical image segmentation is a critical step in computer-aided diagnosis, and convolutional neural networks are popular segmentation networks nowadays. However, the inherent local operation characteristics make it difficult to focus on the global contextual information of lesions with different positions, shapes, and sizes. Semi-supervised learning can be used to learn from both labeled and unlabeled samples, alleviating the burden of manual labeling. However, obtaining a large number of unlabeled images in medical scenarios remains challenging. To address these issues, we propose a Multi-level Global Context Cross-consistency (MGCC) framework that uses images generated by a Latent Diffusion Model (LDM) as unlabeled images for semi-supervised learning. The framework involves of two stages. In the first stage, a LDM is used to generate synthetic medical images, which reduces the workload of data annotation and addresses privacy concerns associated with collecting medical data. In the second stage, varying levels of global context noise perturbation are added to the input of the auxiliary decoder, and output consistency is maintained between decoders to improve the representation ability. Experiments conducted on open-source breast ultrasound and private thyroid ultrasound datasets demonstrate the effectiveness of our framework in bridging the probability distribution and the semantic representation of the medical image. Our approach enables the effective transfer of probability distribution knowledge to the segmentation network, resulting in improved segmentation accuracy.

### MGCC framework:

![framework](imgs/framework.png)

### MGCC model

![mgcc](imgs/MGCC.png)

### **Generation results**

**BUSI Result:**

<img src="imgs/gen_bus.png">  

**TUS Result:**

<img src="imgs/gen_tus.png"/>



## Datasets

Please put the [BUSI](https://www.kaggle.com/aryashah2k/breast-ultrasound-images-dataset) dataset or your own dataset as the following architecture. 
```
├── CMUNet
    ├── inputs
        ├── BUSI
            ├── images
            |   ├── benign (10).png
            │   ├── malignant (17).png
            │   ├── normal (14).png
            │   ├── ...
            |
            └── masks
                ├── 0
                |   ├── benign (10).png
                |   ├── malignant (17).png
                |   ├── normal (14).png
                |   ├── ...
        ├── your dataset
            ├── images
            |   ├── 0a7e06.png
            │   ├── 0aab0a.png
            │   ├── 0b1761.png
            │   ├── ...
            |
            └── masks
                ├── 0
                |   ├── 0a7e06.png
                |   ├── 0aab0a.png
                |   ├── 0b1761.png
                |   ├── ...
```
## Environment

- GPU: NVIDIA GeForce RTX4090 GPU
- Pytorch: 1.13.0 cuda 11.7
- cudatoolkit: 11.7.1
- scikit-learn: 1.0.2

## Training and Validation

1. Generate Stage:

   You can follow this [work](https://github.com/mueller-franzes/medfusion).

2. Semi-supervised Learning Stage:

   You can first spilt your dataset:

   ```python
   python split.py
   ```

   Then, training your dataset:

   ```python
   python train.py
   ```

## Acknowledgements:

This code-base uses helper functions from [CMU-Net](https://github.com/FengheTan9/CMU-Net), [SSL4MIS](https://github.com/HiLab-git/SSL4MIS) and [medFusion](https://github.com/mueller-franzes/medfusion).

## Citation

If you use our code, please cite our paper:

```tex
@article{tang2023multi,
  title={Multi-Level Global Context Cross Consistency Model for Semi-Supervised Ultrasound Image Segmentation with Diffusion Model},
  author={Tang, Fenghe and Ding, Jianrui and Wang, Lingtao and Xian, Min and Ning, Chunping},
  journal={arXiv preprint arXiv:2305.09447},
  year={2023}
}
```

