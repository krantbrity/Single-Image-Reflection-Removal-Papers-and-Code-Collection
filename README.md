## 2025

**- A Lightweight Deep Exclusion Unfolding Network for Single Image Reflection Removal (PAMI 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2503.01938) | [GitHub](https://github.com/jjhuangcs/DExNet)

<details>
<summary>📖 <strong>点击查看摘要</strong></summary>

**Abstract**
Single Image Reflection Removal (SIRR) is a canonical blind source separation problem and refers to the issue of separating a reflection-contaminated image into a transmission and a reflection image. The core challenge lies in minimizing the commonalities among different sources. Existing deep learning approaches either neglect the significance of feature interactions or rely on heuristically designed architectures. In this paper, we propose a novel Deep Exclusion unfolding Network (DExNet), a lightweight, interpretable, and effective network architecture for SIRR. DExNet is principally constructed by unfolding and parameterizing a simple iterative Sparse and Auxiliary Feature Update (i-SAFU) algorithm, which is specifically designed to solve a new model-based SIRR optimization formulation incorporating a general exclusion prior. This general exclusion prior enables the unfolded SAFU module to inherently identify and penalize commonalities between the transmission and reflection features, ensuring more accurate separation. The principled design of DExNet not only enhances its interpretability but also significantly improves its performance. Comprehensive experiments on four benchmark datasets demonstrate that DExNet achieves state-of-the-art visual and quantitative results while utilizing only approximately 8% of the parameters required by leading methods.

</details>

---

# Reversible Decoupling Network for Single Image Reflection Removal (CVPR 2025)

## 📚 Resources
- **[PDF]** - [arXiv](https://arxiv.org/abs/2410.08063) - [GitHub](https://github.com/lime-j/RDNet)

## 📖 Abstract

<details>
<summary><strong>Click to view abstract</strong></summary>

Recent deep-learning-based approaches to single-image reflection removal have shown promising advances, primarily for two reasons: 1) the utilization of recognition-pretrained features as inputs, and 2) the design of dual-stream interaction networks. However, according to the Information Bottleneck principle, high-level semantic clues tend to be compressed or discarded during layer-by-layer propagation. Additionally, interactions in dual-stream networks follow a fixed pattern across different layers, limiting overall performance. 

To address these limitations, we propose a novel architecture called **Reversible Decoupling Network (RDNet)**, which employs a reversible encoder to secure valuable information while flexibly decoupling transmission- and reflection-relevant features during the forward pass. Furthermore, we customize a transmission-rate-aware prompt generator to dynamically calibrate features, further boosting performance. 

Extensive experiments demonstrate the superiority of RDNet over existing SOTA methods on five widely-adopted benchmark datasets. RDNet achieves the best performance in the **NTIRE 2025 Single Image Reflection Removal in the Wild Challenge** in both fidelity and perceptual comparison.

</details>

## 🚀 Performance Results

<details>
<summary><strong>Click to view RTX4090 pretrained weights test results</strong></summary>

### Test Results on RTX4090 with Pretrained Weights

| Dataset | PSNR | SSIM |
|---------|------|------|
| **Real** | 25.7138 | 0.8501 |
| **Postcard** | 26.3343 | 0.9221 |
| **Solidobject** | 26.9457 | 0.9262 |
| **Wild** | 27.8440 | 0.9173 |
| **Nature** | 26.3053 | 0.8463 |
| **Overall** | **26.7236** | **0.9173** |

### Key Highlights
- 🏆 Best performance in NTIRE 2025 Challenge
- 📊 Consistent high performance across all benchmark datasets
- 💪 Superior SOTA results on five widely-adopted benchmarks
- 🔬 Novel reversible encoder architecture for information preservation

</details>

---

