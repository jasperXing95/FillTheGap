<div align="center">
<h1>SpA GAN for Cloud Removal</h1>
</div>

<div align="center">
<img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/Penn000/SpA-GAN_for_cloud_removal?color=green"> <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/Penn000/SpA-GAN_for_cloud_removal">  <img alt="GitHub issues" src="https://img.shields.io/github/issues/Penn000/SpA-GAN_for_cloud_removal"> <img alt="GitHub closed issues" src="https://img.shields.io/github/issues-closed/Penn000/SpA-GAN_for_cloud_removal?color=red">
</div>
<div align="center">
<img alt="GitHub watchers" src="https://img.shields.io/github/watchers/Penn000/SpA-GAN_for_cloud_removal?style=social"> <img alt="GitHub stars" src="https://img.shields.io/github/stars/Penn000/SpA-GAN_for_cloud_removal?style=social"> <img alt="GitHub forks" src="https://img.shields.io/github/forks/Penn000/SpA-GAN_for_cloud_removal?style=social">
</div>

This codes is mainly copy from https://github.com/Penn000/SpA-GAN_for_cloud_removal


## 1. INTRODUCTION

This is the source code of [***Cloud Removal for Remote Sensing Imagery via Spatial Attention Generative Adversarial Network***](https://arxiv.org/abs/2009.13015). In this work, I proposes a novel cloud removal model called ***spatial attention generative adversarial networks*** or ***SpA GAN***, which use [spatial attention networks (SPANet)](https://github.com/stevewongv/SPANet) as generator. The architecture of *SpA GAN* is shown as fellow:

- **Generator**

*SpA GAN* uses *spatial attention networks* an generator. See `./models/gen/SPANet.py` for more details.

<div align="center"><img src="./readme_images/SPANet.jpg"></div>

- **Discriminator**

Discriminator is a fully  CNN that **C** is convolution layer, **B** is batch normalization and **R** is Leaky ReLU. See `./models/dis/dis.py` for more details.

<div align="center"><img src="./readme_images/dis.jpg"></div>

- **Loss**

The total loss of *SpA GAN* is formulated as fellow:

<div align="center"><img src="./readme_images/loss_spagan.png"></div>

the first part is the loss of GAN

<div align="center"><img src="./readme_images/loss_cgan.png"></div>

the second part is standard $L_1$ loss where $\lambda_c$ is a hyper parameter to control the weight of each channel to the loss.

<div align="center"><img src="./readme_images/loss_l1.png"></div>

the third part is attention loss where $A$ is the attention map and $M$ is the mask of cloud that computed from $M=|I_{in}-I_{gt}|_1$.

<div align="center"><img src="./readme_images/loss_att.png"></div>


### Citations

```
@article{Pan2020,
  title   = {Cloud Removal for Remote Sensing Imagery via Spatial Attention Generative Adversarial Network},
  author  = {Heng Pan},
  journal = {arXiv preprint arXiv:2009.13015},
  year    = {2020}
}
```



