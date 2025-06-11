## 2025

**- A Lightweight Deep Exclusion Unfolding Network for Single Image Reflection Removal (PAMI 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2503.01938) | [GitHub](https://github.com/jjhuangcs/DExNet) | [中文](https://github.com/krantbrity/Single-Image-Reflection-Removal-Papers-and-Code-Collection/blob/main/TXT/A%20Lightweight%20Deep%20Exclusion%20Unfolding%20Network%20for%20Single%20Image%20Reflection%20Removal.md)

**简介**: DExNet提出了一个轻量级、可解释且有效的网络架构，通过展开和参数化迭代稀疏和辅助特征更新算法，引入通用排斥先验来识别和惩罚传输层和反射层特征之间的共性。该方法在四个基准数据集上达到了最先进的性能，同时仅使用领先方法约8%的参数量。

---

**- Reversible Decoupling Network for Single Image Reflection Removal (CVPR 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2410.08063) | [GitHub](https://github.com/lime-j/RDNet) | [中文](https://github.com/krantbrity/Single-Image-Reflection-Removal-Papers-and-Code-Collection/blob/main/Markdown/REVERSIBLE%20DECOUPLING%20NETWORK%20FOR%20SINGLE%20IMAGE%20REFLECTION%20REMOVAL.md)

<details>
<summary>RTX 4090 性能表现</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 25.7138 | 0.8501 |
| Postcard | 26.3343 | 0.9221 |
| Solidobject | 26.9457 | 0.9262 |
| Wild | 27.8440 | 0.9173 |
| Nature | 26.3053 | 0.8463 |
| **Overall** | **26.7236** | **0.9173** |

</details>

**简介**: RDNet采用可逆编码器来保护有价值的信息，同时在前向传播过程中灵活地解耦传输层和反射层相关特征。该方法还定制了传输率感知的提示生成器来动态校准特征，在五个广泛采用的基准数据集上超越了现有的最先进方法，并在NTIRE 2025野外单图像反射去除挑战赛中获得最佳性能。

---

**- Rethinking Depth Guided Reflection Removal (TMM 2025)**  
[PDF](https://ieeexplore.ieee.org/document/10891560) | [arXiv] | [GitHub]

**简介**: 该论文受人类双目视觉系统启发，重新思考深度引导的反射去除方法，提出了一种端到端的学习基础反射去除方法，学习传输深度并设计统一结构以级联方式实现深度引导、跨视图和跨帧特征增强。构建了包含合成和真实双目混合视频数据集用于网络训练和测试。

---

**- High-resolution image reflection removal by Laplacian-based component-aware transformer (Scientific Reports 2025)**  
[PDF](https://www.nature.com/articles/s41598-025-94464-6) | [arXiv] | [GitHub]

**简介**: LapCAT提出了一种新颖的基于变换器的高分辨率图像反射去除框架，利用拉普拉斯金字塔网络去除高频反射模式，并在清洁低频背景组件的指导下重建高分辨率背景图像。该方法通过拉普拉斯金字塔分离高分辨率图像为不同尺度的高频信息和低频信息，设计专门的组件感知变换器框架利用自注意力机制建模背景和反射组件之间的差异。

---

**- Dereflection: Any Image with Diffusion Priors and Diversified Data (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2503.17347) | [GitHub](https://github.com/Abuuu122/Dereflection-Any-Image)

**简介**: 该论文提出了"去反射任意图像"的综合解决方案，包含高效的数据准备管道和通用的鲁棒反射去除模型。首先引入了多样化反射去除（DRR）数据集，通过在目标场景中随机旋转反射介质来创建，能够变化反射角度和强度。其次提出了基于扩散的框架，采用一步扩散实现确定性输出和快速推理。

---

**- Survey on Single-Image Reflection Removal using Deep Learning Techniques (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2502.08836) | [GitHub]

**简介**: 这是一篇关于使用深度学习技术进行单图像反射去除的综合综述论文，通过关注ICCV、ECCV、CVPR、NeurIPS等重要会议来回顾当前文献。论文遵循结构化的论文选择过程，批判性地评估了单阶段和两阶段深度学习反射去除方法，提供了最新工作的全面总结，并概述了任务假设、当前深度学习技术、公开可用数据集和相关评估指标。

---

**- Single Image Reflection Removal via inter-layer Complementarity (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2505.12641) | [GitHub]

**简介**: 该论文针对双流架构在物理建模和网络设计中未能充分利用层间互补性的问题，提出了两个针对性改进：首先引入新颖的层间互补性模型，其中从残差层提取的低频组件通过双流架构与传输层交互以增强层间互补性；其次提出了高效的层间互补性注意机制，首先在通道级别交叉重组双流以获得具有层间互补结构的重组流，然后对重组流执行注意力计算以实现更好的层间分离。

## 2024
**- A Closer Look at the Reflection Formulation in Single Image Reflection Removal, (IEEE TIP 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10381629) | [arXiv] | [GitHub]

**- Language-guided Image Reflection Separation, (CVPR 2024)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2024/papers/Zhong_Language-guided_Image_Reflection_Separation_CVPR_2024_paper.pdf) | [arXiv](https://arxiv.org/abs/2402.11874) | [GitHub]

**- Revisiting Single Image Reflection Removal In the Wild, (CVPR 2024)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2024/papers/Zhu_Revisiting_Single_Image_Reflection_Removal_In_the_Wild_CVPR_2024_paper.pdf) | [arXiv](https://arxiv.org/abs/2311.17320) | [GitHub](https://github.com/zhuyr97/Reflection_RemoVal_CVPR2024)

**- Single Image Reflection Separation via Dual-Stream Interactive Transformers, (NeurIPS 2024)**  
[PDF](https://openreview.net/forum?id=Shwtw8uV8l) | [arXiv] | [GitHub](https://github.com/mingcv/DSIT)

**- L-DiffER: Single Image Reflection Removal with Language-Based Diffusion Model, (ECCV 2024)**  
[PDF](https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/02988.pdf) | [arXiv] | [GitHub]

**- Reflection Intensity Guided Single Image Reflection Removal and Transmission Recovery, (IEEE TMM 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10314287) | [arXiv] | [GitHub]

**- Hue Guidance Network for Single Image Reflection Removal, (IEEE TNNLS 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10130817) | [arXiv] | [GitHub](https://github.com/zhuyr97/HGRR)

**- Polarized Reflection Removal with Dual-Stream Attention Guidance, (Pattern Recognition 2024)**  
[PDF](https://www.sciencedirect.com/science/article/abs/pii/S0031320324006964) | [arXiv] | [GitHub]

**- Improving Single Image Reflection Removal using Advanced Training Strategies, (ACM MM 2024)**  
[PDF](https://dl.acm.org/doi/10.1145/3664647.3681072) | [arXiv] | [GitHub]

**- DURRNET: Deep Unfolded Single Image Reflection Removal Network with Joint Prior, (ICASSP 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10446674) | [arXiv](https://arxiv.org/abs/2203.06306) | [GitHub](https://github.com/jjhuangcs/DURRNet)

**- Deep Variational Inference Network for Single Image Reflection Removal, (IEEE TETCI 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10432786) | [arXiv] | [GitHub]

**- Spatio-Temporal Multi-Image Reflection Removal, (IEEE SPL 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10669076) | [arXiv] | [GitHub]

**- Fast Single Image Reflection Removal Using Multi-Stage Scale Space Network, (IEEE Access 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10705159) | [arXiv] | [GitHub]

**- Single image reflection removal via self-attention and local discrimination, (The Visual Computer 2024)**  
[PDF](https://link.springer.com/article/10.1007/s00371-024-03333-2) | [arXiv] | [GitHub](https://github.com/HighColdMan/SIRR_SALD)

**- PromptRR: Diffusion Models as Prompt Generators for Single Image Reflection Removal, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2402.02374) | [GitHub](https://github.com/TaoWangzj/PromptRR)

**- Single-image reflection removal via self-supervised diffusion models, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2412.20466) | [GitHub]

**- Benchmarking Ultra-High-Definition Single-Image Reflection Removal, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2308.00265) | [GitHub](https://github.com/Liar-zzy/Benchmarking-Ultra-High-Definition-Single-Image-Reflection-Removal)

**- Towards Flexible Interactive Reflection Removal with Human Guidance, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2406.01555) | [GitHub](https://github.com/ShawnChenn/FlexibleReflectionRemoval)

**- Utilizing Multi-Step Loss for Single Image Reflection Removal, (arXiv 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10912635) | [arXiv](https://arxiv.org/abs/2412.08582) | [GitHub](https://github.com/AbdelrhmanElnenaey/SIRR_MSloss_RefGAN_RDM)

## 2023
**- Single Image Reflection Separation via Component Synergy, (ICCV 2023)**  
[PDF](https://openaccess.thecvf.com/content/ICCV2023/papers/Hu_Single_Image_Reflection_Separation_via_Component_Synergy_ICCV_2023_paper.pdf) | [arXiv](https://arxiv.org/abs/2308.10027) | [GitHub](https://github.com/mingcv/DSRNet)

**- Missing Recovery: Single Image Reflection Removal Based on Auxiliary Prior Learning, (IEEE TIP 2023)**  
[PDF](https://ieeexplore.ieee.org/document/10002393) | [arXiv] | [GitHub]

**- Single Image Reflection Removal From Glass Surfaces Via Multi-Scale Reflection Detection, (IEEE TCE 2023)**  
[PDF](https://ieeexplore.ieee.org/document/10214078) | [arXiv] | [GitHub]

**- Personalized Single Image Reflection Removal Network through Adaptive Cascade Refinement, (ACM MM 2023)**  
[PDF](https://dl.acm.org/doi/10.1145/3581783.3612271) | [arXiv] | [GitHub]

**- Two-stage single image reflection removal with reflection-aware guidance, (Applied Intelligence 2023)**  
[PDF](https://link.springer.com/article/10.1007/s10489-022-04391-6) | [arXiv](https://arxiv.org/abs/2012.00945) | [GitHub](https://github.com/liyucs/RAGNet)

**- Single Image Reflection Removal with Reflection Intensity Prior Knowledge, (arXiv 2023)** *(Preprint)*  
[PDF] | [arXiv](https://arxiv.org/abs/2312.03798) | [GitHub]

**- Robust Single Image Reflection Removal Against Adversarial Attacks, (CVPR 2023)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2023/html/Song_Robust_Single_Image_Reflection_Removal_Against_Adversarial_Attacks_CVPR_2023_paper.html) | [arXiv] | [GitHub](https://github.com/ZhenboSong/RobustSIRR)

## 2022
**- Single Image Reflection Removal Based on Bi-Channels Prior, (ICIP 2022)**  
[PDF](https://ieeexplore.ieee.org/document/9898067) | [arXiv] | [GitHub]

**- Single Image Reflection Removal Based on Knowledge-Distilling Content Disentanglement, (IEEE Signal Processing Letters 2022)**  
[PDF](https://ieeexplore.ieee.org/document/9705543) | [arXiv] | [GitHub](https://github.com/ytpeng-aimlab/Image-Reflection-Removal-based-on-Knowledge-distilling-Content-Disentanglement)

**- FIPHN: Feature-Integrated Patch-Hierarchical Network for Single Image Reflection Removal, (ICPR 2022)**  
[PDF](https://ieeexplore.ieee.org/document/9956721) | [arXiv] | [GitHub]

**- Single-Image Reflection Removal Using Deep Learning: A Systematic Review, (IEEE Access 2022)** *(Survey Paper)*  
[PDF](https://ieeexplore.ieee.org/document/9711234) | [arXiv] | [GitHub]

## 2021
**- Robust Reflection Removal With Reflection-Free Flash-Only Cues, (CVPR 2021)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2021/html/Lei_Robust_Reflection_Removal_With_Reflection-Free_Flash-Only_Cues_CVPR_2021_paper.html) | [arXiv](https://arxiv.org/abs/2103.04273) | [GitHub](https://github.com/ChenyangLEI/flash-reflection-removal)

**- Single Image Reflection Removal with Absorption Effect, (CVPR 2021)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2021/papers/Zheng_Single_Image_Reflection_Removal_With_Absorption_Effect_CVPR_2021_paper.pdf) | [arXiv] | [GitHub](https://github.com/q-zh/absorption)

**- Location-aware Single Image Reflection Removal, (ICCV 2021)**  
[PDF](https://openaccess.thecvf.com/content/ICCV2021/papers/Dong_Location-Aware_Single_Image_Reflection_Removal_ICCV_2021_paper.pdf) | [arXiv](https://arxiv.org/abs/2012.07131) | [GitHub](https://github.com/zdlarr/Location-aware-SIRR)

**- Distilling Reflection Dynamics for Single-Image Reflection Removal, (ICCVW 2021)**  
[PDF](https://openaccess.thecvf.com/content/ICCV2021W/AIM/papers/Zheng_Distilling_Reflection_Dynamics_for_Single-Image_Reflection_Removal_ICCVW_2021_paper.pdf) | [arXiv] | [GitHub]

**- Trash or Treasure? An Interactive Dual-Stream Strategy for Single Image Reflection Separation, (NeurIPS 2021)**  
[PDF](https://proceedings.neurips.cc/paper/2021/file/cf1f78fe923afe05f7597da2be7a3da8-Paper.pdf) | [arXiv](https://arxiv.org/abs/2110.10546) | [GitHub](https://github.com/mingcv/YTMT-Strategy)

**- Deep-Masking Generative Network: A Unified Framework for Separating Superimposed Images, (TIP 2021)**  
[PDF](https://ieeexplore.ieee.org/document/9424463/) | [arXiv](https://arxiv.org/abs/2010.04324) | [GitHub](https://github.com/funkdub/DMGN-Deep-Masking-Generative-Network-TIP2021)

## 2020

**- Single Image Reflection Removal With Physically-Based Training Images, (CVPR 2020)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2020/papers/Kim_Single_Image_Reflection_Removal_With_Physically-Based_Training_Images_CVPR_2020_paper.pdf) | [arXiv](https://arxiv.org/abs/1904.11934) | [GitHub](https://github.com/sookim813/Reflection_removal_rendering)

**- Polarized Reflection Removal with Perfect Alignment in the Wild, (CVPR 2020)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2020/papers/Lei_Polarized_Reflection_Removal_With_Perfect_Alignment_in_the_Wild_CVPR_2020_paper.pdf) | [arXiv](https://arxiv.org/abs/2003.12789) | [GitHub](https://github.com/ChenyangLEI/polarization-reflection-removal)

**- Single Image Reflection Removal through Cascaded Refinement, (CVPR 2020)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2020/papers/Li_Single_Image_Reflection_Removal_Through_Cascaded_Refinement_CVPR_2020_paper.pdf) | [arXiv](https://arxiv.org/abs/1911.06634) | [GitHub](https://github.com/JHL-HUST/IBCLN)

**- Joint Reflection Removal and Depth Estimation From a Single Image, (IEEE Transactions on Cybernetics 2020)**  
[PDF](https://ieeexplore.ieee.org/document/8957259/) | [arXiv] | [GitHub]

**- CoRRN: Cooperative Reflection Removal Network, (IEEE Transactions on Pattern Analysis and Machine Intelligence 2020)**  
[PDF](https://www.ntu.edu.sg/docs/librariesprovider106/publications/image-processing/corrn-cooperative-reflection-removal-network.pdf?sfvrsn=8d56558b_2) | [arXiv] | [GitHub](https://github.com/wanrenjie/CoRRN)

## 2019

**- Fast Single Image Reflection Suppression via Convex Optimization, (CVPR 2019)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Yang_Fast_Single_Image_Reflection_Suppression_via_Convex_Optimization_CVPR_2019_paper.pdf) | [arXiv](https://arxiv.org/abs/1903.03889) | [GitHub](https://github.com/yyhz76/reflectSuppress)

**- Single Image Reflection Removal Exploiting Misaligned Training Data and Network Enhancements, (CVPR 2019)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Wei_Single_Image_Reflection_Removal_Exploiting_Misaligned_Training_Data_and_Network_CVPR_2019_paper.pdf) | [arXiv](https://arxiv.org/abs/1904.00637) | [GitHub](https://github.com/Vandermode/ERRNet)

**- Single Image Reflection Removal Beyond Linearity, (CVPR 2019)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Wen_Single_Image_Reflection_Removal_Beyond_Linearity_CVPR_2019_paper.pdf) | [arXiv] | [GitHub](https://github.com/csqiangwen/Single-Image-Reflection-Removal-Beyond-Linearity)

## 2018

**- ReflectNet: Separating Reflection and Transmission Images in the Wild, (ECCV 2018)**  
[PDF](https://openaccess.thecvf.com/content_ECCV_2018/papers/Patrick_Wieschollek_Separating_Reflection_and_ECCV_2018_paper.pdf) | [arXiv](https://arxiv.org/abs/1712.02099) | [GitHub](https://github.com/NVlabs/ReflectNet)

**- CRRN: Multi-Scale Guided Concurrent Reflection Removal Network, (CVPR 2018)**  
[PDF](https://openaccess.thecvf.com/content_cvpr_2018/papers/Wan_CRRN_Multi-Scale_Guided_CVPR_2018_paper.pdf) | [arXiv](https://arxiv.org/abs/1805.11802) | [GitHub]

**- Single Image Reflection Separation with Perceptual Losses, (CVPR 2018)**  
[PDF](https://openaccess.thecvf.com/content_cvpr_2018/papers/Zhang_Single_Image_Reflection_CVPR_2018_paper.pdf) | [arXiv](https://arxiv.org/abs/1806.05376) | [GitHub](https://github.com/ceciliavision/perceptual-reflection-removal)

**- Seeing Deeply and Bidirectionally: A Deep Learning Approach for Single Image Reflection Removal, (ECCV 2018)**  
[PDF](https://openaccess.thecvf.com/content_ECCV_2018/papers/Jie_Yang_Seeing_Deeply_and_ECCV_2018_paper.pdf) | [arXiv] | [GitHub](https://github.com/yangj1e/bdn-refremv)

## 2017

**- A Generic Deep Architecture for Single Image Reflection Removal and Image Smoothing, (ICCV 2017)**  
[PDF](https://openaccess.thecvf.com/content_ICCV_2017/papers/Fan_A_Generic_Deep_ICCV_2017_paper.pdf) | [arXiv](https://arxiv.org/abs/1708.03474) | [GitHub](https://github.com/fqnchina/CEILNet)

## 2014

**- Single Image Layer Separation using Relative Smoothness, (CVPR 2014)**  
[PDF](http://yu-li.github.io/paper/li_cvpr14_layer.pdf) | [arXiv] | [GitHub](https://github.com/alexch1/ImageProcessing)

## 2013

**- Specular Reflection Separation Using Dark Channel Prior, (CVPR 2013)**  
[PDF](https://openaccess.thecvf.com/content_cvpr_2013/papers/Kim_Specular_Reflection_Separation_2013_CVPR_paper.pdf) | [arXiv] | [GitHub]
