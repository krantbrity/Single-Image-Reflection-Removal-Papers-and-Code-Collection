# 单图像反射去除中反射公式的深入研究

**Zhikai Chen, Fuchen Long, Zhaofan Qiu, Member, IEEE, Juyong Zhang, Member, IEEE,**  
**Zheng-Jun Zha, Member, IEEE, Ting Yao, Senior Member, IEEE, and Jiebo Luo, Fellow, IEEE**

## 摘要

如何建模反射效应对于单图像反射去除（SIRR）任务至关重要。现代SIRR方法通常简化反射公式，假设传输层和反射层的线性组合。然而，图像内容的巨大变化和真实世界的拍摄条件往往导致远比这复杂的反射。在本文中，我们基于两个重要因素，即反射的强度和模糊度，引入了一种新的屏幕-模糊组合，以更好地表征SIRR中的反射公式。具体而言，我们提出了屏幕-模糊反射网络（SRNet），该网络在其网络设计中执行屏幕-模糊公式，并适应真实场景中的复杂反射。从技术上讲，SRNet由三个组件组成：混合图像生成器、反射估计器和反射去除模块。图像生成器利用屏幕-模糊组合来合成训练用的混合图像。反射估计器学习反射层和测量反射模糊程度的模糊度。反射去除模块进一步使用混合图像、模糊度和反射层以级联方式过滤出传输层。当基于屏幕-模糊组合原理生成训练数据时，在三种不同SIRR方法上报告了优异的结果。此外，在六个数据集上的广泛实验定量和定性地证明了SRNet相对于最先进方法的有效性。

**索引词：** 单图像反射去除，反射公式。

## I. 引言

反射作为一种光学干扰，通常在通过玻璃拍摄的图像中观察到，当相机同时捕获玻璃反射的光（即反射层）和来自玻璃后物体的光（即传输层）时。去除这种不需要的反射将提高图像质量，从而有助于视觉任务，如物体检测和语义分割。早期工作[1], [2], [3], [4], [5], [6], [7], [8], [9], [10], [11], [12], [13]通过在不同条件下（如照明、偏振和相机视角）拍摄多张图像来寻求更丰富的反射线索进行后处理来解决这个问题。相反，单图像反射去除（SIRR）旨在使用单张照片从图像中分离反射，在实际部署中具有更高的潜力。

现代SIRR方法[14], [15], [16], [17], [18], [19], [20], [21]主要采用深度学习模型从数据驱动的角度去除反射。这些方法通常遵循传统的线性组合I = T + R，将混合图像I表述为传输层T和反射层R的求和。尽管这种线性组合在混合图像层方面很简单，但这样的线性组合没有考虑影响反射的其他因素，模型在实际场景中可能存在泛化问题。为了缓解这个问题，我们专注于SIRR中的反射公式，并引入一种新的屏幕-模糊组合：

I = T + (1 − T)(K ⊗ R), (1)

其中(1 − T)是反射强度的衰减项，K表示高斯核以模拟反射层中的散焦效应。与线性组合不同，我们进一步考虑了两个因素，即反射的强度和模糊度。前者源于"屏幕"混合函数，遵循摄影投影模型[22]的理论。观察是在真实情况下，如果传输层的亮度很大，反射的强度就会变小。我们以这个观察为基础，使用衰减项(1 − T)来抑制反射的强度。图1(a)比较了线性组合和屏幕组合I = T + (1 − T)R叠加的图像。屏幕函数合成的图像在视觉上更类似于真实的混合图像，特别是在红色边界框突出显示的传输强度较大的区域。反射模糊度的第二个因素表示反射物体的散焦效应。鉴于高斯核被广泛采用来为图像去模糊[23], [24], [25], [26]建模离焦模糊，我们利用高斯核K来估计反射层的模糊度。一般来说，使用标准差较大的高斯核将导致更多的图像模糊。图1(b)描述了反射层中不同模糊程度的混合图像。如预期的那样，使用标准差大的高斯核会增加反射层的模糊程度。

为了在SIRR中实现屏幕-模糊组合的想法，我们提出了一种新的屏幕-模糊反射网络（SRNet）。SRNet包括一个混合图像生成器、一个反射估计器和一个反射去除模块。混合图像生成器采用屏幕-模糊组合来合成大量训练图像，其反射层引入不同程度的模糊度。反射估计器通过几个2D卷积层学习反射层并回归相应的模糊度。给定输入混合图像、估计的反射层和模糊度，设计了一个级联细化模型以渐进方式过滤混合图像的传输层。SRNet的整体架构通过两个目标进行端到端优化，即反射和传输层的重建，以及神经网络中特征相似性学习的正则化。

总结而言，我们的工作做出了以下贡献：
- 屏幕-模糊组合被证明能够利用反射的强度和模糊度因素来更好地模拟SIRR中的反射公式。
- 所提出的SRNet能够更好地合成混合图像，学习反射层和相应的反射模糊度，并最终分离传输层。
- 我们从为不同SIRR模型生成训练数据的角度验证了屏幕-模糊组合的有效性，并通过在六个数据集上的广泛实验证明了我们SRNet的有效性。

## II. 相关工作

反射去除领域的研究人员[27]通常将该主题总结为三个方向，即单图像方法、多图像方法和辐照度方法。在这里，我们重点关注单图像方法，并简要将单图像反射去除（SIRR）的相关工作分为两类：基于传统先验的方法和基于深度学习的方法。

### A. 基于传统先验的方法

早期的SIRR工作[28], [29], [30], [31], [32], [33], [34], [35], [36], [37], [38], [39], [40], [41], [42]通过低级特征的统计线索从混合图像中捕获传输层，如色度-强度分布、梯度稀疏性先验和图像平滑度。Tan等人[29], [30]专注于基于2D色度-强度空间中镜面点和漫反射点的分布来分离反射。Levin和Weiss[32], [33]采用梯度稀疏性来辅助反射去除，并通过计算最小角点[34]获得稀疏性先验。除了强度和稀疏性的先验外，传输和反射之间的相对平滑度可以被视为图像分离的另一个线索[36], [37], [39]。例如，Li和Brown[39]引入了一般统计模型来用相对平滑度差异区分两层的梯度。通过利用梯度知识来捕获平滑度，Arvanitopoulos等人[35]制定了拉普拉斯数据保真项来增强平滑度检测，Yang等人[42]提出的2D泊松方程可以用于类似目的。此外，Shih等人[40]观察到厚玻璃引起的重影效应也可以用作反射去除的先验知识。基于传统先验的方法通常在非常特定的条件下制定SIRR，因此在真实世界复杂情况下可能存在泛化问题。

### B. 基于深度学习的方法

随着卷积神经网络（CNNs）的成功，将2D CNNs应用于SIRR的图像出现了趋势[14], [15], [16], [17], [18], [19], [21], [36], [43], [44], [45], [46], [47], [48], [49], [50]。这些进展主要从三个方面看待问题：训练数据合成、损失函数设计和网络设计。

