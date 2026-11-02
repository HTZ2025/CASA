# CASA and CASA-Bench

Dataset resources for **CASA: An evidence-grounded multimodal framework for automated construction safety inspection**.

CASA (Construction Anything Scene Assistant) lets an inspector locate objects, ask about site activities, and see which workers or machines support a safety judgment. We will release the code upon publication.

## CASA-Bench

CASA-Bench evaluates three inspection tasks using scenes from **ConstructionSite 10k** and **Construction Activity Captioning — Dataset II** (called **Activity** in the paper). Its test set contains **24,566 questions across 3,573 images**.

| Task | Test questions | Source |
|---|---:|---|
| Object retrieval | 8,997 | ConstructionSite 10k |
| Safety assessment | 11,996 | ConstructionSite 10k |
| Scene and activity description | 3,573 | ConstructionSite 10k (2,999) and Activity (574) |

For safety assessment, we reviewed questions where CASA flagged a violation absent from the original label and corrected the label when the scene supported that judgment. We tightened overly broad boxes around the relevant objects and split boxes enclosing several targets into individual boxes. The revised references also include CASA-proposed boxes accepted during review.

## Source datasets and access

The links below provide the original authors’ releases. Section 4.1 of the paper describes the CASA-Bench splits and revised safety annotations. CISv2 and SODA supply separate training and evaluation data for CASA’s perception component.

| Dataset | Source annotations | Role in CASA | Original source |
|---|---|---|---|
| **CISv2** | Object categories, bounding boxes, and instance masks | Construction perception adaptation and evaluation | [Author repository](https://github.com/XZ-YAN/CIS-Dataset) |
| **SODA** | Object categories and bounding boxes | Joint perception adaptation with CISv2 and detection evaluation | [Author project page](https://linjiarui.net/en/portfolio/2022-02-22-SODA-site-object-detection-dataset-for-deep-learning-in-construction) |
| **ConstructionSite 10k** | Image captions, safety-rule violation annotations with explanations and supporting boxes, and object grounding annotations | Caption adaptation, multi-task instruction tuning, and evaluation of retrieval, safety assessment, and scene description | [Hugging Face dataset](https://huggingface.co/datasets/LouisChen15/ConstructionSite) |
| **Construction Activity Captioning — Dataset II** | Construction images and natural-language captions | Caption adaptation, instruction tuning, and activity-description evaluation; called **Activity** in our paper | [Author repository](https://github.com/HannahHuanLIU/AEC-image-captioning) |

### 1. CISv2

The Construction Instance Segmentation dataset provides instance-level annotations for construction workers, materials, and machinery. CASA uses **version 2 (CISv2)**, which supplies both bounding boxes and segmentation masks for perception adaptation.

- **Repository and preparation instructions:** [XZ-YAN/CIS-Dataset](https://github.com/XZ-YAN/CIS-Dataset)
- **CISv2 download:** [Aliyun Drive](https://www.alipan.com/s/zPCWUKibWGj)
- **Original paper:** [Construction Instance Segmentation (CIS) Dataset for Deep Learning-Based Computer Vision](https://doi.org/10.1016/j.autcon.2023.105083)

Select the **CISv2** release in the repository and follow the authors' decoding instructions to prepare its images and annotations.

### 2. SODA

SODA (Site Object Detection dAtaset) provides construction-site images with bounding-box annotations for workers, materials, machinery, and site-layout elements. CASA uses SODA as an additional source of box supervision during joint perception adaptation with CISv2.

- **Project page and download information:** [SODA — Jia-Rui Lin's page](https://linjiarui.net/en/portfolio/2022-02-22-SODA-site-object-detection-dataset-for-deep-learning-in-construction)
- **Author-provided Baidu Netdisk link:** [Download SODA](https://pan.baidu.com/s/1vuWIOdBnb-U5F_JOxcZoBw?pwd=9cnh)
- **Baidu extraction code:** `9cnh`
- **Original paper:** [SODA: A large-scale open site object detection dataset for deep learning in construction](https://doi.org/10.1016/j.autcon.2022.104499)

### 3. ConstructionSite 10k

ConstructionSite 10k supports three complementary tasks: image captioning, safety-rule violation question answering, and construction-object grounding.

CASA uses its captions for visual-language adaptation and its task annotations for instruction tuning and evaluation. Object retrieval covers excavators, rebar, and workers wearing white hard hats. Safety assessment covers basic personal protective equipment, fall protection, edge protection, and worker–excavator separation.

- **Original dataset:** [LouisChen15/ConstructionSite on Hugging Face](https://huggingface.co/datasets/LouisChen15/ConstructionSite)
- **Author implementation:** [ConstructionSite-10k-Implementation](https://github.com/LouisChen15/ConstructionSite-10k-Implementation)
- **Original paper:** [Are large pre-trained vision language models effective construction safety inspectors](https://doi.org/10.1017/dce.2026.10044)

To access the dataset files, sign in to Hugging Face and accept the conditions shown on the dataset page.

### 4. Construction Activity Captioning — Dataset II

The construction-activity image-captioning study releases two datasets. CASA uses **Dataset II**, referred to as **Activity** in our paper, for learning and evaluating descriptions of visible construction activities.

- **Repository:** [HannahHuanLIU/AEC-image-captioning](https://github.com/HannahHuanLIU/AEC-image-captioning)
- **Dataset II download:** [Baidu Netdisk](https://pan.baidu.com/s/18DMTw7V6kBM_XIUoOYtyBw)
- **Baidu extraction code:** `9dzf`
- **Original paper:** [Manifesting construction activity scenes via image captioning](https://doi.org/10.1016/j.autcon.2020.103334)

Choose the **Dataset II** download listed in the authors' repository.

## Dataset Citations

Please cite the original dataset papers when using these resources.

```bibtex
@article{yan2023cis,
  author  = {Yan, Xuzhong and Zhang, Hong and Wu, Yefei and Lin, Chen and Liu, Shengwei},
  title   = {Construction Instance Segmentation (CIS) Dataset for Deep Learning-Based Computer Vision},
  journal = {Automation in Construction},
  volume  = {156},
  pages   = {105083},
  year    = {2023},
  doi     = {10.1016/j.autcon.2023.105083}
}

@article{duan2022soda,
  author  = {Duan, Rui and Deng, Hui and Tian, Mao and Deng, Yichuan and Lin, Jiarui},
  title   = {SODA: A large-scale open site object detection dataset for deep learning in construction},
  journal = {Automation in Construction},
  volume  = {142},
  pages   = {104499},
  year    = {2022},
  doi     = {10.1016/j.autcon.2022.104499}
}

@article{chen2026construction,
  author  = {Chen, Xuezheng and Zou, Zhengbo},
  title   = {Are large pre-trained vision language models effective construction safety inspectors},
  journal = {Data-Centric Engineering},
  volume  = {7},
  pages   = {e11},
  year    = {2026},
  doi     = {10.1017/dce.2026.10044}
}

@article{liu2020captioning,
  author  = {Liu, Huan and Wang, Guangbin and Huang, Ting and He, Ping and Skitmore, Martin and Luo, Xiaochun},
  title   = {Manifesting construction activity scenes via image captioning},
  journal = {Automation in Construction},
  volume  = {119},
  pages   = {103334},
  year    = {2020},
  doi     = {10.1016/j.autcon.2020.103334}
}
```

## Acknowledgments

We thank the dataset authors for making their data and annotations available to the construction research community. Each dataset remains subject to the terms provided by its original authors.
