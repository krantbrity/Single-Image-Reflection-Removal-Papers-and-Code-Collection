<details>
<summary><strong>📅 按年份统计(已收集58篇)</strong></summary>
1
## 2025年 (7篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| PAMI | 1 |
| TMM | 1 |
| Scientific Reports | 1 |
| CVPR | 1 |
| arXiv | 3 |

## 2024年 (19篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| IEEE TIP | 1 |
| CVPR | 2 |
| NeurIPS | 1 |
| ECCV | 1 |
| IEEE TMM | 1 |
| IEEE TNNLS | 1 |
| Pattern Recognition | 1 |
| ACM MM | 1 |
| ICASSP | 1 |
| IEEE TETCI | 1 |
| IEEE SPL | 1 |
| IEEE Access | 1 |
| The Visual Computer | 1 |
| arXiv | 6 |

## 2023年 (7篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| ICCV | 1 |
| IEEE TIP | 1 |
| IEEE TCE | 1 |
| ACM MM | 1 |
| Applied Intelligence | 1 |
| CVPR | 1 |
| arXiv | 1 |

## 2022年 (4篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| ICIP | 1 |
| IEEE SPL | 1 |
| ICPR | 1 |
| IEEE Access | 1 |

## 2021年 (6篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| CVPR | 2 |
| ICCV | 1 |
| ICCVW | 1 |
| NeurIPS | 1 |
| IEEE TIP | 1 |

## 2020年 (5篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| CVPR | 3 |
| IEEE Transactions on Cybernetics | 1 |
| IEEE PAMI | 1 |

## 2019年 (3篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| CVPR | 3 |

## 2018年 (4篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| ECCV | 2 |
| CVPR | 2 |

## 2017年 (1篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| ICCV | 1 |

## 2014年 (1篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| CVPR | 1 |

## 2013年 (1篇)
| 期刊/会议 | 论文数量 |
|----------|---------|
| CVPR | 1 |

</details>

<details>
<summary><strong>📊 按期刊会议统计(已收集58篇)</strong></summary>

| 期刊/会议类别 | 期刊/会议名称 | 论文数量 |
|--------------|-------------|---------|
| **顶级CV会议** | CVPR | 16 |
| | ICCV | 3 |
| | ECCV | 3 |
| **顶级ML会议** | NeurIPS | 2 |
| **IEEE顶级期刊** | PAMI | 2 |
| | TIP | 3 |
| **IEEE其他期刊** | TMM | 2 |
| | TNNLS | 1 |
| | TCE | 1 |
| | TETCI | 1 |
| | SPL | 2 |
| | Access | 2 |
| | Transactions on Cybernetics | 1 |
| **其他期刊** | Pattern Recognition | 1 |
| | Applied Intelligence | 1 |
| | Scientific Reports | 1 |
| | The Visual Computer | 1 |
| **其他会议** | ACM MM | 2 |
| | ICASSP | 1 |
| | ICIP | 1 |
| | ICPR | 1 |
| | ICCVW | 1 |
| **预印本** | arXiv | 10 |

</details>

## 2026