为了解决为SIRR模型训练收集足够真实混合图像对的困难，先前的工作提出了各种公式来生成合成混合图像。Fan等人[14]首先平滑反射层，然后通过经验设计的反射幅度进行调整以生成混合图像。稍后在[15]中，Zhang等人研究了相机视角的渐晕效应用于反射生成。Zheng等人[18]探索了玻璃对反射造成的吸收效应。为了进一步动态地适应各种场景条件下的反射层，Wen等人[47]通过特定学习的混合掩码来利用反射层。尽管如此，这些方法仍然假设反射的幅度独立于传输，这忽略了彼此之间的相关性。

为反射去除特别设计了几种损失函数。Fan等人[14]采用L1损失来最小化传输和混合图像之间的边缘差异，以避免模糊上下文生成。此外，Zhang等人[15]设计了感知损失和排斥损失，分别解决颜色模糊性和学习像素级相似性。为了现实的图像细化，对抗损失[51]也在一些工作[15], [46]中被使用。

在网络设计方面，Fan等人[14]提出了一个两阶段结构来估计反射层的梯度图作为传输预测的指导。Wan等人[16]通过权重共享网络同时预测传输和梯度图以增强反射去除。为了更有效地利用混合图像信息，Hu和Guo[21]采用了一般的交互策略，在他们的双流分解网络中使用激活函数的变化，将上下文从一个流转换为另一个流的财富。一些辅助数据也被用于改善传输估计的特征学习。一个代表性工作是[19]，其中Dong等人估计反射置信度图来强调SIRR的目标区域。Li等人[45]利用输入和反射之间的特征差异作为传输的初始化，以缓解预测中的重反射问题。

然而，大多数基于深度学习的方法仍然面临在多样化真实条件下建模反射的挑战，特别是具有各种清晰度的反射。此外，还存在解决图像反射的其他方向，如无监督模型[52]和基于NeRF的模型[53]，以从图像生成的角度实现传输层重建。特别是，RahmaniKhezri等人[52]采用两个交叉耦合网络[54]来生成两个独特的背景和反射层。该模型不需要大量的图像对进行训练，也没有额外的信息或假设。Zhu等人[53]最近引入了一个带有循环边缘约束的神经传输径向场，寻求在给定一组反射损坏图像的情况下渲染传输视图。它提供了通过渲染过程分离传输和反射层的新视角。由于渲染性能高度依赖于邻近视图的特征，不同视图间不一致的视觉特征问题可能对反射去除产生负面影响。

### C. 总结

我们的方法属于基于深度学习的SIRR方法。鉴于有证据[55]表明人类视觉系统中存在视觉非线性，反射建模的更令人满意的方法似乎是挖掘传输和反射之间的相关性，而不是采用线性组合模型。因此，与上述方法不同，我们的方法不仅通过非线性屏幕-模糊组合利用反射的强度和模糊度来更好地模拟现实反射过程，还有效地将上述两个因素整合到反射去除的网络设计中。

## III. 屏幕-模糊反射网络

在本节中，我们详细阐述我们的屏幕-模糊反射网络（SRNet）。图2显示了我们反射去除架构的概述。具体而言，SRNet首先采用屏幕-模糊组合来模拟现实反射过程，并生成反射层中具有不同模糊程度的合成混合图像。接下来，反射估计器在合成训练混合图像上学习反射层和模糊度。最后，反射去除模块通过利用估计的反射层和模糊度的先验知识，逐步减少反射来分离传输层。整个架构通过优化两个目标进行训练，即反射和传输层的重建，以及神经网络中特征相似性学习的正则化。

### A. 屏幕-模糊组合

现代SIRR方法通常在线性组合下将混合图像I中的反射制定为传输层T和反射层R的组合：

I = T + R, (2)

其中T和R都在[0, 1]范围内归一化。这种线性求和无法完全捕获真实世界反射场景中基于光的叠加。例如，在反射组合中传输和反射层的强度之间存在相对关系。如视觉现象研究所示，工作[55]指出视觉增量阈值随着强度参考场的增长而增长。换句话说，在较亮的场景下物体变得更难被区分，因此在具有亮传输的区域中的反射变得不明显。然而，这个规则在线性组合中被忽略，线性组合通过简单求和直接融合反射和传输。此外，相机通常聚焦于传输层中的目标物体，因此导致反射层的散焦效应。反射层由散焦引起的模糊度在线性组合的反射公式中很难被考虑。因此，我们通过强调上述两个因素，即反射的强度和模糊度，引入了一种新的非线性屏幕-模糊组合，以近似真实世界的反射。

#### 1) 强度抑制：

在现实中，有许多视觉非线性的场景，例如伽马校正，表明人类对暗色调中的强度变化比亮色调中的强度变化更敏感。因此，强度的组合在空间上不是均匀的，在具有亮传输层的区域中反射的效应将在视觉上被削弱。遵循这种哲学[55]，我们通过屏幕函数[22]来制定反射中的过程，以通过从传输导出的权重来抑制强度。具体而言，我们通过基于传输层强度添加衰减项来重新制定公式(2)中的线性组合函数：

I = T + (1 − T)R, (3)

其中T和R都在[0, 1]内归一化。它模拟一个摄影幻灯片在另一个[22]上的投影。结果，当传输层T的亮度很大时，反射层R的强度将被比率(1−T)降低。

#### 2) 反射的模糊度：

为了拍摄清晰的照片，相机的焦距通常被很好地调节以聚焦于传输层，这经常导致反射层的散焦。不同程度的散焦会导致反射层上不同程度的模糊度。因此，我们进一步细化反射组合以模拟反射层的模糊度。为了简化问题公式，我们建议通过基于显微镜中的点扩散函数（PSF）模型[56]的高斯函数来拟合反射物体的发射器条件。这种模型在图像去模糊[24]的研究中也得到了验证。详细地，我们采用2D高斯核K来在反射层R上获得不同程度的模糊度。形式上，组合被重新制定为：

I = T + (1 − T)(K ⊗ R), (4)

其中操作⊗表示2D卷积。反射层的模糊程度由高斯核的标准差σK调整。当采用标准差大的核来卷积反射层时，输出的模糊程度将增加。为了方便模型训练，引入模糊度λ来测量模糊程度，计算为λ = ZσK。λ通过在σK上应用比例比率Z在[0, 1]内归一化。

公式(4)中所提出的屏幕-模糊组合将反射层的强度抑制和反射层的不同模糊程度都考虑到反射模拟中。与传统的线性组合相比，我们的模型提供了更现实和准确的解决方案来近似自然光的反射，并作为训练图像合成和后续网络优化的更好基础。

### B. 反射估计器

