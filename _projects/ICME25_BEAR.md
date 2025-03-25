---
layout: page
title: BEAR
description: Domain-Hallucinated Updating for Multi-Domain Face Anti-spoofing (ICME-2025)
img: assets/img/AAAI24_DHU/fig1.png
importance: 1
category: research
---


<h3 align="center">Domain-Hallucinated Updating for Multi-Domain Face Anti-spoofing</h3>

  <p align="center">
    Chengyang Hu<sup>1</sup>*, Ke-Yue Zhang<sup>2</sup>*, Taiping Yao<sup>2</sup>, Shice Liu<sup>2</sup>, Shouhong Ding<sup>2</sup>, Xin Tan<sup>3</sup>, Lizhuang Ma<sup>1,3,4</sup>
    <br />
    <sup>1</sup> Shanghai Jiao Tong University
    <br />
    <sup>2</sup> Youtu Lab, Tencent
    <br />
    <sup>3</sup> East China Normal University
    <br />
    <sup>4</sup> MoE Key Lab of Artificial Intelligence, Shanghai Jiao Tong University
    <br />
    <a><strong>(AAAI 2024)</strong></a>
    <br />
    <br />
    <a href="https://ojs.aaai.org/index.php/AAAI/article/view/27992">Paper</a>
    ·
    <a href="https://github.com/hu-cheng-yang/CVPR2024-HPDR?tab=readme-ov-file">Code</a>
    <!-- Code (Release Soon) -->
    ·
    <a href="https://hu-cheng-yang.github.io/projects/AAAI24_DHU/">Project Page</a>
    ·
    <a href="https://mp.weixin.qq.com/s/MAHtzbwfte0t1Th6thHaEA">中文解读</a>
  </p>

## Abstract

Multi-Domain Face Anti-Spoofing (MD-FAS) is a practical setting that aims to update models on new domains using only novel data while ensuring that the knowledge acquired from previous domains is not forgotten. Prior methods utilize the responses from models to represent the previous domain knowledge or map the different domains into separated feature spaces to prevent forgetting. However, due to domain gaps, the responses of new data are not as accurate as those of previous data.  Also, without the supervision of previous data, separated feature spaces might be destroyed by new domains while updating, leading to catastrophic forgetting. Inspired by the challenges posed by the lack of previous data, we solve this issue from a new standpoint that generates hallucinated previous data for updating FAS model. To this end, we propose a novel Domain-Hallucinated Updating (DHU) framework to facilitate the hallucination of data. Specifically, Domain Information Explorer learns representative domain information of the previous domains. Then, Domain Information Hallucination module transfers the new domain data to pseudo-previous domain ones. Moreover, Hallucinated Features Joint Learning module is proposed to asymmetrically align the new and pseudo-previous data for real samples via dual levels to learn more generalized features, promoting the results on all domains. Our experimental results and visualizations demonstrate that the proposed method outperforms state-of-the-art competitors in terms of effectiveness.

## Method

<!-- ![Framework](/assets/img/AAAI24_DHU/framework.png) -->
<div align=center> 
<img src="/assets/img/AAAI24_DHU/framework.png" height=250>
</div>
The overall structure of proposed Domain-Hallucinated Updating (DHU) framework. First, we propose Domain Information Explorer to learn effective domain information in shallow layers. Also, we first propose Domain Information Hallucination module to hallucinate the previous domain feature to prevent the forgetting issue. After obtaining the pseudo-previous and new domain feature, we design Hallucinated Features Joint Learning to align the real input features from sample-based view and distribution-based view for generalizability.

<!-- GETTING STARTED -->

## Result

<!-- ![Result on FASMD Benchmark](/assets/img/AAAI24_DHU/result.png) -->
<div align=center> 
<img src="/assets/img/AAAI24_DHU/result.png" height=200>
</div>

The performance reported in TPR@FPR=0.5%. The model first trains on the source dataset (A) and then train on other datasets (B-E). avg indicates the average performance on two datasets. Bolded scores indicate the best performance. \(\dag\): We re-implement FAS-wrapper with ResNet-18 by inserting stacked CNN models as Discriminator into every ResNet layer.

<div align=center> 

<!-- ![Result on OCMI Benchmark](/assets/img/AAAI24_DHU/result_longseq.png) -->
<img src="/assets/img/AAAI24_DHU/result_longseq.png" height=160>

</div>
The performance reported in AUC and ACER on long sequence CASIA ->  OULU -> Idiap -> MSU. 
Bolded scores show the best performance. Underlined scores show the second best performance.

<div align=center> 

<!-- ![Result on OCMI Benchmark](/assets/img/AAAI24_DHU/result_longseq.png) -->
<img src="/assets/img/AAAI24_DHU/result_general.png" height=220>

</div>

The performance on unseen domains in TPR@FPR=0.5% and ACER. The model first trains sequentially with datasets A and B and tests on C-E. The result in Serial, and Parallel Res-Adapter is the average result with different adapters. 

## Visualization

<div align=center> 

<!-- ![Result on OCMI Benchmark](/assets/img/AAAI24_DHU/result_longseq.png) -->
<img src="/assets/img/AAAI24_DHU/visualization.png" height=220>

</div>

* **Left**: The t-SNE visualization of the feature from different layers. (a) shows the previous, hallucinated previous, and new feature in the shallow layer (\(f_2\)) (b) shows the previous and new feature in the deep layer (\(f_4\)).
* **Right**: The t-SNE visualization of the previous domain information distribution. The right pictures show examples from different domain information groups.

## Conclusion
In this paper, we propose a novel Domain-Hallucinated Updating (DHU) framework to address the challenging task of Multi-domain Face Anti-Spoofing (MD-FAS). First, we introduce Domain Information Explorer in the previous training stage that learns representative domain information buffer \(\mathcal{B}\). Then, Domain Information Hallucination module is designed in the new training stage to generate pseudo-previous domain information to prevent forgetting. Additionally, we devise Hallucinated Features Joint Learning module to utilize pseudo-previous and new domain features, which aligns real samples' features from sample-based and distribution-based views to improve model's generalizability. The experimental results and visualizations demonstrate that the proposed method outperforms other competitors.


<!-- CONTRIBUTING -->
## Citing Our Work

If you find our work is useful in your reasearch, please consider citing:
```bib
@inproceedings{hu2024domain,
  title={Domain-Hallucinated Updating for Multi-Domain Face Anti-spoofing},
  author={Hu, Chengyang and Zhang, Ke-Yue and Yao, Taiping and Liu, Shice and Ding, Shouhong and Tan, Xin and Ma, Lizhuang},
  booktitle={Proceedings of the AAAI Conference on Artificial Intelligence},
  volume={38},
  number={3},
  pages={2193--2201},
  year={2024}
}
```


<!-- ACKNOWLEDGMENTS -->
## Acknowledgments
Our work is based on the following opensource project. We thank their authors for making the source code publically available.
* [mammoth](https://github.com/aimagelab/mammoth)
* [Multi-domain Learning FAS](https://github.com/CHELSEA234/Multi-domain-learning-FAS/tree/main/source_SiW_Mv2)