**- GenSIRR: Rectifying Latent Space for Generative Single-Image Reflection Removal (CVPR 2026)**  
[PDF] | [arXiv](https://arxiv.org/abs/2512.06358) | [GitHub](https://gensirr.research.mingjia.li/)

**简介**: （摘要翻译）单幅图像反射去除是一个高度病态的问题。现有方法通常难以推理受反射污染区域的组成关系，因此在野外场景中的图像恢复和泛化能力有限。本文将一种用于图像编辑的潜在扩散模型重新构建，使其能够有效感知并处理高度模糊的层叠图像输入，从而生成高质量恢复结果。作者认为，这一转换的难点来自一个关键但长期被忽视的问题：语义编码器的潜空间缺乏内在结构，无法将复合图像理解为其组成层的线性叠加。为此，本文提出三个相互协同的组件：首先，设计反射等变 VAE，使潜空间与反射形成过程中的线性物理规律对齐；其次，引入可学习的任务特定文本嵌入，以绕过自然语言提示的语义模糊性并提供精确引导；最后，提出深度引导的早期分支采样策略，利用生成过程中的随机性选择更有潜力的恢复结果。大量实验表明，该方法在多个基准数据集上达到新的最先进性能，并能较好地泛化到具有挑战性的真实世界场景。

---

**- NTIRE 2026 Challenge on Single Image Reflection Removal in the Wild: Datasets, Results, and Methods (CVPR Workshops 2026)**  
[PDF] | [arXiv](https://arxiv.org/abs/2604.10321) | [GitHub](https://github.com/caijie0620/OpenRR-5k)

**简介**: （摘要翻译）本文回顾并总结了 NTIRE 2026 野外单图像反射去除挑战赛。该挑战赛与 NTIRE 2026 联合举办，旨在鼓励研究者发展在野外场景中进行单图像反射去除的有效方法。与依赖合成数据集的传统挑战不同，本次挑战使用 OpenRR-5k 数据集的高质量真实图像对进行训练和验证，其中包含 5,000 个训练样本、300 个验证样本和 100 个真实世界测试样本。共有 101 支队伍注册参赛，11 支队伍提交了最终结果。获胜方法显著推进了野外反射去除性能，并通过五位该领域专家的视觉评估得到一致认可。本文对挑战赛设置、数据集、参赛方法和结果进行了全面介绍，并讨论了反射去除在真实场景中的关键难点和未来方向。

---

**- ReLo-IRR: Reflection-Guided LoRA Framework for Image Reflection Removal (ICASSP 2026)**  
[ICASSP](https://www.cmsworkshops.com/ICASSP2026/view_paper.php?PaperNum=8093&bare=1) | [Accepted List](https://cmsworkshops.com/ICASSP2026/papers/accepted_papers.php)

**简介**: （未检索到公开摘要）当前可访问的 ICASSP 2026 论文页面仅公开题名、作者、会议场次和报告时间等信息，未提供摘要正文；因此此条暂未替换为摘要翻译。

---

**- ReflexSplit: Single Image Reflection Separation via Layer Fusion-Separation (CVPR 2026)**  
[Project](https://wuw2135.github.io/ReflexSplit-ProjectPage/) | [arXiv](https://arxiv.org/abs/2601.17468) | [GitHub](https://github.com/wuw2135/ReflexSplit)

**简介**: （摘要翻译）单幅图像反射去除任务旨在从一张混合图像中恢复清晰的透射层。然而，现有方法通常将反射去除视为从输入图像到干净图像的直接映射，忽略了透射层和反射层之间复杂的耦合关系，因而在真实场景中容易产生残留反射或结构失真。本文提出 ReflexSplit，一种基于层融合与层分离的单幅图像反射分离框架。该方法认为，传输层和反射层既存在共享的结构信息，也具有各自独立的层特征。为此，ReflexSplit 设计跨尺度门控融合模块以充分利用共享上下文，并引入层融合-分离模块在深层特征中显式区分透射层和反射层。同时，课程式训练策略被用于逐步增强模型的分离能力。实验表明，该方法在多个基准数据集和真实场景图像上取得了优于现有方法的表现。

---

**- SIRR-LMM: Single-image Reflection Removal via Large Multimodal Model (WACV Workshops 2026)**  
[CVF](https://openaccess.thecvf.com/content/WACV2026W/GAIP/html/Guo_SIRR-LMM_Single-image_reflection_removal_via_Large_Multimodal_Model_WACVW_2026_paper.html) | [PDF](https://openaccess.thecvf.com/content/WACV2026W/GAIP/papers/Guo_SIRR-LMM_Single-image_reflection_removal_via_Large_Multimodal_Model_WACVW_2026_paper.pdf) | [arXiv](https://arxiv.org/abs/2601.07209)

**简介**: （摘要翻译）单幅图像反射去除的目标是从包含反射污染的图像中恢复背景透射层。现有方法大多依赖合成数据或特定网络结构，难以泛化到复杂真实场景。本文提出 SIRR-LMM，一种利用大型多模态模型进行单幅图像反射去除的方法。作者首先构建了一个基于路径追踪 3D 玻璃模型的合成数据生成框架，能够在真实背景图像上生成物理精确的反射场景，并支持不同玻璃属性、相机设置和后处理效果。为了适配大型多模态模型，方法将图像层拼接为单一复合输入，并结合联合字幕描述进行训练，同时使用任务特定 LoRA 进行高效微调，而非全参数训练。实验结果表明，SIRR-LMM 在反射去除和反射分离任务上优于现有最先进方法，并展示了大型多模态模型在低层视觉复原任务中的潜力。

---

**- Dereflection: Any Image with Diffusion Priors and Diversified Data (AAAI 2026)**  
[AAAI](https://ojs.aaai.org/index.php/AAAI/article/view/42489) | [PDF](https://ojs.aaai.org/index.php/AAAI/article/download/42489/46450) | [arXiv](https://arxiv.org/abs/2503.17347) | [GitHub](https://github.com/Abuuu122/Dereflection-Any-Image)

**简介**: （摘要翻译）现有反射去除方法通常针对特定场景或特定类型的反射进行设计，在面对复杂真实图像时泛化能力不足。本文提出 Dereflection Any Image，一种面向任意图像的通用反射去除框架。该方法从数据和模型两个方面提升鲁棒性：在数据层面，作者提出多样化反射数据构建流程，通过随机旋转反射介质来生成不同角度、强度和形态的反射，从而构建更具覆盖性的 DRR 数据集；在模型层面，方法利用扩散先验进行图像恢复，并结合一步扩散和条件控制机制，在保持生成质量的同时提高推理效率。大量实验表明，该方法在多种真实场景图像上具有较强泛化能力，并能有效处理不同类型的反射退化。

---

**- GFRRN: Explore the Gaps in Single Image Reflection Removal (arXiv 2026)**  
[PDF] | [arXiv](https://arxiv.org/abs/2602.22695) | [GitHub]

**简介**: （摘要翻译）现有单图像反射去除方法通常存在两个关键差距：一是预训练模型特征与反射去除模型特征之间的语义理解差距，二是合成数据与真实数据之间反射标签不一致所造成的训练差距。为解决这些问题，本文提出 GFRRN。该方法首先采用参数高效微调策略，将可学习的 Mona 层集成到预训练模型中，以缩小预训练特征与任务特征之间的差异并对齐训练方向；随后设计标签生成器，以统一合成数据和真实数据中的反射标签。此外，作者提出高斯自适应频率学习块，用于自适应学习和融合频率先验；并提出动态 Agent 注意力作为窗口注意力的替代方案，以增强全局建模能力。实验结果表明，该方法在多个数据集上取得了具有竞争力的性能。

---

**- FUMO: Prior-Modulated Diffusion for Single Image Reflection Removal (arXiv 2026)**  
[PDF] | [arXiv](https://arxiv.org/abs/2603.19036) | [GitHub]

**简介**: （摘要翻译）扩散模型在图像复原任务中表现出强大的生成能力，但直接用于单图像反射去除时，往往缺乏对空间位置和结构细节的精确控制。本文提出 FUMO，一种先验调制的扩散框架，用于提升反射去除过程中的空间可控性和结构保真度。该方法从混合图像中直接提取两类先验：一类是用于估计空间反射严重程度的强度先验，另一类是通过多尺度残差聚合获得的高频先验，用于捕获细节敏感响应。在训练过程中，FUMO 采用由粗到精的范式：第一阶段将上述先验结合起来进行门控条件残差注入，使模型关注反射主导且结构敏感的区域；第二阶段通过精细化网络在图像空间中校正局部不对齐并锐化细节。实验结果表明，该方法能够在复杂真实场景中获得更稳定、更精细的反射去除结果。

---

**- Complementary Mixture-of-Experts and Complementary Cross-Attention for Single Image Reflection Separation in the Wild (TIP 2026)**  
[DOI](https://doi.org/10.1109/TIP.2026.3659334)

**简介**: （摘要翻译）野外单图像反射分离需要同时恢复透射层和反射层，但由于两层内容在外观和结构上相互混叠，任务具有很强的不适定性。本文提出互补混合专家和互补交叉注意力机制，以增强层间互补关系建模。具体而言，互补混合专家模块通过多个专家分支学习不同退化模式下的层特征，并以互补方式促进透射层与反射层的解耦；互补交叉注意力模块则在两个层分支之间建立交互，使网络能够利用一层的信息辅助另一层的分离。实验表明，该方法能够有效提升野外反射分离中的层间区分能力，并在多个基准上取得优异表现。

---

**- PA-NAFNet: An Improved Nonlinear Activation Free Network with Pyramid Attention for Single Image Reflection Removal (Digital Signal Processing 2026)**  
[ScienceDirect](https://www.sciencedirect.com/science/article/pii/S1051200425004968) | [DOI](https://doi.org/10.1016/j.dsp.2025.105474)

**简介**: （摘要翻译）单幅图像反射去除是图像复原中的重要任务，目标是从包含反射的图像中恢复清晰的透射层。本文提出 PA-NAFNet，一种改进的无非线性激活网络，通过引入金字塔注意力机制提升反射去除效果。该方法在 NAFNet 的基础上增强多尺度特征建模能力，使模型能够更好地捕获不同尺度的反射模式与背景结构。金字塔注意力模块通过聚合多层次上下文信息，加强对反射区域的定位与抑制，同时保持网络的轻量化和高效性。实验结果表明，PA-NAFNet 在多个反射去除基准上取得了优于基线模型的性能，并在计算成本和恢复质量之间取得了较好平衡。

---

**- Explicit Semantic Guidance for Single Image Reflection Removal via Perceptual Influence Modeling (Pattern Recognition 2026)**  
[ScienceDirect](https://www.sciencedirect.com/science/article/pii/S0031320325015444) | [DOI](https://doi.org/10.1016/j.patcog.2025.112881)

**简介**: （摘要翻译）单幅图像反射去除需要从混合图像中分离透射层与反射层，但由于两者在视觉上高度耦合，该任务具有很强的歧义性。本文提出一种基于感知影响建模的显式语义引导方法。作者认为，语义信息能够帮助模型理解图像内容及其与反射区域之间的关系，从而辅助更准确地恢复透射层。该方法通过显式建模不同语义区域对反射去除过程的感知影响，引导网络关注更可能受到反射干扰的区域，并在恢复过程中保持重要结构与语义一致性。实验结果表明，引入显式语义引导能够提升复杂场景中的反射理解能力和透射层恢复质量。

---

**- Depth-Synergized Mamba Meets Memory Experts for All-Day Image Reflection Separation (AAAI 2026)**  
[AAAI](https://ojs.aaai.org/index.php/AAAI/article/view/37386) | [arXiv](https://arxiv.org/abs/2601.00322) | [GitHub](https://github.com/fashyon/DMDNet)

**简介**: （摘要翻译）全天候图像反射分离面临显著挑战，尤其是在日间和夜间场景中，透射层与反射层的对比度可能非常接近，导致两层内容难以区分。本文提出 DMDNet，一种结合深度协同 Mamba 建模与记忆专家机制的反射分离网络。该方法利用深度信息作为结构线索，增强模型对场景几何关系的理解；同时引入 Mamba 结构以高效建模长程依赖，并通过记忆专家模块学习不同光照和退化条件下的反射分离经验。作者还构建了 NightIRS 夜间反射分离数据集，以补充现有数据在夜间场景上的不足。实验结果表明，DMDNet 在全天候尤其是夜间复杂场景中具有更强的分离能力。

---

**- Unified Removal of Raindrops and Reflections: A New Benchmark and A Novel Pipeline (arXiv 2026)**  
[arXiv](https://arxiv.org/abs/2603.16446)

**简介**: （摘要翻译）真实玻璃场景中的图像退化往往并非单一反射或雨滴，而是多种退化同时存在。本文提出统一去除雨滴与反射的 UR³ 任务，并构建相应基准，以促进对真实复杂玻璃退化问题的研究。作者指出，现有方法通常分别处理雨滴去除或反射去除，难以应对二者共存时的复杂耦合退化。为此，本文提出一种新的统一处理流程，旨在同时建模雨滴遮挡、反射叠加和背景恢复之间的关系。实验结果表明，统一建模策略能够更好地适应真实场景中的复合退化，为玻璃表面图像恢复提供了新的研究方向。

---

## 2025

**- DIRS: Single Image Reflection Separation via Deep Feature Interaction (2025)**  
[PDF] | [arXiv] | [GitHub](https://github.com/mingcv/DIRS?tab=readme-ov-file#-dirs-single-image-reflection-separation-via-deep-feature-interaction) | [中文]

**简介**: （未检索到公开摘要）当前可访问的 GitHub 页面仅表明该仓库为 “DIRS: Single Image Reflection Separation via Deep Feature Interaction” 的官方实现，未提供论文摘要正文；因此此条暂未替换为摘要翻译。

---

**- A Lightweight Deep Exclusion Unfolding Network for Single Image Reflection Removal (PAMI 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2503.01938) | [GitHub](https://github.com/jjhuangcs/DExNet) | [中文](https://github.com/krantbrity/Single-Image-Reflection-Removal-Papers-and-Code-Collection/blob/main/Markdown/A%20Lightweight%20Deep%20Exclusion%20Unfolding%20Network%20for%20Single%20Image%20Reflection%20Removal.md)

**简介**: （摘要翻译）单幅图像反射去除是一个不适定问题，现有深度网络虽然取得了较好效果，但往往参数量较大、可解释性有限。本文提出 DExNet，一种轻量级深度排斥展开网络。该方法从反射去除中的排斥先验出发，将迭代稀疏表示和辅助特征更新算法展开为可学习网络结构，并通过参数化形式实现端到端训练。DExNet 引入通用排斥先验，用于识别和惩罚透射层与反射层特征之间的共性，从而增强层间分离能力。实验表明，该方法在多个基准数据集上达到最先进性能，同时仅使用领先方法约 8% 的参数量，兼具有效性、轻量性和可解释性。

---

**- Reversible Decoupling Network for Single Image Reflection Removal (CVPR 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2410.08063) | [GitHub](https://github.com/lime-j/RDNet) | [中文](https://github.com/krantbrity/Single-Image-Reflection-Removal-Papers-and-Code-Collection/blob/main/Markdown/REVERSIBLE%20DECOUPLING%20NETWORK%20FOR%20SINGLE%20IMAGE%20REFLECTION%20REMOVAL.md)

<details>
<summary>完整RDNet结果</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 25.7138 | 0.8501 |
| Postcard | 26.3343 | 0.9221 |
| Solidobject | 26.9457 | 0.9262 |
| Wild | 27.8440 | 0.9173 |
| Nature | 26.3053 | 0.8463 |
| **Overall** | **26.7236** | **0.9173** |

</details>

<details>
<summary>只使用线性矫正器</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 20.9579 | 0.7611 |
| Postcard | 23.1805 | 0.8838 |
| Solidobject | 25.3336 | 0.8977 |
| Wild | 26.1879 | 0.8987 |
| Nature | 22.2390 | 0.7835 |
| **Overall** | **24.2590** | **0.8820** |

</details>

<details>
<summary>无处理基线结果</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 19.2294 | 0.7430 |
| Postcard | 21.3269 | 0.8767 |
| Solidobject | 23.8050 | 0.8831 |
| Wild | 26.1748 | 0.8941 |
| Nature | 20.6916 | 0.7847 |
| **Overall** | **22.7592** | **0.8721** |

</details>

**简介**: （摘要翻译）单幅图像反射去除需要从混合图像中恢复透射层，但现有方法在编码过程中容易丢失有用信息，导致恢复质量受限。本文提出 RDNet，一种可逆解耦网络。该方法采用可逆编码器以保护有价值的信息，并在前向传播过程中灵活解耦与透射层和反射层相关的特征。为进一步增强适应性，RDNet 还设计了传输率感知的提示生成器，用于动态校准特征表示。实验结果表明，RDNet 在五个广泛使用的基准数据集上超过了现有最先进方法，并在 NTIRE 2025 野外单图像反射去除挑战赛中取得最佳性能。

---

**- Removing Reflections from RAW Photos (CVPR 2025 Oral)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2025/papers/Kee_Removing_Reflections_from_RAW_Photos_CVPR_2025_paper.pdf) | [arXiv](https://arxiv.org/abs/2404.14414) | [GitHub](https://erickee.com/reflections/cvpr2025.html)

**简介**: （摘要翻译）从单张照片中去除反射通常具有歧义性，因为一张普通 RGB 图像很难区分反射层和真实场景内容。本文提出在 RAW 图像域中进行反射去除，并可选择输入一张反向拍摄的上下文照片来消除歧义。与在 sRGB 图像上处理不同，RAW 图像保留了更接近线性成像过程的光度信息，有助于更准确地模拟反射混合。该系统仅使用合成 RAW 图像混合进行训练，结合光度和几何上更精确的反射模拟。方法包含一个在低分辨率下运行的基础模型和一个将结果提升到全分辨率的上采样模型，可在普通设备上较快生成预览结果。实验表明，RAW 域训练和模拟数据质量对真实场景反射去除具有重要作用，并优于许多架构层面的改进。

---

**- Flash-Split: 2D Reflection Removal with Flash Cues and Latent Diffusion Separation (CVPR 2025)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_Flash-Split_2D_Reflection_Removal_with_Flash_Cues_and_Latent_Diffusion_CVPR_2025_paper.pdf) | [arXiv](https://arxiv.org/abs/2501.00637) | [GitHub]

**简介**: （摘要翻译）闪光灯能够为反射去除提供有价值的线索，但真实拍摄中的闪光/无闪光图像对常常存在错位，限制了其直接使用。本文提出 Flash-Split，一种鲁棒的两阶段闪光灯反射分离框架，使用一对可能未对齐的闪光和无闪光图像。核心思想是在低维潜空间中利用闪光线索进行反射分离。第一阶段，方法在编码后的闪光/无闪光潜空间对上训练双分支扩散模型，从而缓解图像错位带来的影响；第二阶段，通过以原始图像为条件的跨潜空间解码过程恢复高分辨率细节。实验结果表明，Flash-Split 在具有挑战性的真实场景中显著优于现有基准方法。

---

**- PolarFree: Polarization-based Reflection-Free Imaging (CVPR 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2503.18055) | [GitHub] | [中文]

**简介**: （摘要翻译）偏振信息能够帮助区分透射光和反射光，但现有偏振反射去除数据规模有限，制约了学习型方法的发展。本文提出 PolarFree，一种基于偏振的无反射成像方法，并构建了大规模 PolaRGB 数据集。该数据集包含 6,500 组精确对齐的混合图像与透射图像对，比现有偏振数据集规模大得多，并同时提供 RGB 和偏振信息。方法进一步利用扩散过程生成无反射线索，并结合偏振线索进行反射去除，从而更有效地恢复清晰透射层。实验表明，PolarFree 在复杂反射场景中显著提升了图像清晰度和恢复质量。

---

**- ALANet: Adaptive Language-Aware Image Reflection Removal Network (IJCAI 2025)**  
[IJCAI](https://www.ijcai.org/proceedings/2025/109) | [PDF](https://www.ijcai.org/proceedings/2025/0109.pdf) | [arXiv](https://arxiv.org/abs/2603.06200) | [GitHub](https://github.com/fashyon/ALANet)

**简介**: （摘要翻译）语言引导能够为单图像反射去除提供高层语义信息，但机器生成的图像描述往往不准确，错误语言输入可能误导恢复过程。本文提出 ALANet，即自适应语言感知图像反射去除网络。该方法将过滤与优化两种策略相结合：首先通过语言感知竞争注意力模块降低错误语言输入带来的负面影响；其次利用自适应语言校准模块，根据视觉特征对语言特征进行动态校准。此外，ALANet 设计了语言引导的空间-通道交叉注意力模块，以增强复杂反射场景下的层内容解耦能力。实验结果表明，该方法能够更有效地利用语言信息，并提升反射去除性能。

---

**- NTIRE 2025 Challenge on Single Image Reflection Removal in the Wild: Datasets, Methods and Results (CVPR Workshops 2025)**  
[PDF] | [arXiv] | [GitHub] | [中文]

**简介**: （摘要翻译）本文总结了 NTIRE 2025 野外单图像反射去除挑战赛的设置、数据集、参赛方法和结果。该挑战赛旨在推动真实场景中单图像反射去除方法的发展，并为相关算法提供统一评测平台。挑战赛基于 OpenRR 数据集进行，包含真实世界中的反射图像及其对应无反射图像，强调像素对齐和场景多样性。多支参赛队伍提交了不同技术路线的解决方案，包括双流网络、可逆编码、提示引导和多尺度恢复等。本文比较了各方法在定量指标和视觉质量上的表现，并总结了当前野外反射去除任务中的主要挑战和未来发展方向。

---

**- FIRM: Flexible Interactive Reflection ReMoval (AAAI 2025)**  
[PDF](https://ojs.aaai.org/index.php/AAAI/article/view/32222) | [arXiv](https://arxiv.org/abs/2406.01555) | [GitHub](https://github.com/ShawnChenn/FlexibleReflectionRemoval) | [中文]

**简介**: （摘要翻译）现有反射去除方法通常完全自动运行，难以处理复杂场景中的强反射和高度歧义区域。本文提出 FIRM，一个灵活的交互式反射去除框架，允许用户通过点、框、描边或文本描述等多种形式提供指导，并且所需交互时间仅约为以往交互式方法的 10%。该方法首先使用 segment-any-reflection 模型生成准确的反射掩码，再通过对比引导交互块实现更精确的图像层分离。FIRM 能够根据用户输入自适应调整反射区域识别和去除过程，在多个数据集上达到最先进性能，并展示了用户辅助在复杂反射去除中的实用价值。

---

**- Rethinking Depth Guided Reflection Removal (TMM 2025)**  
[PDF](https://ieeexplore.ieee.org/document/10891560) | [arXiv] | [GitHub] [中文](https://github.com/krantbrity/Single-Image-Reflection-Removal-Papers-and-Code-Collection/blob/main/Markdown/Rethinking%20Depth%20Guided%20Reflection%20Removal.md)

**简介**: （摘要翻译）深度信息被认为能够辅助反射去除，但现有深度引导方法对深度的利用方式仍存在局限。本文重新思考深度引导反射去除问题，并提出一种端到端学习框架。受人类双目视觉系统启发，该方法学习传输层深度，并设计统一结构，以级联方式实现深度引导、跨视图特征增强和跨帧特征增强。作者还构建了包含合成和真实双目混合视频的数据集，用于网络训练和测试。实验结果表明，合理建模深度与多视角/多帧信息之间的关系，可以提升反射去除的结构一致性和真实场景表现。

---

**- High-resolution image reflection removal by Laplacian-based component-aware transformer (Scientific Reports 2025)**  
[PDF](https://www.nature.com/articles/s41598-025-94464-6) | [arXiv] | [GitHub]

**简介**: （摘要翻译）高分辨率图像反射去除需要同时处理细节丰富的背景和复杂高频反射模式。本文提出 LapCAT，一种基于拉普拉斯金字塔的组件感知 Transformer 框架。该方法利用拉普拉斯金字塔将高分辨率图像分解为不同尺度的高频信息和低频信息：高频分支重点去除反射模式，低频分支提供较干净的背景组件作为指导，从而重建高分辨率背景图像。作者进一步设计组件感知 Transformer，通过自注意力机制建模背景与反射组件之间的差异。实验表明，该方法能够有效处理高分辨率图像中的复杂反射，并保持背景细节。

---

**- Benchmarking Ultra-High-Definition Image Reflection Removal (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2308.00265) | [GitHub](https://github.com/Liar-zzy/Benchmarking-Ultra-High-Definition-Single-Image-Reflection-Removal) | [中文]

**简介**: （摘要翻译）尽管单图像反射去除已有大量研究，但超高清图像上的评测和训练数据仍然不足。本文首次构建了两个大规模 UHD 反射去除数据集 UHDRR4K 和 UHDRR8K。UHDRR4K 包含 2,999 个训练四元组和 168 个测试四元组，UHDRR8K 包含 1,014 个训练四元组和 105 个测试四元组。基于这些数据集，作者提出 RRFormer，一种面向 UHD 图像反射去除的 Transformer 架构，包含预处理嵌入模块、自注意力特征提取模块和多尺度空间特征提取模块。实验结果表明，RRFormer 在 UHD 和非 UHD 数据集上均达到最先进性能，并验证了专门针对超高清图像建模的重要性。

---

**- WindowSeat: Reflection Removal through Efficient Adaptation of Diffusion Transformers (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2512.05000) | [GitHub](https://github.com/huawei-bayerlab/windowseat-reflection-removal)

**简介**: （摘要翻译）现有反射去除方法大多依赖任务特定网络结构，难以充分利用基础扩散模型的泛化能力。本文提出 WindowSeat，一种用于单图像反射去除的扩散 Transformer 框架。该方法系统分析了现有反射去除数据源在多样性、可扩展性和光真实性方面的不足，并在 Blender 中构建基于物理的渲染流程，使用 Principled BSDF 合成更真实的玻璃材料和反射效果。在模型层面，WindowSeat 通过 LoRA 高效适配预训练基础扩散模型，而不是从头训练任务特定架构。实验表明，结合高质量合成数据和高效模型适配后，该方法在域内和零样本基准上均取得最先进性能。

---

**- Reflections Unlock: Geometry-Aware Reflection Disentanglement in 3D Gaussian Splatting for Photorealistic Scenes Rendering (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2507.06103) | [GitHub] | [中文]

**简介**: （摘要翻译）在具有反射的真实场景中，3D 高斯泼溅重建往往会将反射错误地整合进几何和外观表示中，影响渲染质量和几何一致性。本文提出 Reflections Unlock，一种几何感知的反射解耦框架，用于照片级真实场景渲染。该方法通过 3D 高斯分层显式分离传输和反射组件，以更好地捕获复杂反射并提升真实场景几何一致性。具体而言，方法采用双分支表示和高阶球谐函数来表示高频反射细节，并结合反射去除模块、伪深度图和几何感知双边平滑约束来增强 3D 几何一致性。实验结果表明，该方法能够在含反射场景中获得更真实、更稳定的渲染效果。

---

**- Survey on Single-Image Reflection Removal using Deep Learning Techniques (MIPR 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2502.08836) | [DOI](https://doi.org/10.1109/MIPR67560.2025.00011)

**简介**: （摘要翻译）单图像反射去除是计算机视觉中的重要问题，近年来深度学习方法显著推动了该领域发展。本文综述了使用深度学习技术进行单图像反射去除的研究进展，重点关注 ICCV、ECCV、CVPR、NeurIPS 等重要会议和相关文献。作者采用结构化的论文选择流程，对单阶段和两阶段深度学习反射去除方法进行批判性评估，并总结了常用任务假设、网络技术、公开数据集和评估指标。该综述还比较了不同方法的优势与局限，讨论了真实场景泛化、数据构建和模型可解释性等未来挑战。

---

**- Single Image Reflection Removal via inter-layer Complementarity (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2505.12641) | [GitHub]

**简介**: （摘要翻译）单图像反射分离旨在从混合图像中分离透射层和反射层。现有方法通常将预训练模型的通用先验与文本提示、反射检测等任务特定先验结合起来。然而，作为目标透射层最直接的任务特定先验，透射先验尚未得到有效建模和充分利用，从而限制了复杂场景下的性能。为此，本文提出一种基于轻量级透射先验生成和有效先验融合的双先验交互框架。首先，设计局部线性校正网络，基于物理约束 T = S I + B 对预训练模型进行微调，其中 S 和 B 分别表示逐像素和逐通道的缩放与偏置变换。该网络能够以极少参数高效生成高质量透射先验。其次，构建双先验交互 Transformer，采用双流通道重组注意力机制，通过重组通用先验和透射先验特征进行注意力计算，实现两类先验的深度融合并利用其互补信息。多个基准数据集上的实验结果表明，该方法达到最先进性能。

<details>
<summary>RTX 4090</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 25.1180 | 0.8276 |
| Postcard | 26.4330 | 0.9307 |
| Solidobject | 27.0718 | 0.9295 |
| Wild | 27.9621 | 0.9216 |
| Nature | 27.0336 | 0.8527 |
| **Overall** | **26.8329** | **0.9219** |

</details>

---

**- OpenRR-5k: A Large-Scale Benchmark for Reflection Removal in the Wild (MIPR 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2506.05482) | [GitHub](https://github.com/caijie0620/OpenRR-5k)

**简介**: （摘要翻译）高质量真实世界数据对野外反射去除至关重要，但现有数据集在规模、多样性和像素对齐方面仍存在不足。本文提出 OpenRR-5k，一个用于野外反射去除的大规模基准数据集，包含 5,300 对高质量、像素对齐的图像对，每对由反射图像和对应无反射图像组成。数据集划分为 5,000 张训练图像、300 张验证图像和 100 张无真值的真实世界测试图像，覆盖多样场景、光照条件、物体类型和反射模式。作者还对多个现有反射去除方法进行基准评测，展示了 OpenRR-5k 在推动真实场景反射去除研究方面的价值。

---

**- OpenRR-1k: A Scalable Dataset for Real-World Reflection Removal (ICIP 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2506.08299) | [GitHub](https://github.com/caijie0620/Reflection-Removal-in-the-Wild)

**简介**: （摘要翻译）真实世界反射去除数据集的构建通常困难且成本较高，尤其需要保证反射图像与无反射图像之间的高质量对齐。本文提出 OpenRR-1k，一种可扩展的真实世界反射去除数据集构建范式。该方法从新的视角采集反射数据，具有方便、低成本、可扩展的特点，同时能够确保图像对具有高质量、良好对齐，并覆盖自然多样的真实场景。基于该范式，作者构建了 OpenRR-1k 数据集，用于支持真实世界单图像反射去除方法的训练和评估。

---

**- F2T2-HiT: A U-Shaped FFT Transformer and Hierarchical Transformer for Reflection Removal (ICIP 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2506.05489)

**简介**: （摘要翻译）真实世界反射通常具有复杂多样的空间结构和频率特征，给单图像反射去除带来挑战。本文提出 F2T2-HiT，一种结合 U 形快速傅立叶变换 Transformer 和分层 Transformer 的反射去除架构。该方法在 UNet 框架内结合 FFT Transformer 块和层次化 Transformer 块，分别用于捕获频域特征和多尺度空间上下文。通过将频率建模与层级特征建模相结合，F2T2-HiT 能够更有效地处理真实场景中复杂多变的反射模式。实验结果表明，该方法在多个反射去除数据集上取得了有竞争力的性能。

---

**- PromptRR: Diffusion Models as Prompt Generators for Single Image Reflection Removal (arXiv 2025)**  
[PDF] | [arXiv](https://arxiv.org/abs/2402.02374) | [GitHub](https://github.com/TaoWangzj/PromptRR)

**简介**: （摘要翻译）现有反射去除方法通常缺乏有效提示来引导模型区分透射层和反射层。本文提出 PromptRR，一种提示引导的反射去除框架，利用频率信息作为新的视觉提示来提升性能。该框架将反射去除过程解耦为提示生成和提示引导恢复两个阶段。在提示生成阶段，方法首先通过提示预训练策略训练频率提示编码器，然后采用扩散模型作为提示生成器，产生高质量的低频和高频提示。在提示引导恢复阶段，这些频率提示被集成到 PromptFormer 网络中，并通过设计的 Transformer 提示块有效引导模型实现更好的反射去除。实验表明，PromptRR 在多个基准上取得了优异表现。

---

**- Single-image Reflection Removal via Self-supervised Diffusion Models (J Supercomputing 2025)**  
[PDF](https://link.springer.com/article/10.1007/s11227-024-06837-9) | [arXiv](https://arxiv.org/abs/2412.20466) | [GitHub]

**简介**: （摘要翻译）配对训练数据难以获取限制了单图像反射去除方法的发展。本文提出一种结合循环一致性和去噪扩散概率模型的自监督反射去除方法，无需配对训练数据即可从单张图像中去除反射。该方法包含反射去除网络和反射合成网络：反射去除网络利用扩散模型对分解过程进行建模并恢复透射图像；反射合成网络则通过非线性注意力机制，利用分离出的组件重新合成输入图像，以形成自监督约束。作者还提出新的博物馆反射去除数据集。实验结果表明，该方法在 SIR²、FRR 和 MRR 数据集上优于现有最先进方法。

---

**- Single Image-Based Reflection Removal via Dual-Stream Multi-Column Reversible Encoding (Applied Sciences 2025)**  
[PDF](https://www.mdpi.com/2076-3417/15/20/11229) | [arXiv] | [GitHub]

**简介**: （摘要翻译）本文提出一种基于双流多列可逆编码的单图像反射去除方法。现有方法在编码过程中可能损失细节信息，并且复杂注意力结构会增加计算成本。为此，作者引入可逆特征编码策略，并结合简化的双流解码结构。可逆 NAFNet 编码器能够在编码过程中保留全部特征信息，同时避免额外内存开销；双流解码器则利用共享编码器特征和跳跃连接，在透射流与反射流之间实现隐式双向信息流。尽管模型采用轻量化结构并省略注意力模块，但实验结果表明，该方法在标准反射去除基准上取得了具有竞争力的表现。

---

**- A Review on Learning Based Image Reflection Removal Algorithms (Intelligent Data Analysis 2025)**  
[PDF](https://journals.sagepub.com/doi/10.3233/IDA-230904) | [arXiv] | [GitHub]

**简介**: （摘要翻译）基于学习的图像反射去除算法已经从早期传统方法发展到以深度学习为主的多种技术路线。本文系统回顾了学习型图像反射去除算法的发展历程，涵盖 CNN、GAN、RNN、Transformer 等不同网络架构及其在反射去除任务中的应用。作者对已有方法的建模思路、网络结构、训练数据和适用场景进行分类总结，并对常用公开数据集和评估指标进行全面梳理。该综述还分析了当前方法在真实场景泛化、数据采集、计算复杂度和评价标准方面的不足，为后续研究提供参考。

---

**- A Wavelet-Guided Deep Unfolding Network for Single Image Reflection Removal (IEEE 2025)**  
[PDF](https://ieeexplore.ieee.org/document/11051128/) | [arXiv] | [GitHub]

**简介**: （摘要翻译）反射伪影通常表现为高频细节扰动，而低频内容相对较少受到影响。基于这一观察，本文提出一种小波引导的深度展开网络，用于单图像反射去除。该方法利用离散小波变换在频域中区分和隔离反射伪影，同时保留透射层信息。通过小波分解，模型能够更有针对性地处理受反射影响严重的高频分量，并减少对低频背景结构的破坏。深度展开网络进一步将这一频率先验融入可学习迭代过程，在可解释性和恢复性能之间取得平衡。实验结果表明，该方法能够有效去除反射并保持图像细节。

---

**- Several Points Are All It Takes: Saluting User-Assisted Single Image Reflection Removal (IEEE Signal Processing Letters 2025)**  
[PDF] | [arXiv] | [GitHub]

**简介**: （摘要翻译）现有用户辅助反射去除方法通常需要密集交互，增加了使用负担。本文提出一种仅依赖少量用户点标注的单图像反射去除方法，证明“几个点”即可为模型提供有效高层先验。方法将用户提供的稀疏点指导转换为统一的对比掩码，为识别混合图像中的反射层和透射层提供明确线索。与需要大量描边或区域标注的交互式方法相比，该方法显著降低了用户标注成本，同时保持较高的反射去除质量。实验结果表明，稀疏用户辅助能够有效提升复杂场景中的反射定位与层分离能力。

---

**- Real-World Image Reflection Removal: An Ultra-High-Definition Dataset and an Efficient Baseline (IEEE 2025)**  
[PDF](https://ieeexplore.ieee.org/document/10804834) | [arXiv] | [GitHub]

**简介**: （摘要翻译，公开页面仅显示摘要片段）现有反射去除数据集分辨率不高，训练数据也严重依赖合成数据，这阻碍了反射去除方法的性能提升，并限制了面向高清图像的有效技术发展。为此，本文引入 Real-world Reflection Removal in 4K（RR4K）数据集。该数据集容量大、分辨率高达 6000×4000 像素，代表了该领域的重要进展，可提供更真实、更高质量的评测基准。基于该数据集，作者还提出一种针对高清图像处理优化的高效单图像反射去除方法。

## 2024
**- A Closer Look at the Reflection Formulation in Single Image Reflection Removal, (IEEE TIP 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10381629) | [arXiv] | [GitHub] | [中文](https://github.com/krantbrity/Single-Image-Reflection-Removal-Papers-and-Code-Collection/blob/main/Markdown/A%20Closer%20Look%20at%20the%20Reflection%20Formulation%20in%20Single%20Image%20Reflection%20Removal.md)

**简介：** 这篇论文深入分析了单图像反射移除中的反射建模公式，重新审视了传统的线性叠加模型在实际场景中的局限性。作者提出了更精确的反射形成机制，并基于新的理论分析设计了改进的去反射算法，在理论和实践上都有重要贡献。

**- Language-guided Image Reflection Separation, (CVPR 2024)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2024/papers/Zhong_Language-guided_Image_Reflection_Separation_CVPR_2024_paper.pdf) | [arXiv](https://arxiv.org/abs/2402.11874) | [GitHub]

**简介：** 这篇论文提出了语言引导的反射分离方法，通过引入语言描述来提供图层内容信息，解决反射分离问题的ill-posed性质。该方法采用跨注意力机制和对比学习策略来构建语言描述与图像层之间的对应关系，使用门控网络设计和随机训练策略来处理可识别层的歧义性。这是首个将自然语言作为先验知识引入反射移除任务的工作。

**- Revisiting Single Image Reflection Removal In the Wild, (CVPR 2024)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2024/papers/Zhu_Revisiting_Single_Image_Reflection_Removal_In_the_Wild_CVPR_2024_paper.pdf) | [arXiv](https://arxiv.org/abs/2311.17320) | [GitHub](https://github.com/zhuyr97/Reflection_RemoVal_CVPR2024)

**简介：** 这项研究从两个角度重新审视了真实世界条件下的单图像反射移除问题：真实反射对的收集流程和真实反射位置的感知。作者设计了一个先进的反射收集流程，能够适应各种真实世界的反射场景并降低收集大规模对齐反射对的成本。构建了名为"野外反射移除"(RRW)的大规模高质量反射数据集，包含超过14,950对高分辨率真实世界反射图像，比前期数据集大45倍。

<details>
<summary>RTX 4090</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 21.9253 | 0.7881 |
| Postcard | 24.2854 | 0.8869 |
| Solidobject | 26.8903 | 0.9253 |
| Wild | 26.8204 | 0.9101 |
| Nature | 26.1442 | 0.8455 |
| **Overall** | **25.6020** | **0.8993** |

</details>

**- Single Image Reflection Separation via Dual-Stream Interactive Transformers, (NeurIPS 2024)**  
[PDF](https://openreview.net/forum?id=Shwtw8uV8l) | [arXiv] | [GitHub](https://github.com/mingcv/DSIT)

**简介：** 这篇论文针对现有双流方法在处理复杂案例时性能显著下降的问题，提出了双流交互变换器(DSIT)设计。具体设计了双注意力交互结构，包含双流自注意力和层感知双流交叉注意力机制，同时捕获层内和层间特征相关性。通过跨架构交互将单流预训练变换器嵌入与双流卷积特征进行调制，提供更丰富的语义先验。

<details>
<summary>RTX 4090</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 25.1854 | 0.8339 |
| Postcard | 26.3838 | 0.9254 |
| Solidobject | 26.8733 | 0.9252 |
| Wild | 27.9013 | 0.9230 |
| Nature | 26.6751 | 0.8470 |
| **Overall** | **26.7142** | **0.9182** |

</details>

**- L-DiffER: Single Image Reflection Removal with Language-Based Diffusion Model, (ECCV 2024)**  
[PDF](https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/02988.pdf) | [arXiv] | [GitHub]

**简介：** 这篇论文引入了L-DiffER，一个专为ill-posed单图像反射移除任务设计的基于语言的扩散模型。为了克服现有基于语言的扩散模型在图像恢复中精确控制和保真度方面的局限性，提出了迭代条件细化策略来解决不准确控制条件的问题。采用多条件约束机制确保图像颜色和结构的恢复保真度，同时保持处理低透射反射的生成能力。

**- Reflection Intensity Guided Single Image Reflection Removal and Transmission Recovery, (IEEE TMM 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10314287) | [arXiv] | [GitHub]

**简介：** 这篇论文提出了一种基于反射强度引导的单图像反射移除和透射恢复方法。通过分析反射强度的空间分布特性，设计了强度感知的网络架构，能够根据不同区域的反射强度自适应地调整去反射策略，在保持透射层细节的同时有效移除各种强度的反射。

**- Hue Guidance Network for Single Image Reflection Removal, (IEEE TNNLS 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10130817) | [arXiv] | [GitHub](https://github.com/zhuyr97/HGRR)

**简介：** 该论文提出了色调引导网络(HGN)用于单图像反射移除。基于颜色理论中色调信息相对稳定的特性，设计了色调引导模块来辅助网络更好地区分反射层和透射层。实验表明该方法在处理具有相似亮度但不同色调的反射透射混合场景时表现出色。

<details>
<summary>RTX 4090</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 23.7821 | 0.8178 |
| Postcard | 23.8513 | 0.9004 |
| Solidobject | 25.1090 | 0.9020 |
| Wild | 27.0477 | 0.8999 |
| Nature | 25.5137 | 0.8270 |
| **Overall** | **24.7809** | **0.8947** |

</details>

**- Polarized Reflection Removal with Dual-Stream Attention Guidance, (Pattern Recognition 2024)**  
[PDF](https://www.sciencedirect.com/science/article/abs/pii/S0031320324006964) | [arXiv] | [GitHub]

**简介：** 这项工作利用偏振成像技术进行反射移除，提出了双流注意力引导的偏振反射移除方法。通过分析不同偏振角度下反射和透射的偏振特性差异，设计了专门的双流网络架构，并引入注意力机制来自适应地融合不同偏振信息，显著提升了复杂场景下的反射移除效果。

**- Improving Single Image Reflection Removal using Advanced Training Strategies, (ACM MM 2024)**  
[PDF](https://dl.acm.org/doi/10.1145/3664647.3681072) | [arXiv] | [GitHub]

**简介：** 这篇论文专注于改进单图像反射移除的训练策略。提出了包括数据增强、损失函数设计、训练调度等在内的一系列先进训练技术，通过系统性的训练策略优化，在不改变网络架构的情况下显著提升现有方法的性能。

**- DURRNET: Deep Unfolded Single Image Reflection Removal Network with Joint Prior, (ICASSP 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10446674) | [arXiv](https://arxiv.org/abs/2203.06306) | [GitHub](https://github.com/jjhuangcs/DURRNet)

**简介：** 该论文提出了深度展开的反射移除网络DURRNet，将传统优化算法的迭代过程展开为深度网络架构。通过引入联合先验知识，包括稀疏性先验和平滑性先验，设计了端到端可训练的深度展开网络，在理论可解释性和实际性能之间取得了很好的平衡。

**- Deep Variational Inference Network for Single Image Reflection Removal, (IEEE TETCI 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10432786) | [arXiv] | [GitHub]

**简介：** 这项工作将变分推理引入单图像反射移除任务，提出了深度变分推理网络。通过建模反射移除过程的不确定性，使用变分自编码器框架来学习反射和透射的概率分布，能够输出多种可能的去反射结果并提供不确定性估计。

**- Spatio-Temporal Multi-Image Reflection Removal, (IEEE SPL 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10669076) | [arXiv] | [GitHub]

**简介：** 该论文扩展了传统的单图像反射移除，提出了时空多图像反射移除方法。通过利用视频序列或多张图像之间的时间和空间相关性，设计了时空一致性约束，能够在移除反射的同时保持时间连贯性，特别适用于视频去反射任务。

**- Fast Single Image Reflection Removal Using Multi-Stage Scale Space Network, (IEEE Access 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10705159) | [arXiv] | [GitHub]

**简介：** 这篇论文关注计算效率，提出了基于多阶段尺度空间网络的快速反射移除方法。通过在不同尺度空间中逐步细化去反射结果，实现了速度和效果的良好平衡，特别适合实时应用场景。

**- Single image reflection removal via self-attention and local discrimination, (The Visual Computer 2024)**  
[PDF](https://link.springer.com/article/10.1007/s00371-024-03333-2) | [arXiv] | [GitHub](https://github.com/HighColdMan/SIRR_SALD)

**简介：** 该工作结合自注意力机制和局部判别学习，提出了新的反射移除框架。自注意力模块帮助网络关注全局结构信息，而局部判别模块则专注于学习局部区域的反射特征，两者结合提升了复杂场景下的去反射性能。

**- PromptRR: Diffusion Models as Prompt Generators for Single Image Reflection Removal, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2402.02374) | [GitHub](https://github.com/TaoWangzj/PromptRR)

**简介：** 这篇论文提出了新颖的提示引导反射移除(PromptRR)框架，使用频率信息作为新的视觉提示来提升反射移除性能。该框架将反射移除过程解耦为提示生成和后续的提示引导恢复。在提示生成阶段，提出了提示预训练策略来训练频率提示编码器，将真实图像编码为低频和高频提示，然后采用扩散模型作为提示生成器。

**- Single-image reflection removal via self-supervised diffusion models, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2412.20466) | [GitHub]

**简介：** 这项工作探索了自监督扩散模型在反射移除中的应用。通过设计自监督训练策略，使扩散模型能够在没有配对训练数据的情况下学习反射移除任务，为解决训练数据稀缺问题提供了新的思路。

**- Benchmarking Ultra-High-Definition Single-Image Reflection Removal, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2308.00265) | [GitHub](https://github.com/Liar-zzy/Benchmarking-Ultra-High-Definition-Single-Image-Reflection-Removal)

**简介：** 该论文专注于超高清图像的反射移除基准测试。构建了首个大规模超高清反射移除数据集，并对现有方法在超高清图像上的性能进行了全面评估，指出了当前方法在处理高分辨率图像时面临的挑战和机遇。

**- Towards Flexible Interactive Reflection Removal with Human Guidance, (arXiv 2024)**  
[PDF] | [arXiv](https://arxiv.org/abs/2406.01555) | [GitHub](https://github.com/ShawnChenn/FlexibleReflectionRemoval)

**简介：** 这项工作提出了灵活的交互式反射移除方法，利用人类指导来解决反射移除的固有歧义性。通过整合点击、边界框等多种形式的稀疏人类指导作为高级先验，设计了交互式的反射移除框架，能够根据用户意图生成个性化的去反射结果。

**- Utilizing Multi-Step Loss for Single Image Reflection Removal, (arXiv 2024)**  
[PDF](https://ieeexplore.ieee.org/document/10912635) | [arXiv](https://arxiv.org/abs/2412.08582) | [GitHub](https://github.com/AbdelrhmanElnenaey/SIRR_MSloss_RefGAN_RDM)

**简介：** 该论文提出了多步损失函数用于单图像反射移除。通过在训练过程中的不同阶段使用不同的损失函数组合，能够更好地指导网络学习从粗糙到精细的反射移除过程，提升了最终的去反射质量。

## 2023
**- Single Image Reflection Separation via Component Synergy, (ICCV 2023)**  
[PDF](https://openaccess.thecvf.com/content/ICCV2023/papers/Hu_Single_Image_Reflection_Separation_via_Component_Synergy_ICCV_2023_paper.pdf) | [arXiv](https://arxiv.org/abs/2308.10027) | [GitHub](https://github.com/mingcv/DSRNet)

**简介：** 这篇论文基于对现有模型缺陷的深入分析，提出了一种更通用的叠加模型形式，通过引入可学习的残差项来有效捕获分解过程中的残余信息，指导分离后的图层更加完整。为了充分发挥其优势，作者进一步精心设计了网络结构，包括新颖的双流交互机制和配备语义金字塔编码器的强大分解网络。

<details>
<summary>RTX 4090</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 23.8455 | 0.8091 |
| Postcard | 24.7225 | 0.9147 |
| Solidobject | 26.8810 | 0.9226 |
| Wild | 27.0383 | 0.9145 |
| Nature | 25.2681 | 0.8356 |
| **Overall** | **25.8408** | **0.9104** |

</details>

**- Missing Recovery: Single Image Reflection Removal Based on Auxiliary Prior Learning, (IEEE TIP 2023)**  
[PDF](https://ieeexplore.ieee.org/document/10002393) | [arXiv] | [GitHub]

**简介：** 该论文提出了基于辅助先验学习的单图像反射移除方法，专注于恢复因反射而缺失的图像信息。通过设计辅助先验学习机制，网络能够更好地理解和恢复被反射遮挡的背景细节，特别是在处理强反射和复杂场景时表现出色。

**- Single Image Reflection Removal From Glass Surfaces Via Multi-Scale Reflection Detection, (IEEE TCE 2023)**  
[PDF](https://ieeexplore.ieee.org/document/10214078) | [arXiv] | [GitHub]

**简介：** 这项工作专门针对玻璃表面的反射移除问题，提出了多尺度反射检测方法。通过在不同尺度上检测和定位反射区域，能够更精确地识别反射成分的分布特征，从而实现更有效的反射移除，特别适用于玻璃幕墙、窗户等场景。

**- Personalized Single Image Reflection Removal Network through Adaptive Cascade Refinement, (ACM MM 2023)**  
[PDF](https://dl.acm.org/doi/10.1145/3581783.3612271) | [arXiv] | [GitHub]

**简介：** 该论文提出了个性化的单图像反射移除网络，通过自适应级联细化实现针对不同场景的定制化处理。网络能够根据输入图像的特征自动调整处理策略，为不同类型的反射模式提供个性化的解决方案。

**- Two-stage single image reflection removal with reflection-aware guidance, (Applied Intelligence 2023)**  
[PDF](https://link.springer.com/article/10.1007/s10489-022-04391-6) | [arXiv](https://arxiv.org/abs/2012.00945) | [GitHub](https://github.com/liyucs/RAGNet)

**简介：** 这项工作提出了两阶段的反射移除框架，配备反射感知引导机制。第一阶段粗略分离反射和透射层，第二阶段通过反射感知引导进行精细化处理，确保在保持透射层质量的同时彻底移除反射成分。

**- Single Image Reflection Removal with Reflection Intensity Prior Knowledge, (arXiv 2023)** *(Preprint)*  
[PDF] | [arXiv](https://arxiv.org/abs/2312.03798) | [GitHub]

**简介：** 该预印本论文利用反射强度先验知识来改进单图像反射移除效果。通过分析反射强度的物理特性和分布规律，为网络提供额外的先验约束，提高反射检测和移除的准确性。

**- Robust Single Image Reflection Removal Against Adversarial Attacks, (CVPR 2023)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2023/html/Song_Robust_Single_Image_Reflection_Removal_Against_Adversarial_Attacks_CVPR_2023_paper.html) | [arXiv] | [GitHub](https://github.com/ZhenboSong/RobustSIRR)

**简介：** 这篇论文首次关注深度学习反射移除方法的对抗鲁棒性问题。针对当前方法在面对微小扰动时性能显著下降的问题，提出了集成跨尺度注意力模块、多尺度融合模块和对抗图像判别器的鲁棒反射移除模型，显著提升了方法在对抗攻击下的稳定性。

## 2022
**- Single Image Reflection Removal Based on Bi-Channels Prior, (ICIP 2022)**  
[PDF](https://ieeexplore.ieee.org/document/9898067) | [arXiv] | [GitHub]

**简介：** 该论文提出了基于双通道先验的单图像反射移除方法。通过利用图像在不同通道（如RGB、YUV等）中的差异特性，为反射和透射的分离提供额外的约束条件，提高分离的准确性和鲁棒性。

**- Single Image Reflection Removal Based on Knowledge-Distilling Content Disentanglement, (IEEE Signal Processing Letters 2022)**  
[PDF](https://ieeexplore.ieee.org/document/9705543) | [arXiv] | [GitHub](https://github.com/ytpeng-aimlab/Image-Reflection-Removal-based-on-Knowledge-distilling-Content-Disentanglement)

**简介：** 这项工作将知识蒸馏技术引入反射移除任务，提出了基于知识蒸馏的内容解耦方法。通过教师网络向学生网络传递反射分离的知识，实现更高效和准确的内容解耦。

**- FIPHN: Feature-Integrated Patch-Hierarchical Network for Single Image Reflection Removal, (ICPR 2022)**  
[PDF](https://ieeexplore.ieee.org/document/9956721) | [arXiv] | [GitHub]

**简介：** 该论文提出了特征集成的补丁层次网络(FIPHN)，通过分层处理不同尺度的图像补丁，并集成多层次特征信息，实现更精细的反射移除效果。

**- Single-Image Reflection Removal Using Deep Learning: A Systematic Review, (IEEE Access 2022)** *(Survey Paper)*  
[PDF](https://ieeexplore.ieee.org/document/9711234) | [arXiv] | [GitHub]

**简介：** 这是一篇系统性的综述论文，全面回顾了基于深度学习的单图像反射移除方法。论文系统性地分析了不同方法的优缺点，总结了该领域的发展趋势和面临的挑战，为研究者提供了宝贵的参考。

## 2021
**- Robust Reflection Removal With Reflection-Free Flash-Only Cues, (CVPR 2021)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2021/html/Lei_Robust_Reflection_Removal_With_Reflection-Free_Flash-Only_Cues_CVPR_2021_paper.html) | [arXiv](https://arxiv.org/abs/2103.04273) | [GitHub](https://github.com/ChenyangLEI/flash-reflection-removal)

**简介：** 这篇论文提出了利用闪光灯照明的创新方法来辅助反射移除。通过分析闪光灯照明下反射和透射成分的不同响应特性，设计了基于闪光线索的鲁棒反射移除算法，在实际拍摄场景中表现出色。

**- Single Image Reflection Removal with Absorption Effect, (CVPR 2021)**  
[PDF](https://openaccess.thecvf.com/content/CVPR2021/papers/Zheng_Single_Image_Reflection_Removal_With_Absorption_Effect_CVPR_2021_paper.pdf) | [arXiv] | [GitHub](https://github.com/q-zh/absorption)

**简介：** 该论文考虑了玻璃材质的吸收效应对反射成像的影响，提出了更物理准确的反射成像模型。通过建模光线在玻璃中的吸收和散射过程，实现了更精确的反射移除效果。

**- Location-aware Single Image Reflection Removal, (ICCV 2021)**  
[PDF](https://openaccess.thecvf.com/content/ICCV2021/papers/Dong_Location-Aware_Single_Image_Reflection_Removal_ICCV_2021_paper.pdf) | [arXiv](https://arxiv.org/abs/2012.07131) | [GitHub](https://github.com/zdlarr/Location-aware-SIRR)

**简介：** 这项工作提出了位置感知的反射移除方法，通过显式建模反射在图像中的空间分布特征，为网络提供位置先验信息。该方法能够更好地处理局部反射和不均匀反射分布的情况。

<details>
<summary>RTX 4090</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 23.0750 | 0.8255 |
| Postcard | 24.2698 | 0.9071 |
| Solidobject | 24.1561 | 0.8993 |
| Wild | 26.0274 | 0.8997 |
| Nature | 23.6571 | 0.8194 |
| **Overall** | **24.3463** | **0.8963** |

</details>

**- Distilling Reflection Dynamics for Single-Image Reflection Removal, (ICCVW 2021)**  
[PDF](https://openaccess.thecvf.com/content/ICCV2021W/AIM/papers/Zheng_Distilling_Reflection_Dynamics_for_Single-Image_Reflection_Removal_ICCVW_2021_paper.pdf) | [arXiv] | [GitHub]

**简介：** 该论文提出了反射动态蒸馏的概念，通过分析反射的动态特性（如时间变化、空间变化等），设计了相应的蒸馏策略来提升反射移除的效果。

**- Trash or Treasure? An Interactive Dual-Stream Strategy for Single Image Reflection Separation, (NeurIPS 2021)**  
[PDF](https://proceedings.neurips.cc/paper/2021/file/cf1f78fe923afe05f7597da2be7a3da8-Paper.pdf) | [arXiv](https://arxiv.org/abs/2110.10546) | [GitHub](https://github.com/mingcv/YTMT-Strategy)

**简介：** 这篇论文提出了交互式双流策略，通过让两个分支网络进行"协作-竞争"的交互学习，其中一个分支的"垃圾"输出可能恰好是另一个分支需要的"宝藏"，从而实现更有效的反射和透射分离。

**- Deep-Masking Generative Network: A Unified Framework for Separating Superimposed Images, (TIP 2021)**  
[PDF](https://ieeexplore.ieee.org/document/9424463/) | [arXiv](https://arxiv.org/abs/2010.04324) | [GitHub](https://github.com/funkdub/DMGN-Deep-Masking-Generative-Network-TIP2021)

**简介：** 该论文提出了深度掩码生成网络(DMGN)，这是一个用于分离叠加图像的统一框架。通过生成式建模和深度掩码机制，能够处理包括反射移除在内的多种图像分离任务。

## 2020

**- Single Image Reflection Removal With Physically-Based Training Images, (CVPR 2020)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2020/papers/Kim_Single_Image_Reflection_Removal_With_Physically-Based_Training_Images_CVPR_2020_paper.pdf) | [arXiv](https://arxiv.org/abs/1904.11934) | [GitHub](https://github.com/sookim813/Reflection_removal_rendering)

**简介：** 这篇论文首次提出使用基于物理的渲染技术生成训练数据，解决了真实反射数据稀缺的问题。通过准确建模光线传播、折射和反射的物理过程，生成了大量高质量的训练样本。

**- Polarized Reflection Removal with Perfect Alignment in the Wild, (CVPR 2020)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2020/papers/Lei_Polarized_Reflection_Removal_With_Perfect_Alignment_in_the_Wild_CVPR_2020_paper.pdf) | [arXiv](https://arxiv.org/abs/2003.12789) | [GitHub](https://github.com/ChenyangLEI/polarization-reflection-removal)

**简介：** 该论文利用偏振成像技术进行反射移除，提出了野外环境下的完美对齐偏振反射移除方法。通过分析不同偏振角度下的图像特征，实现了高质量的反射移除效果。

**- Single Image Reflection Removal through Cascaded Refinement, (CVPR 2020)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2020/papers/Li_Single_Image_Reflection_Removal_Through_Cascaded_Refinement_CVPR_2020_paper.pdf) | [arXiv](https://arxiv.org/abs/1911.06634) | [GitHub](https://github.com/JHL-HUST/IBCLN)

**简介：** 这项工作提出了级联细化的反射移除框架，通过多个级联的细化模块逐步提升反射移除的质量。每个级联阶段都专注于不同层次的细节恢复和反射抑制。

<details>
<summary>RTX 4090</summary>

| Dataset | PSNR | SSIM |
|---------|------|------|
| Real | 21.8540 | 0.7770 |
| Postcard | 23.4470 | 0.8790 |
| Solidobject | 24.9473 | 0.8991 |
| Wild | 24.3465 | 0.8862 |
| Nature | 24.0265 | 0.7980 |
| **Overall** | **24.1135** | **0.8805** |

</details>

**- Joint Reflection Removal and Depth Estimation From a Single Image, (IEEE Transactions on Cybernetics 2020)**  
[PDF](https://ieeexplore.ieee.org/document/8957259/) | [arXiv] | [GitHub]

**简介：** 该论文将反射移除与深度估计结合，提出了联合优化框架。通过利用深度信息约束反射分离过程，同时反射移除的结果也能改善深度估计的准确性，实现了两个任务的互相促进。

**- CoRRN: Cooperative Reflection Removal Network, (IEEE Transactions on Pattern Analysis and Machine Intelligence 2020)**  
[PDF](https://www.ntu.edu.sg/docs/librariesprovider106/publications/image-processing/corrn-cooperative-reflection-removal-network.pdf?sfvrsn=8d56558b_2) | [arXiv] | [GitHub](https://github.com/wanrenjie/CoRRN)

**简介：** 这篇论文提出了协作式反射移除网络(CoRRN)，通过设计多个协作的子网络，每个子网络专注于不同的任务（如边缘保持、细节恢复等），通过协作机制实现高质量的反射移除。

## 2019

**- Fast Single Image Reflection Suppression via Convex Optimization, (CVPR 2019)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Yang_Fast_Single_Image_Reflection_Suppression_via_Convex_Optimization_CVPR_2019_paper.pdf) | [arXiv](https://arxiv.org/abs/1903.03889) | [GitHub](https://github.com/yyhz76/reflectSuppress)

**简介：** 该论文提出了基于凸优化的快速反射抑制方法，将反射移除问题转化为凸优化问题求解。相比于深度学习方法，该方法计算效率更高，并且具有良好的理论保证。

**- Single Image Reflection Removal Exploiting Misaligned Training Data and Network Enhancements, (CVPR 2019)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Wei_Single_Image_Reflection_Removal_Exploiting_Misaligned_Training_Data_and_Network_CVPR_2019_paper.pdf) | [arXiv](https://arxiv.org/abs/1904.00637) | [GitHub](https://github.com/Vandermode/ERRNet)

**简介：** 这项工作创新性地利用了未对齐的训练数据，并提出了相应的网络增强技术。通过设计能够处理数据不对齐问题的网络架构，缓解了高质量配对训练数据稀缺的问题。

**- Single Image Reflection Removal Beyond Linearity, (CVPR 2019)**  
[PDF](https://openaccess.thecvf.com/content_CVPR_2019/papers/Wen_Single_Image_Reflection_Removal_Beyond_Linearity_CVPR_2019_paper.pdf) | [arXiv] | [GitHub](https://github.com/csqiangwen/Single-Image-Reflection-Removal-Beyond-Linearity)

**简介：** 该论文突破了传统线性叠加模型的限制，提出了超越线性的反射移除方法。通过建模非线性的反射成像过程，能够更准确地处理复杂的反射现象。

## 2018

**- ReflectNet: Separating Reflection and Transmission Images in the Wild, (ECCV 2018)**  
[PDF](https://openaccess.thecvf.com/content_ECCV_2018/papers/Patrick_Wieschollek_Separating_Reflection_and_ECCV_2018_paper.pdf) | [arXiv](https://arxiv.org/abs/1712.02099) | [GitHub](https://github.com/NVlabs/ReflectNet)

**简介：** ReflectNet是野外环境下反射和透射图像分离的开创性工作之一。该方法提出了端到端的深度学习框架，能够在复杂的真实世界场景中实现有效的反射移除。

**- CRRN: Multi-Scale Guided Concurrent Reflection Removal Network, (CVPR 2018)**  
[PDF](https://openaccess.thecvf.com/content_cvpr_2018/papers/Wan_CRRN_Multi-Scale_Guided_CVPR_2018_paper.pdf) | [arXiv](https://arxiv.org/abs/1805.11802) | [GitHub]

**简介：** 该论文提出了多尺度引导的并发反射移除网络(CRRN)，通过在多个尺度上并发处理反射移除任务，能够更好地捕获不同尺度的反射特征。

**- Single Image Reflection Separation with Perceptual Losses, (CVPR 2018)**  
[PDF](https://openaccess.thecvf.com/content_cvpr_2018/papers/Zhang_Single_Image_Reflection_CVPR_2018_paper.pdf) | [arXiv](https://arxiv.org/abs/1806.05376) | [GitHub](https://github.com/ceciliavision/perceptual-reflection-removal)

**简介：** 这项工作将感知损失引入反射分离任务，通过利用预训练网络的高层特征来衡量图像的感知质量，显著提升了反射移除结果的视觉效果。

**- Seeing Deeply and Bidirectionally: A Deep Learning Approach for Single Image Reflection Removal, (ECCV 2018)**  
[PDF](https://openaccess.thecvf.com/content_ECCV_2018/papers/Jie_Yang_Seeing_Deeply_and_ECCV_2018_paper.pdf) | [arXiv] | [GitHub](https://github.com/yangj1e/bdn-refremv)

**简介：** 该论文提出了双向深度网络，通过深度和双向的信息流动来处理反射移除任务。网络能够同时考虑前向和后向的信息传播，提升分离效果。

## 2017

**- A Generic Deep Architecture for Single Image Reflection Removal and Image Smoothing, (ICCV 2017)**  
[PDF](https://openaccess.thecvf.com/content_ICCV_2017/papers/Fan_A_Generic_Deep_ICCV_2017_paper.pdf) | [arXiv](https://arxiv.org/abs/1708.03474) | [GitHub](https://github.com/fqnchina/CEILNet)

**简介：** 这是较早期的深度学习反射移除工作之一，提出了通用的深度架构来处理反射移除和图像平滑任务。该方法为后续的深度学习方法奠定了基础。

## 2014

**- Single Image Layer Separation using Relative Smoothness, (CVPR 2014)**  
[PDF](http://yu-li.github.io/paper/li_cvpr14_layer.pdf) | [arXiv] | [GitHub](https://github.com/alexch1/ImageProcessing)

**简介：** 该论文提出了基于相对平滑性的单图像层分离方法，是早期的重要工作之一。通过分析反射层和透射层的平滑性差异，设计了相应的分离算法。

## 2013

**- Specular Reflection Separation Using Dark Channel Prior, (CVPR 2013)**  
[PDF](https://openaccess.thecvf.com/content_cvpr_2013/papers/Kim_Specular_Reflection_Separation_2013_CVPR_paper.pdf) | [arXiv] | [GitHub]

**简介：** 这篇论文利用暗通道先验进行镜面反射分离，是较早将图像去雾领域的暗通道先验技术应用到反射移除问题的工作，为该领域提供了新的研究思路。