从混合图像I恢复传输层T是一个病态问题[14]，因为反射的形式是多样的。直接通过深度模型回归T将导致发散，使性能不令人满意。缓解这个问题的自然解决方案是采用辅助信息，如边缘[14], [16]，来约束优化空间。给定来自屏幕-模糊组合的合成混合图像，我们建议首先估计反射层及其相应的模糊度作为辅助信息来促进传输预测。设计的反射估计器可以进一步泛化以近似真实世界的混合图像来挖掘反射信息，从而最终增强后续的反射去除。

图3描述了反射估计器和基本反射解码器块的结构。给定混合图像I，模糊度λ̂通过卷积神经网络Eλ估计。接下来，我们利用模型Em从五个不同的空间分辨率（在我们使用的VGG-19模型中设置）提取视觉特征F0M到F4M。所有特征都被馈送到一堆反射解码器块（D1R到D4R）中以逐步重建反射层。在第i个反射解码器块DiR中，来自最后i-1块的输入解码反射特征Ri−1首先沿空间维度上采样以对齐输入视觉特征FiM。Ri−1和FiM在通道维度上连接，然后输入到两个卷积层分支中以学习两种类型的反射特征，即尖锐反射特征Fis和模糊反射特征Fib。输出解码反射特征Ri是两个特征的加权和，由估计的模糊度λ̂利用：

Ri = (1 − λ̂)Fis + λ̂Fib. (5)

这里，λ̂管理引导两个分支学习具有低/高模糊程度的尖锐/模糊反射层的特征。获得的Ri将被馈送到下一个解码器块Di+1R以进一步细化反射层。请注意，第一个解码器块D1R的输入特征来自Em的具有最小分辨率的卷积层，然后上采样以进行特征对齐。在最后一个解码器块中，使用带有sigmoid激活的卷积层来估计反射层R̂。

反射估计器赋予SRNet在不同摄影条件下区分反射的能力。这种良好的泛化能力使SRNet容易适用于真实生活的混合图像，而不仅仅是合成混合图像。此外，我们利用估计的反射层R̂和预测的模糊度参数λ̂作为先验知识来促进反射去除。

### C. 反射去除模块

基于估计反射层的辅助信息，增强反射去除的直接方法[19], [45], [48]是在CNNs中将反射层的中级特征与混合图像的特征连接以进行传输回归。如[57]中指出的，简单的特征连接不足以充分利用估计反射层的信息，并限制重反射的抑制。为了增强传输细节的学习，我们引入了反射去除模块，该模块通过拉普拉斯导数改善传输估计，旨在捕获局部窗口内的纹理信息。估计反射层的模糊度被利用作为导数的权重。当估计反射层的模糊程度很高时，反射中的纹理信息较少，导数对传输预测的贡献较少。

如图4所示，反射去除模块将混合图像I、估计反射R̂和预测模糊度λ̂作为输入。混合图像I和预测反射R̂分别馈送到两个独立的视觉编码器EI和ER中。类似于反射估计器的设计，混合图像的视觉特征（F0I到F4I）和估计反射层（F1R到F4R）从EI和ER中的不同卷积层提取。接下来，构建四个级联传输解码器块以通过利用所有上述特征来估计传输层的表示。在第i个传输解码器块DiT中，i-1块的输入传输解码特征Ti−1在空间上上采样以对齐混合图像特征FiI和反射层特征FiR的分辨率。接下来，我们通过拉普拉斯操作将FiR和FiI转换为二阶导数。一般来说，传输的导数ΔTi可以通过混合图像和反射层之间的导数差异来估计。基于传输和反射层在梯度域[27]中的统计模型[35], [39]，模糊反射相对于尖锐反射具有相对较小的梯度和较少的纹理信息。在传输回归期间，统计模型表明当模糊度很高时，我们应该减少反射层的贡献。先前的工作[39]遵循这种配方并为反射去除构建目标。传输和反射层在梯度域中同时优化，模糊度被视为调整这两个分量贡献的比例比率。类似地，我们建议利用最简单的公式[58]的比例比率1 − λ̂来在有很多模糊度时减少反射层梯度的权重。相反，尖锐反射层的导数应该从混合图像中被大量过滤，权重应该增加。因此，传输层的导数被制定为：

ΔTi = ΔFiI − (1 − λ̂)ΔFiR, (6)

其中Δ表示2D拉普拉斯操作。同时，在Ti−1和FiI的连接表示上估计掩码Mi。通过两次卷积和Mi在ΔTi上的特征缩放，传输解码特征Ti作为块的输出获得。传输层的表示由四个块以级联方式逐步重建。在最后一个传输解码器块的末尾，采用一个带有sigmoid激活的卷积层来预测最终的传输层。

### D. 网络优化

所提出的SRNet以端到端方式训练，通过优化两个主要目标，即反射/传输层的重建，以及CNNs中特征相似性学习的正则化。为了实现这一点，采用四个损失进行网络优化，即重建损失、感知损失、掩码损失和对抗损失。

#### 1) 重建损失：

重建损失Lrec被设计为L1损失，以最小化预测反射/传输层R̂/T̂与真实反射/传输层R/T之间的像素差异，计算为：

Lrec = ∥R̂ − R∥1 + ∥T̂ − T∥1, (7)

其中∥·∥1表示L1范数。

#### 2) 感知损失：

遵循[15]中的标准设置，感知损失Lpercep用于特征正则化。采用L1损失来最小化估计反射/传输层与VGG-19模型中选定层集L的真实反射/传输层特征之间的距离：

Lpercep = ∑l∈L κl(∥Φl(T̂) − Φl(T)∥1 + ∥Φl(R̂) − Φl(R)∥1), (8)

其中Φl表示从层集L中的层l提取的特征，κl是该层的平衡权重。

#### 3) 掩码损失：

为了正则化反射去除模块中掩码Mi的学习，设计掩码损失Lmask为：

Lmask = ∑4i=1(||Mi[Re > φ]||1 + ||Mi[Re < ψ] − 1||1), (9)

其中Re = I − T表示混合图像与真实传输层之间的差异。φ和ψ是两个阈值。通过这个损失，强反射区域（Re > φ）中学习的注意力值将接近零，弱反射（Re < ψ）下的值将接近一。因此，掩码在弱反射下维持传输层以调节特征学习。

#### 4) 对抗损失：

为了增强传输的质量，我们进一步通过对抗损失Ladv正则化传输层的生成以缓解颜色退化问题。我们的SRNet被视为生成器G，构建四层CNN作为判别器D。Ladv计算为：

LadvD = −ET[logD(T)] − EI[1 − logD(G(I))],
LadvG = −EI[logD(G(I))]. (10)

我们SRNet中的整体训练目标L通过整合上述四个损失制定为多任务损失：

L = β1Lrec + β2Lpercep + β3Lmask + β4Ladv, (11)

其中βi, i ∈ {1, 2, 3, 4}是权衡参数。

## IV. 实验

### A. 实验设置

#### 1) 训练数据：