**- Rethinking Depth Guided Reflection Removal (TMM 2025)**  
[PDF](https://ieeexplore.ieee.org/document/10891560) | [arXiv] | [GitHub]

<details>
<summary>📖 <strong>点击查看摘要</strong></summary>

**Abstract**
> **注：** 完整摘要未能从搜索结果中获取

When photographing through glass, reflections are often observed, which negatively impact the quality of the captured images or videos. In this paper, we summarize and rethink depth guided reflection removal methods and, inspired by the human binocular vision system, investigate how to utilize depth for effective binocular video reflection removal. We propose an end-to-end learning-based reflection removal method that learns the transmission depth and designs a unified structure to achieve depth guided, cross-view, and cross-frame feature enhancement in a cascaded manner. The method appears to focus on utilizing depth information from binocular vision systems for more effective reflection removal in video sequences.

</details>

---

**- High-resolution image reflection removal by Laplacian-based component-aware transformer (Scientific Reports 2025)**  
[PDF](https://www.nature.com/articles/s41598-025-94464-6) | [arXiv] | [GitHub]

<details>
<summary>📖 <strong>点击查看摘要</strong></summary>

**Abstract**
Recent data-driven deep learning methods for image reflection removal have made impressive progress, promoting the quality of photo capturing and scene understanding. Due to the massive consumption of computational complexity and memory usage, the performance of these methods degrades significantly while dealing with high-resolution images. Besides, most existing methods for reflection removal can only remove reflection patterns by downsampling the input image into a much lower resolution, resulting in the loss of plentiful information. In this paper, we propose a novel transformer-based framework for high-resolution image reflection removal, termed as the Laplacian pyramid-based component-aware transformer (LapCAT). LapCAT leverages a Laplacian pyramid network to remove high-frequency reflection patterns and reconstruct the high-resolution background image guided by the clean low-frequency background components. The method addresses the computational challenges of processing high-resolution images while maintaining quality through a specialized transformer architecture.

</details>

---

**- Dereflection: Any Image with Diffusion Priors and Diversified Data (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2503.17347) | [GitHub](https://github.com/Abuuu122/Dereflection-Any-Image)

<details>
<summary>📖 <strong>点击查看摘要</strong></summary>

**Abstract**
Reflection removal of a single image remains a highly challenging task due to the complex entanglement between target scenes and unwanted reflections. Despite significant progress, existing methods are hindered by the scarcity of high-quality, diverse data and insufficient restoration priors, resulting in limited generalization across various real-world scenarios. In this paper, we propose Dereflection Any Image, a comprehensive solution with an efficient data preparation pipeline and a generalizable model for robust reflection removal. First, we introduce a dataset named Diverse Reflection Removal (DRR) created by randomly rotating reflective mediums in target scenes, enabling variation of reflection angles and intensities, and setting a new benchmark in scale, quality, and diversity. Second, we propose a diffusion-based framework with one-step diffusion for deterministic outputs and fast inference. The approach combines advanced diffusion models with a carefully designed dataset to address the generalization challenges in reflection removal.

</details>

---

**- Survey on Single-Image Reflection Removal using Deep Learning Techniques (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2502.08836) | [GitHub]

<details>
<summary>📖 <strong>点击查看摘要</strong></summary>

**Abstract**
The phenomenon of reflection is quite common in digital images, posing significant challenges for various applications such as computer vision, photography, and image processing. Traditional methods for reflection removal often struggle to achieve clean results while maintaining high fidelity and robustness, particularly in real-world scenarios. Over the past few decades, numerous deep learning-based approaches for reflection removal have emerged, yielding impressive results. In this survey, we conduct a comprehensive review of the current literature by focusing on key venues such as ICCV, ECCV, CVPR, NeurIPS, etc., as these conferences and journals have been central to advances in the field. The contribution of this survey is three-fold: first, we provide a comprehensive summary of the most recent work on single-image reflection removal; second, we outline task hypotheses, current deep learning techniques, publicly available datasets, and relevant evaluation metrics; and third, we identify key challenges and opportunities in deep learning-based reflection removal, highlighting the potential of this rapidly evolving research area.

</details>

---

**- Single Image Reflection Removal via inter-layer Complementarity (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2505.12641) | [GitHub]

<details>
<summary>📖 <strong>点击查看摘要</strong></summary>

**Abstract**
Although dual-stream architectures have achieved remarkable success in single image reflection removal, they fail to fully exploit inter-layer complementarity in their physical modeling and network design, which limits the quality of image separation. To address this fundamental limitation, we propose two targeted improvements to enhance dual-stream architectures: First, we introduce a novel inter-layer complementarity model where low-frequency components extracted from the residual layer interact with the transmission layer through dual-stream architecture to enhance inter-layer complementarity. Meanwhile, high-frequency components from the residual layer provide inverse modulation to both streams, improving the detail quality of the transmission layer. Second, we propose an efficient inter-layer complementarity attention mechanism which first cross-reorganizes dual streams at the channel level to obtain reorganized streams with inter-layer complementary structures, then performs attention computation on the reorganized streams to achieve better inter-layer separation, and finally restores the original stream structure for output. Experimental results demonstrate that our method achieves state-of-the-art separation quality on multiple public datasets while significantly reducing both computational cost and model complexity.

</details>

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