遵循SIRR中的标准设置[15], [46], [57]，我们利用合成和真实世界的混合图像进行训练。来自PASCAL VOC数据集[59]子集的公共图像对[14]用于通过屏幕-模糊组合合成图像，总共产生7,196个合成混合图像对。此外，来自Zhang等人[15]发布的Real20数据集的90个真实世界混合图像对也用作训练数据。

#### 2) 评估数据集：

我们在六个流行的SIRR数据集上经验验证了我们SRNet的有效性，即Real20、SIR2 Postcard、SIR2 Solid、SIR2 Wild、Nature20和CDR。

Real20[14]数据集由20个真实混合图像对组成，用于SIRR评估。SIR2 Postcard、SIR2 Solid和SIR2 Wild数据集组成整个SIR2[60]数据集。在SIR2 Postcard数据集中，有199个明信片的混合图像对，内容与场景相关。SIR2 Solid数据集包含200个日常生活物品的室内混合图像对，SIR2 Wild包括55个关于野生场景的图像对。遵循进展[46], [47], [57]，上述数据集中的所有图像对都用于评估，总共有474个图像对。

此外，Nature20[45]和CDR[61]数据集用于另外两个独立评估。Nature20[45]由200个图像对用于训练和20个图像对用于测试组成。为了评估我们SRNet在模糊和不模糊反射条件下的泛化能力，我们额外应用CDR数据集[61]来验证SRNet在具有不同模糊程度反射的真实世界混合图像上的有效性。CDR的测试集可以分为两组，即BRST和SRST数据集，分别包含122和105个具有模糊反射（BR）和尖锐反射（SR）的图像对。

#### 3) 实现细节：

我们在PyTorch平台上实现SRNet。采用自适应矩估计优化器（Adam）进行模型优化。SRNet中的反射估计器由两个视觉编码器，即Eλ和Em，以及一个级联反射解码器DR组成。我们利用标准ResNet-18[62]作为视觉编码器Eλ。表I详细说明了Em和DR的结构。采用Em的五层（骨干网：VGG-19[63]），即conv1_2、conv2_2、conv3_4、conv4_4和conv5_4来输出视觉表示。表II进一步详细说明了反射去除模块的视觉编码器EI/ER和级联传输解码器DT的结构。视觉编码器EI和ER分别用于生成混合图像和反射层在不同空间分辨率的视觉特征。感知损失中选定的层集L和相应的权衡参数κl分别固定为{conv1_2, conv2_2, conv3_2, conv4_2, conv5_2}和{1/2.6, 1/4.8, 1/3.7, 1/5.6, 10/1.5}。掩码损失中的参数φ和ψ通过交叉验证设置为0.3和0.01。我们将损失权重βi, i ∈ {1, 2, 3, 4}分别设置为{1.0, 0.2, 1.0, 0.002}。基础学习率经验固定为0.0001。采用三步训练策略来优化SRNet。我们首先通过均方误差（MSE）损失优化Eλ 100个epoch以回归真实模糊度λ。然后反射估计器通过与Eλ的联合学习再微调40个epoch。反射估计器和反射去除模块进一步共同训练总共100个epoch。

#### 4) 评估指标：

遵循大多数SIRR进展[14], [45], [46], [57]，我们采用标准的峰值信噪比（PSNR）和结构相似性（SSIM）作为性能比较的评估指标。

### B. 与最先进方法的比较

我们将SRNet与几种最先进的技术进行比较，包括CEILNet[14]、Zhang等人[15]、BDN[48]、ERRNet[46]、IBCLN[45]和RAGNet[57]。表III总结了PSNR和SSIM比较。总体而言，SRNet在Real20和SIR2数据集上始终实现最佳性能，在平均PSNR和SSIM方面超越所有其他方法。一般来说，更高的PSNR/SSIM值表明估计的传输表示更好的感知质量。具体而言，SRNet在Real20和SIR2 Solid上实现23.58dB和26.96dB的PSNR，分别比最佳竞争者RAGNet高出0.63dB和0.81dB。尽管SRNet和RAGNet都利用反射作为反射去除的额外指导，但它们的不同之处在于RAGNet在线性组合假设下估计反射，而SRNet超越线性并通过考虑反射的强度和模糊度来表征反射公式。如结果所示，更现实的合成训练图像确实有益于反射去除的模型学习。

此外，我们在Nature20的训练集上微调我们的模型，并在表IV中报告测试集上的性能。我们的SRNet实现24.07dB的PSNR，相比最佳竞争者IBCLN提高了0.5dB。性能再次证明了我们SRNet在真实世界混合图像反射去除方面的有效性。

除了PSNR和SSIM外，图5可视化了6个示例的反射去除。特别是，SRNet成功过滤掉了红色边界框突出显示的区域中的反射，这些区域具有低强度的传输层（第1种情况）或高度模糊的反射层（第2种情况），而其他模型未能去除反射。结果基本上表明了我们SRNet的两个优势。首先，屏幕-模糊组合在传输层亮度较弱时在组合中给反射层更多权重，并模拟更现实的反射。其次，SRNet中模糊度的包含赋予模型在处理具有各种模糊程度的反射时更强的鲁棒性，并最终改善SIRR。

### C. 模糊或不模糊反射的泛化性

为了更好地验证我们SRNet在具有不同模糊程度反射层的反射去除上的泛化性，我们采用CDR数据集进行额外评估。表V显示了CDR中BRST和SRST数据集的PSNR和SSIM，分别包含混合图像中的模糊和尖锐反射层。如结果所示，我们的SRNet在相同设置下在具有模糊反射的BRST上超越强竞争者RAGNet。特别是，SRNet表现出更好的性能，在SRST上获得比ERRNet高0.8dB的PSNR增益。结果验证了SRNet即使在不模糊反射上的传输预测的泛化性。通过在模型训练中考虑反射的模糊程度，我们的SRNet可以区分具有各种模糊程度的反射，而不是仅仅专注于模糊反射情况。

### D. 屏幕-模糊组合的评估

接下来，我们评估屏幕-模糊组合的有效性，该组合建模真实世界反射的过程。为了检查合成混合图像的质量，我们测量真实世界混合图像与不同组合方式生成的合成图像之间的均方误差（MSE）。具体地，我们将每个图像分割为32 × 32空间大小的补丁，最终在SIR2数据集上总共获得87,168个补丁。平均MSE在所有补丁上计算，表VI列出了SIR2数据集上的统计数据。我们将我们的屏幕-模糊组合与线性组合和其他两个混合图像合成流水线[14], [15]进行比较。如预期的那样，线性组合表现最差，在真实和合成混合图像之间显示出很大的MSE差距。这在某种程度上揭示了线性组合泛化到真实世界图像反射的弱点。CEILNet[14]和我们的屏幕-模糊组合之间存在MSE性能差距。尽管两者都抑制反射层的强度以获得混合图像，但它们的根本不同之处在于CEILNet生成的复合图像是通过在整个反射层上减去一个全局强度值，而我们的屏幕-模糊组合是通过基于传输的影响动态调整每个像素的反射强度。因此，我们的方法提供了更灵活和鲁棒的像素级反射公式以获得更好的合成训练数据。

图6进一步可视化了两种情况下通过不同组合方式的合成混合图像。与真实混合图像相比，我们的屏幕-模糊组合不仅保持饱和度（红色边界框中显示），还模拟类似的模糊效应反射（蓝色边界框中显示）。可视化验证了我们屏幕-模糊组合通过考虑强度和模糊程度来合成非常接近的混合图像的有效性。

图7进一步显示了由不同反射组合策略生成的混合图像补丁位于不同MSE区间的频率分布直方图。横轴表示一系列连续的MSE区间，纵轴表示混合补丁的数量。除了直方图，我们还以指数方式[64], [65]拟合概率密度函数并绘制相应的概率密度函数曲线。如图所示，在低MSE范围（< 10−2）内，我们屏幕-模糊组合生成的混合补丁的频率明显高于线性组合和其他两种混合图像合成方法组成的补丁的频率。这再次验证了屏幕-模糊组合生成高质量混合图像对以实现SIRR训练真实反射的优越性。

为了验证屏幕-模糊组合在为不同SIRR模型生成训练数据方面的效果，我们进一步评估了在合成图像上学习的BDN[48]、ERRNet[46]和SRNet的性能。表VII详细说明了SIR2数据集上的平均PSNR性能。如预期的那样，在屏幕-模糊组合生成的训练数据上学习的所有三个模型都提升了PSNR性能，分别从23.05dB/23.65dB/24.26dB提升到23.8dB/24.77dB/25.43dB。性能趋势也与图像合成中的MSE性能一致。结果证明了探索反射层强度衰减和通过高斯模拟反射模糊度用于反射公式的优势。

### E. 反射估计器的评估

在这里，我们检查我们SRNet中反射估计器（RE）的基本反射解码器块。实现了反射解码器块的三个额外变体，即REw/oλ̂、REw/oFb和REw/oFs，用于比较。REw/oλ̂学习反射解码特征，只有一个卷积层分支，不考虑估计模糊度参数λ̂的特征缩放。REw/oFb去除模糊反射特征学习分支，REw/oFs排除尖锐反射特征学习分支。

表VIII总结了SIR2数据集上不同方法的PSNR性能。与具有单反射解码器分支的REw/oλ̂相比，SRNet在Postcard、Solid和Wild数据集上分别实现0.66dB、0.68dB和0.69dB的PSNR增加。去除反射解码器块中的任一特征学习分支（w/o Fb或w/o Fs）将导致性能下降。结果验证了两分支设计以预测更准确的反射层，利用这样准确的反射层作为先验知识增强最终反射去除。

图8还显示了SRNet和三个模型变体学习的反射层和传输层的定性视觉示例。如图所示，REw/oFb或REw/oFs估计的反射层呈现比REw/oλ̂更细粒度的内容（例如，红色边界框中塔的顶部）。结果基本上表明了涉及模糊度进行尖锐/模糊特征预测的优势。尽管如此，REw/oFb或REw/oFs只强调尖锐轮廓或模糊区域的反射恢复，可能没有反射层的完整估计。通过两个特征分支的联合学习，SRNet预测涵盖尖锐和模糊视觉部分的最佳质量反射层，并更彻底地去除反射区域。

### F. 反射去除模块的评估

然后，我们研究反射去除模块（RRM）中的每个设计如何影响传输估计的性能。我们通过改变传输解码器块的设计进行性能比较，设计了RRMw/oλ̂和RRMw/o∆两个额外运行。RRMw/oλ̂忽略特征缩放中的参数λ̂，直接通过∆Ti = ∆FiI − ∆FiR进行传输特征学习。RRMw/o∆是传输解码器块的变体，通过去除拉普拉斯并直接在视觉特征而不是导数上解码传输特征。

表VIII显示了SIR2数据集上反射去除的PSNR性能。总体而言，SRNet相对于RRMw/oλ̂和RRMw/o∆表现出更好的性能。特别是，SRNet在平均PSNR方面比RRMw/oλ̂高出1.86dB。这些结果证明了重新缩放反射导数对特征学习的影响。通过RRMw/o∆的直接特征融合无法充分捕获纹理信息，RRMw/o∆的PSNR不如在导数中进行特征融合的SRNet。

### G. 正则化项的评估

为了进一步分析每个正则化项如何对SRNet的最终性能做出贡献，我们在网络优化的最终目标中去除每个损失。具体地，我们研究三个变体，即SRNetw/oLpercep、SRNetw/oLmask和SRNetw/oLadv，分别去除感知损失、掩码损失和对抗损失。图10描述了两个反射去除情况的视觉比较。如图所示，当去除感知损失和掩码损失时，反射层的视觉内容仍在预测的传输层中。结果证实了两个正则化项的有效性。通过SRNetw/oLadv和SRNet之间的视觉比较，我们注意到SRNetw/oLadv预测的传输层包括一些颜色退化的伪影（红色边界框）。这是预期的，因为对抗损失通过捕获像素空间中的数据分布来增强图像质量。类似的探索也可以在反射去除的先前工作[15]中找到。

表IX进一步总结了不同变体的PSNR性能和训练时间比较。我们报告一个epoch的平均训练时间。总体而言，SRNet在三个子集上实现最佳PSNR性能。与SRNetw/oLadv相比，SRNet通过涉及额外的每个epoch 11分钟训练时间将平均PSNR从25.22dB提升到25.43dB。尽管包含对抗损失带来了一些训练成本，但定量性能和视觉质量都可以得到改善。这些结果验证了对抗学习正则化反射去除模型训练的适用性。

### H. 参数敏感性

多个损失组合的一个常见问题是需要设置之间的权衡参数。图11显示了SRNet在Real20和SIR2数据集上关于不同损失权重β2、β3和β4的平均PSNR和SSIM性能，而β1设置为1.0作为默认值，因为传输层的回归是主要目标。如这三个图所示，当在[0.1, 0.5]、[0.5, 2.5]和[0, 0.008]范围内变化β2、β3和β4时，我们可以看到性能曲线像"∧"。当β2、β3和β4分别为0.2、1.0和0.002时实现最佳性能。结果基本上验证了感知损失、掩码损失和对抗损失的特征正则化的有效性。此外，图12进一步描述了通过选择掩码损失的不同阈值φ和ψ的SRNet反射去除性能。当φ和ψ分别为0.3和0.01时，所提出的SRNet表现最佳。这验证了掩码损失设计以调节传输解码器块中特征学习的有效性。

### I. 更多反射和失败案例分析的讨论

在现实世界中，反射现象是复杂的，除了上述部分讨论的模糊效应外，还存在其他类型的反射。因此，我们在这里进一步研究SRNet在两种更多反射上的功效，即重影反射和低传输反射。

重影反射主要由玻璃的折射引起。当玻璃的厚度不能被忽略时，来自反射物体的光将同时在玻璃的外表面和内表面反射两次，导致重复的反射场景（例如，图13中的蓝色框）。为了验证SRNet在这种反射上的有效性，我们在CDR数据集[61]的子集上进行实验，该子集由具有/不具有重影反射的混合图像组成。表X显示了非重影和重影反射的PSNR和SSIM性能。我们的SRNet在其他基线中始终获得最佳性能。一般来说，与没有重影效应的反射相比，具有重影效应的混合图像中的反射和传输层可以更具区分性。因此，所有方法在重影反射去除上的性能都比非重影反射去除更好。图13进一步可视化了两个具有重影反射的情况。如图所示，SRNet的反射估计器可以有效预测具有重影效应的反射层，并在后续阶段进一步促进反射去除。

低传输反射，如[27]中讨论的，是反射去除问题中最具挑战性的情况之一。反射层在一些区域（例如，图14中的蓝色框）中主导混合图像，传输层的视觉信息被完全覆盖和丢失。在论文中，我们提出的SRNet在一定反射强度范围内利用屏幕-模糊组合，这种类型的低传输反射显然超出了适用强度范围。因此，SRNet未能精确估计和去除图14所示两个示例中具有大强度的反射层。为了缓解这个问题，输入图像的低混合区域中的上下文先验可以用于指导高混合区域的传输层估计。这种解决方案非常类似于图像修复设置，有许多新提出的技术来处理这个问题，如GANs[66]和扩散模型[67]。我们相信重建低传输反射区域是有效的，这将是我们反射去除未来工作之一。

## V. 结论

我们提出了屏幕-模糊反射网络（SRNet），该网络探索两个重要因素，即反射的强度和模糊度，用于真实世界场景中的复杂反射去除。特别是，我们通过在网络设计中整合这两个因素来研究去除反射的问题。为了实现我们的想法，我们首先引入屏幕-模糊组合来合成训练混合图像。模糊度测量反射层中的模糊度。反射估计器然后学习反射层并回归模糊度，反射去除模块基于混合图像、估计的反射层和模糊度进一步逐步过滤传输层。我们已经验证了屏幕-模糊组合在为不同SIRR方法生成更好训练图像方面的作用。此外，在六个数据集上进行的广泛实验定量和定性地验证了所提出的SRNet的有效性。我们可能的未来工作包括三个方向。首先，我们将考虑数据合成阶段的域适应以改善合成模型的泛化能力。其次，为图像修复问题设计的上下文信息可以被研究以促进面向低传输图像的反射去除。第三，我们将进一步探索更复杂反射模糊类型的公式，例如运动模糊，在框架设计中。

## 参考文献

[1] R. Szeliski, S. Avidan, and P. Anandan, "Layer extraction from multiple images containing reflections and transparency," in Proc. CVPR, 2000, pp. 1246–1253.

[2] X. Guo, X. Cao, and Y. Ma, "Robust separation of reflection from multiple images," in Proc. IEEE Conf. Comput. Vis. Pattern Recognit., Jun. 2014, pp. 2195–2202.

[3] B.-J. Han and J.-Y. Sim, "Reflection removal using low-rank matrix completion," in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 3872–3880.

[4] P. Wieschollek, O. Gallo, J. Gu, and J. Kautz, "Separating reflection and transmission images in the wild," in Proc. ECCV, 2018, pp. 89–104.

[5] R. Li, S. Qiu, G. Zang, and W. Heidrich, "Reflection separation via multi-bounce polarization state tracing," in Proc. ECCV, 2020, pp. 781–796.

[6] A. Punnappurath and M. S. Brown, "Reflection removal using a dual-pixel sensor," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2019, pp. 1556–1565.

[7] C. Lei, X. Huang, M. Zhang, Q. Yan, W. Sun, and Q. Chen, "Polarized reflection removal with perfect alignment in the wild," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2020, pp. 1747–1755.

[8] C. Lei and Q. Chen, "Robust reflection removal with reflection-free flash-only cues," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2021, pp. 14806–14815.

[9] N. Kong, Y.-W. Tai, and J. S. Shin, "A physically-based approach to reflection separation: From physical modeling to constrained optimization," IEEE Trans. Pattern Anal. Mach. Intell., vol. 36, no. 2, pp. 209–221, Feb. 2014.

[10] S. Wen, Y. Zheng, and F. Lu, "Polarization guided specular reflection separation," IEEE Trans. Image Process., vol. 30, pp. 7280–7291, 2021.

[11] T. Li, D. P. K. Lun, and Y.-H. Chan, "Robust reflection removal based on light field imaging," IEEE Trans. Image Process., vol. 28, no. 4, pp. 1798–1812, Apr. 2019.

[12] T. Li, Y.-H. Chan, and D. P. K. Lun, "Improved multiple-image-based reflection removal algorithm using deep neural networks," IEEE Trans. Image Process., vol. 30, pp. 68–79, 2021.

[13] J. Y. Cheong, C. Simon, C.-S. Kim, and I. K. Park, "Reflection removal under fast forward camera motion," IEEE Trans. Image Process., vol. 26, no. 12, pp. 6061–6073, Dec. 2017.

[14] Q. Fan, J. Yang, G. Hua, B. Chen, and D. Wipf, "A generic deep architecture for single image reflection removal and image smoothing," in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), Oct. 2017, pp. 3258–3267.

[15] X. Zhang, R. Ng, and Q. Chen, "Single image reflection separation with perceptual losses," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit., Jun. 2018, pp. 4786–4794.

[16] R. Wan, B. Shi, L.-Y. Duan, A.-H. Tan, and A. C. Kot, "CRRN: Multi-scale guided concurrent reflection removal network," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit., Jun. 2018, pp. 4777–4785.

[17] R. Wan, B. Shi, H. Li, L.-Y. Duan, A.-H. Tan, and A. C. Kot, "CoRRN: Cooperative reflection removal network," IEEE Trans. Pattern Anal. Mach. Intell., vol. 42, no. 12, pp. 2969–2982, Dec. 2020.

[18] Q. Zheng, B. Shi, J. Chen, X. Jiang, L.-Y. Duan, and A. C. Kot, "Single image reflection removal with absorption effect," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2021, pp. 13390–13399.

[19] Z. Dong, K. Xu, Y. Yang, H. Bao, W. Xu, and R. W. H. Lau, "Location-aware single image reflection removal," in Proc. IEEE/CVF Int. Conf. Comput. Vis. (ICCV), Oct. 2021, pp. 4997–5006.

[20] Y. Chang and C. Jung, "Single image reflection removal using convolutional neural networks," IEEE Trans. Image Process., vol. 28, no. 4, pp. 1954–1966, Apr. 2019.

[21] Q. Hu and X. Guo, "Trash or treasure? An interactive dual-stream strategy for single image reflection separation," in Proc. NeurIPS, 2021, pp. 24683–24694.

[22] S. Valentine, The Hidden Power of Blend Modes in Adobe Photoshop. Hoboken, NJ, USA: Adobe Press, 2012.

[23] J. Flusser, S. Farokhi, C. Höschl, T. Suk, B. Zitová, and M. Pedone, "Recognition of images degraded by Gaussian blur," IEEE Trans. Image Process., vol. 25, no. 2, pp. 790–806, Feb. 2016.

[24] Y.-Q. Liu, X. Du, H.-L. Shen, and S.-J. Chen, "Estimating generalized Gaussian blur kernels for out-of-focus image deblurring," IEEE Trans. Circuits Syst. Video Technol., vol. 31, no. 3, pp. 829–843, Mar. 2021.

[25] C. J. Schuler, M. Hirsch, S. Harmeling, and B. Schölkopf, "Learning to deblur," IEEE Trans. Pattern Anal. Mach. Intell., vol. 38, no. 7, pp. 1439–1451, Jul. 2016.

[26] S. Nah, T. H. Kim, and K. M. Lee, "Deep multi-scale convolutional neural network for dynamic scene deblurring," in Proc. CVPR, 2017, pp. 3883–3891.

[27] R. Wan, B. Shi, H. Li, Y. Hong, L.-Y. Duan, and A. C. Kot, "Benchmarking single-image reflection removal algorithms," IEEE Trans. Pattern Anal. Mach. Intell., vol. 45, no. 2, pp. 1424–1441, Feb. 2023.

[28] B. Sarel and M. Irani, "Separating transparent layers through layer information exchange," in Proc. ECCV, 2004, pp. 328–341.

[29] R. T. Tan, K. Nishino, and K. Ikeuchi, "Separating reflection components based on chromaticity and noise analysis," IEEE Trans. Pattern Anal. Mach. Intell., vol. 26, no. 10, pp. 1373–1379, Oct. 2004.

[30] R. T. Tan and K. Ikeuchi, "Separating reflection components of textured surfaces using a single image," IEEE Trans. Pattern Anal. Mach. Intell., vol. 27, no. 2, pp. 178–193, Feb. 2005.

[31] A. Levin, A. Zomet, and Y. Weiss, "Learning to perceive transparency from the statistics of natural scenes," in Proc. NIPS, 2002, pp. 1271–1278.

[32] A. Levin and Y. Weiss, "User assisted separation of reflections from a single image using a sparsity prior," in Proc. ECCV, 2004, pp. 602–613.

[33] A. Levin and Y. Weiss, "User assisted separation of reflections from a single image using a sparsity prior," IEEE Trans. Pattern Anal. Mach. Intell., vol. 29, no. 9, pp. 1647–1654, Sep. 2007.

[34] A. Levin, A. Zomet, and Y. Weiss, "Separating reflections from a single image using local features," in Proc. CVPR, Jul. 2004, pp. 306–313.

[35] N. Arvanitopoulos, R. Achanta, and S. Süsstrunk, "Single image reflection suppression," in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 1752–1760.

[36] Y.-C. Chung, S.-L. Chang, J.-M. Wang, and S.-W. Chen, "Interference reflection separation from a single image," in Proc. WACV, 2009, pp. 1–6.

[37] Q. Yan, Y. Xu, X. Yang, and T. Nguyen, "Separation of weak reflection from a single superimposed image," IEEE Signal Process. Lett., vol. 21, no. 10, pp. 1173–1176, Oct. 2014.

[38] R. Wan, B. Shi, T. A. Hwee, and A. C. Kot, "Depth of field guided reflection removal," in Proc. IEEE Int. Conf. Image Process. (ICIP), Sep. 2016, pp. 21–25.

[39] Y. Li and M. S. Brown, "Single image layer separation using relative smoothness," in Proc. IEEE Conf. Comput. Vis. Pattern Recognit., Jun. 2014, pp. 2752–2759.

[40] Y. Shih, D. Krishnan, F. Durand, and W. T. Freeman, "Reflection removal using ghosting cues," in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2015, pp. 3193–3201.

[41] R. Wan, B. Shi, L.-Y. Duan, A.-H. Tan, W. Gao, and A. C. Kot, "Region-aware reflection removal with unified content and gradient priors," IEEE Trans. Image Process., vol. 27, no. 6, pp. 2927–2941, Jun. 2018.

[42] Y. Yang, W. Ma, Y. Zheng, J.-F. Cai, and W. Xu, "Fast single image reflection suppression via convex optimization," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2019, pp. 8133–8141.

[43] M. Jin, S. Süsstrunk, and P. Favaro, "Learning to see through reflections," in Proc. IEEE Int. Conf. Comput. Photography (ICCP), May 2018, pp. 1–12.

[44] S. Kim, Y. Huo, and S.-E. Yoon, "Single image reflection removal with physically-based training images," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2020, pp. 5163–5172.

[45] C. Li, Y. Yang, K. He, S. Lin, and J. E. Hopcroft, "Single image reflection removal through cascaded refinement," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2020, pp. 3562–3571.

[46] K. Wei, J. Yang, Y. Fu, D. Wipf, and H. Huang, "Single image reflection removal exploiting misaligned training data and network enhancements," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2019, pp. 8170–8179.

[47] Q. Wen, Y. Tan, J. Qin, W. Liu, G. Han, and S. He, "Single image reflection removal beyond linearity," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2019, pp. 3766–3774.

[48] J. Yang, D. Gong, L. Liu, and Q. Shi, "Seeing deeply and bidirectionally: a deep learning approach for single image reflection removal," in Proc. ECCV, 2018, pp. 654–669.

[49] H. Zhang et al., "Fast user-guided single image reflection removal via edge-aware cascaded networks," IEEE Trans. Multimedia, vol. 22, no. 8, pp. 2012–2023, Aug. 2020.

[50] B. H. P. Prasad, K. S. G. Rosh, R. B. Lokesh, K. Mitra, and S. Chowdhury, "V-DESIRR: Very fast deep embedded single image reflection removal," in Proc. ICCV, 2021, pp. 2390–2399.

[51] P. Isola, J.-Y. Zhu, T. Zhou, and A. A. Efros, "Image-to-image translation with conditional adversarial networks," in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 5967–5976.

[52] H. RahmaniKhezri, S. Kim, and M. Hefeeda, "Unsupervised single-image reflection removal," IEEE Trans. Multimedia, vol. 25, pp. 4958–4971, Jun. 2022.

[53] C. Zhu, R. Wan, and B. Shi, "Neural transmitted radiance fields," in Proc. NeurIPS, 2022, pp. 38994–39006.

[54] V. Lempitsky, A. Vedaldi, and D. Ulyanov, "Deep image prior," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit., Jun. 2018, pp. 9446–9454.

[55] G. Buchsbaum, "An analytical derivation of visual nonlinearity," IEEE Trans. Biomed. Eng., vol. BME-27, no. 5, pp. 237–242, May 1980.

[56] S. Stallinga and B. Rieger, "Accuracy of the Gaussian point spread function model in 2D localization microscopy," Opt. Exp., vol. 18, no. 24, p. 24461, 2010.

[57] Y. Li, M. Liu, Y. Yi, Q. Li, D. Ren, and W. Zuo, "Two-stage single image reflection removal with reflection-aware guidance," 2020, arXiv:2012.00945.

[58] S. Zhuo and T. Sim, "Defocus map estimation from a single image," Pattern Recognit., vol. 44, no. 9, pp. 1852–1858, Sep. 2011.

[59] M. Everingham, L. Van Gool, C. K. I. Williams, J. Winn, and A. Zisserman, "The PASCAL visual object classes (VOC) challenge," Int. J. Comput. Vis., vol. 88, no. 2, pp. 303–338, Jun. 2010.

[60] R. Wan, B. Shi, L.-Y. Duan, A.-H. Tan, and A. C. Kot, "Benchmarking single-image reflection removal algorithms," in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), Oct. 2017, pp. 3942–3950.

[61] C. Lei et al., "A categorized reflection removal dataset with diverse real-world scenes," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. Workshops (CVPRW), Jun. 2022, pp. 3039–3047.

[62] K. He, X. Zhang, S. Ren, and J. Sun, "Deep residual learning for image recognition," in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2016, pp. 770–778.

[63] K. Simonyan and A. Zisserman, "Very deep convolutional networks for large-scale image recognition," in Proc. ICLR, 2015, pp. 1–14.

[64] A. W. Marshall and I. Olkin, "A multivariate exponential distribution," J. Amer. Stat. Assoc., vol. 62, pp. 30–44, Mar. 1967.

[65] R. D. Gupta and D. Kundu, "Generalized exponential distribution: Different method of estimations," J. Stat. Comput. Simul., vol. 69, no. 4, pp. 315–337, Jul. 2001.

[66] H. Zheng et al., "Image inpainting with cascaded modulation GAN and object-aware training," in Proc. ECCV, 2022, pp. 277–296.

[67] A. Lugmayr, M. Danelljan, A. Romero, F. Yu, R. Timofte, and L. Van Gool, "RePaint: Inpainting using denoising diffusion probabilistic models," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2022, pp. 11451–11461.

## 作者简介

**陈志凯** 于2020年获得中国科学技术大学（USTC）学士学位，目前在信息科学技术学院攻读博士学位。他目前的研究兴趣包括视觉修复、视觉增强和生成学习。

**龙富臣** 于2021年获得中国科学技术大学（USTC）博士学位。他目前是中国北京京东探索研究院视觉和多媒体实验室的研究员。他参与了几个时间动作提议和检测竞赛，如ActivityNet Challenge 2019中的扩展视频活动检测（ActEV-PC）、ActivityNet时间动作检测挑战2018和ActivityNet时间动作提议挑战2017。他的研究兴趣包括时间动作提议和定位、多媒体检索和视频理解。

**邱兆凡**（IEEE会员）于2020年获得中国科学技术大学（USTC）博士学位。他目前是中国北京京东探索研究院视觉和多媒体实验室的研究员。他参与了几个大规模视频分析竞赛，如ActivityNet大规模活动识别挑战和THUMOS动作识别挑战。他的研究兴趣包括大规模视频分类、语义分割和多媒体理解。他于2017年获得MSRA奖学金。

**张举勇**（IEEE会员）于2006年获得中国科学技术大学学士学位，并获得新加坡南洋理工大学博士学位。他目前是中国科学技术大学数学科学学院教授。他的研究兴趣包括计算机图形学、计算机视觉和数值优化。他是IEEE TRANSACTIONS ON MULTIMEDIA和IEEE COMPUTER GRAPHICS AND APPLICATIONS的副编辑。

**查正军**（IEEE会员）分别于2004年和2009年获得中国科学技术大学学士和博士学位。他目前是中国科学技术大学信息科学与技术学院的正教授，以及国家脑启发智能技术与应用工程实验室（NEL-BITA）的执行主任。他在其研究领域的顶级期刊和会议上发表了一系列论文，包括多媒体分析与理解、计算机视觉、模式识别和脑启发智能。他获得了著名会议的多项论文奖励，包括ACM Multimedia的最佳论文奖和最佳学生论文奖以及AAAI的杰出论文奖。他担任/曾担任IEEE TRANSACTIONS ON MULTIMEDIA、IEEE TRANSACTIONS ON CIRCUITS AND SYSTEMS FOR VIDEO TECHNOLOGY和ACM Transactions on Multimedia Computing, Communications, and Applications的副编辑。

**姚婷**（IEEE高级会员）目前是中国北京京东探索研究院视觉和多媒体实验室的首席研究员。在加入京东之前，他是微软亚洲研究院的研究员。他是国际基准竞赛中几个顶级多媒体分析系统的主要设计师，如ActivityNet大规模活动识别挑战2019-2016、视觉域适应挑战2019-2017和COCO图像字幕挑战。他是MSR视频到语言挑战、ACM Multimedia 2017和2016的主要组织者，并构建了MSR-VTT，这是一个在全世界广泛使用的大规模视频到文本数据集。他的研究兴趣包括视频理解、视觉和语言以及深度学习。他的工作获得了许多奖项，包括2015年ACM SIGMM杰出博士论文奖、2019年ACM SIGMM新星奖和2019年IEEE TCMC新星奖。他是IEEE TRANSACTIONS ON MULTIMEDIA的副编辑。

**罗杰波**（IEEE会员）目前是美国纽约州罗切斯特大学工程学院Albert Arendt Hopeman教授和计算机科学教授，他于2011年加入该校，此前在柯达研究实验室有15年的成功职业生涯。他发表了600多篇技术文章，拥有90多项美国专利。他的研究兴趣包括计算机视觉、自然语言处理、机器学习、数据挖掘、计算社会科学和数字健康。他是NAI、ACM、AAAI、SPIE和IAPR的会员。他参与了众多技术会议，包括担任ACM Multimedia 2010、IEEE CVPR 2012、ACM ICMR 2016和IEEE ICIP 2017的程序联合主席，以及ACM Multimedia 2018和IEEE ICME 2024的总联合主席。他曾担任IEEE TRANSACTIONS ON PATTERN ANALYSIS AND MACHINE INTELLIGENCE（TPAMI）、IEEE TRANSACTIONS ON MULTIMEDIA（TMM）、IEEE TRANSACTIONS ON CIRCUITS AND SYSTEMS FOR VIDEO TECHNOLOGY（TCSVT）、IEEE TRANSACTIONS ON BIG DATA（TBD）、ACM Transactions on Intelligent Systems and Technology（TIST）、Pattern Recognition、Knowledge and Information Systems（KAIS）、Machine Vision and Applications和Intelligent Medicine的编委会成员。他于2020年至2022年担任IEEE TRANSACTIONS ON MULTIMEDIA的主编。
