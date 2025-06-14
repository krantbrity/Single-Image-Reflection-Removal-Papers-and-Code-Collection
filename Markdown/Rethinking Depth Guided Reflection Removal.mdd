# 深度引导反射移除的再思考

**作者：** Lingzhi He†, Yakun Chang†, Runmin Cong, Senior Member, IEEE, Hongyu Liu, Shujuan Huang, Renshuai Tao, Yao Zhao*, Fellow, IEEE

† 共同贡献者  
* 通信作者

本工作得到中央高校基本科研业务费专项资金(No.2022JBZY043)、国家自然科学基金(No.U24B20179, No.62120106009, No.62301009, No.62471278)的部分支持。

Lingzhi He, Yakun Chang, Hongyu Liu, Shujuan Huang, Renshuai Tao, 和 Yao Zhao 隶属于北京交通大学，北京先进信息科学与网络技术重点实验室，教育部视觉智能+X国际合作联合实验室，北京，100044，中国。邮箱：{lingzhihe, ykchang, liu.hongyu, shujuanhuang, rstao, yzhao}@bjtu.edu.cn。

Runmin Cong 隶属于山东大学控制科学与工程学院，山东，250100，中国。邮箱：rmcong@sdu.edu.cn。

---

## 摘要

当通过玻璃拍摄时，常常观察到反射现象，这会对捕获的图像或视频质量产生负面影响。在本文中，我们总结并重新思考了深度引导的反射移除方法，并受人类双目视觉系统的启发，研究如何利用深度信息来实现有效的双目视频反射移除。我们提出了一种端到端的基于学习的反射移除方法，该方法学习透射深度并设计了一个统一结构，以级联方式实现深度引导、跨视图和跨帧特征增强。在统一结构内，设计了不同的门控控制器来强调特征交互的方向。构建了一个包含合成和真实双目混合视频数据集用于网络训练和测试。在所提出数据集的合成和真实数据上的实验结果表明，所提出的方法在双目视频反射移除方面达到了优异的性能。

**索引词**—反射移除，层分离，图像复原，深度引导

---

## I. 引言

当通过玻璃捕获图像或录制视频时，通常会引入反射，污染透射场景，导致底层内容的混淆和模糊。移除反射和恢复原始透射场景对于高级计算机视觉任务中的准确决策至关重要，如目标检测[1]、人脸识别[2]、语义分割[3][4]和异常检测[5][6]。由于捕获单幅图像的便利性，单幅图像反射移除[7][8][9][10]已成为一种流行选择。然而，这项任务具有挑战性，因为反射层和透射层都是具有未知混合比例的自然图像。因此，在没有额外引导的情况下，该问题具有无限多个可能的解决方案。因此，在这种具有挑战性的条件下引入辅助引导来解决图像层分离问题是直观的。

在过去几十年中，深度被认为是反射移除的有效引导[11][12][14][15]。获得透射场景深度的有效方法是通过主动近红外传感器[11]。由于深度获取独立于可见光反射，深度信息可以用于移除反射。然而，这种方法需要非常规传感器和拍摄方向与玻璃之间的特定角度范围[11]，这两个条件都限制了其在更一般场景中的应用。对于更广泛可用的消费级单目相机，感知两层深度的常用方法是调整焦距以保持透射场景在视野中，从而导致反射边缘模糊。例如，从单幅图像估计的景深(DoF)被用于识别反射边缘[12]，为反射移除提供了可行的解决方案。然而，DoF估计[13]依赖于手动参数，当混合图像包含复杂纹理时，会降低模型的鲁棒性。为了更鲁棒地感知深度，使用一对以不同焦点设置捕获的图像是可行的[14][15]。不幸的是，这种策略仅限于静态场景。在更一般的动态场景中，调整焦距以跟上运动是具有挑战性的。使用单目相机获得深度的另一种方法是利用多视图摄影[16]。然而，这种方法仍然基本依赖于通过边缘分类来区分透射和反射。此外，由于单目相机无法同时捕获多视角图像，还需要额外的运动估计。因此，反射移除依赖于深度估计的鲁棒性。

与单目相机相比，双目相机可以在相同的参考时间戳下捕获一对跨视角图像，具有已知参数，如相机基线和投影矩阵。这一特性促进了像素级对齐[17]，并能够估计反射不变流来进行跨视角补偿[18]。然而，在这些方法[17][18]中，深度感知被忽略且未被利用，因为反射层和透射层中都存在视差。具体来说，透射场景产生真实深度，而反射场景产生伪深度[19]。对于人类视觉，丰富的先验知识使我们能够直观地区分真实和伪深度，而无需任何边缘分类判断。如图1所示，人类视觉通过感知透射场景的深度来区分反射层和透射层。大脑自动过滤掉不正确的深度信息，从而产生准确的透射深度。当处理反射污染的场景时，双目相机通常感知伪深度[19]和真实深度。受人类视觉系统的启发，我们提出从反射污染的图像中估计透射深度，遵循人眼区分反射层和透射层的方式，来引导有效的反射移除。

然而，在双目相机中，当处理反射污染的场景时，深度感知会产生伪深度和真实深度。

受双目人类视觉系统的启发，并受深度学习模型强大能力的驱动，我们假设通过在双目数据上的广泛训练，特别设计的深度学习模型可以获得先验知识来有效区分真实和伪深度。这种学习到的知识随后被应用于移除反射。因此，我们提出了一种端到端的深度引导反射移除网络(DGR2-Net)用于双目视频反射移除。设计的DGR2-Net利用深度估计模块来随后生成无反射的透射深度。此外，双目视频固有地包含跨视角空间和跨帧时间补全信息。因此，我们主要利用深度引导，辅以跨视角和跨帧线索，在这项工作中实现有效的反射移除。为了充分利用这种丰富的引导，我们设计了一个统一结构来探索局部和全局特征之间的相关性。使用统一结构，采用专门设计的门控控制器来基于特征点是否针对三个任务中的每一个进行点对点对齐来强调特征交互的方向。为了训练我们的模型并验证我们提出方法的有效性，我们构建了一个跨不同场景捕获的混合双目视频数据集。在我们提出的真实世界数据集和合成数据集上的实验结果表明，所提出的方法在双目视频反射移除方面取得了优异的性能。

总而言之，主要贡献在以下方面得到强调：

- 一种端到端的基于学习的方法，探索双目视频反射移除的有效深度引导；

- 一种统一结构，采用定制设计的门控控制器以级联方式强调特征交互的方向，实现深度引导、跨视角空间引导和跨帧时间引导的有效利用来进行特征增强；

- 构建一个跨不同场景捕获的混合双目视频数据集，用于验证当前方法并启发未来研究。

---

## II. 相关工作

### A. 单图像反射移除

单图像反射移除(SIRR)方法旨在从单幅混合图像中移除反射并恢复透射图像。由于其巨大的病态性，大多数传统的基于优化的方法设计手工制作的先验来约束解空间，如梯度稀疏性先验[20][21]、平滑性先验[22][23]、重影线索[24]和梯度先验[25]。Yang等人[26]通过凸优化抑制反射。近年来，许多基于深度学习的方法被提出来处理复杂的反射。作为开创性工作，Fan等人[7]提出了一个两阶段级联网络用于边缘预测并引导反射移除。为了促进数据驱动的SIRR方法的发展，研究者们[9][27][28][31][29][30]提出了反射移除数据集，并分析了数据集特征。几种用户引导方法[21][32][33]利用用户交互来标记特定反射。Wen等人[34]预测非线性alpha混合掩码并设计重建损失。Wan等人[8]利用图像上下文和梯度的组合来移除反射。Zheng等人[35]提出估计玻璃的吸收效应因子。Zhu等人[36]缓解反射/透射模糊性并改善透射的渲染保真度。Duan等人[37]遵循人类视觉的"发展-然后-竞争"过程，提出图像分解网络。Hong等人[38]通过解决几何和光度对齐来移除全景图像的反射。Zhu等人[39]提出色调引导反射移除网络。最近，几种方法[10][40][41][42][43][44][45]利用级联细化在多次迭代中迭代移除反射。一些轻量级网络由Prasad等人[46]和Peng等人[47]提出，使它们更适合于现实世界应用。RahmaniKhezri等人[48]介绍了第一种无监督反射移除方法。

### B. 多图像反射移除

多图像反射移除(MIRR)方法旨在引入由额外图像提供的额外约束来提供更稳定的解决方案。Xue等人[49]通过对反射层和透射层施加重尾分布来惩罚重叠梯度来移除反射。一些基于偏振的方法[50][51][52][53][54]通常采用由偏振器提供的一组图像来区分反射的位置。这些方法需要手动旋转偏振器或使用偏振相机，从而限制了它们的适用性。一些方法[22][55][56][57]要求用户从多个视点捕获图像或视频，所提出的方法学习反射层和透射层之间的运动差异。Gai等人[58]提出了一个网络来估计线性混合系数以及透射层和反射层的运动以促进反射移除。Yang等人[59]通过亮度一致性约束将光流估计与层分离集成。Niklaus等人[18]引入反射不变运动估计和图像变形以考虑透射视差。一些研究者[60][61][62][63][64]利用用主动光源捕获的图像来获得无反射引导，从而促进反射移除。从主动近红外传感器[11]捕获或从多图像[14][15][16]估计的深度图可以通过提供关于场景物体表面距离的信息为反射移除提供有效引导。

---

## III. 深度引导方法

### A. 动机

与深度相关的反射移除方法可以根据所使用的成像设备分为基于单目的和基于双目的方法。单图像单目方法[12]（如图2(a)所示）估计深度置信度图并利用边缘选择来区分反射边缘和透射边缘。由于单幅图像中的信息量有限，在复杂情况下获得的深度置信度图不可靠。一种多图像单目方法[16]（见图2(b)）集成来自不同视点获得的多幅图像的特征。然后执行深度估计和基于深度的边缘选择。虽然这些基于深度的边缘选择操作为定位反射和透射区域提供了线索，但它们对深度信息的利用与人类视觉系统区分反射的方式不一致。其他研究者[11]（图2(c)）设计了一个多模态网络，实现深度和RGB图像之间的深度引导特征融合。然而，这种方法需要非常规传感器和拍摄方向与玻璃之间的特定角度范围，这两个条件都限制了其在更一般场景中的应用。对于基于双目的方法，典型方法[18]（见图2(d)）首先从单个输入对学习反射不变光流，然后应用变形操作来校正运动，同时忽略深度感知。在重新思考深度引导反射移除时，我们已经确定双目视频通过集成深度估计、深度引导、视图引导和帧引导增强，有望更好地解决这个问题。我们强烈断言，使用深度估计在双目视频中实现反射移除不仅仅是结合现有方法的问题；它需要更有针对性的模块设计来确保鲁棒的反射移除。

双目相机同时从不同视角捕获成对的视频帧，提供了获得混合深度图的固有优势。然而，混合深度图不适合作为反射移除的直接引导，因为反射会引入伪深度信息。如图2(e)所示，我们设计了一个深度估计模块，该模块使用混合视频帧对作为输入来产生更清晰的透射深度帧。在使用透射深度图作为引导之前，左右视图的特征融合确保深度特征与RGB特征完全对齐。因此，预先设计并应用跨视角特征增强模块。受人类视觉系统背景深度感知特性的启发，我们结合深度特征和RGB特征的局部和全局相关性，而不是特征图的直接组合。这种方法不仅为相应像素启用跨模态低级特征引导，还利用不同模态之间的高级特征引导。此外，考虑到视频帧和透射深度图之间的连续性，提出跨帧特征增强模块来利用时间帧补充。它可以为反射层提供线索，同时增强网络对高级视频语义的理解，从而生成更连贯的视频。

### B. 提出的流水线

图2(e)说明了端到端深度引导反射移除网络(DGR2-Net)的提出流水线，该网络利用基于递归CNN的方法以逐帧方式移除反射。给定由双目相机捕获的视频序列{I^l_i, I^r_i}，其中i ∈ [0, N-1]表示视频帧的索引。然后，我们通过设计深度估计模块D(·)来实现深度感知，该模块将观察到的混合视频帧对作为输入来生成透射深度帧对{D̂^l_i, D̂^r_i}：

{D̂^l_i, D̂^r_i} = D({I^l_i, I^r_i}) (1)

为了移除反射，DGR2-Net的其余部分（表示为T(·)）将前N个帧对、当前帧对、后续N个帧对：{I^l_{i+n}, I^r_{i+n}}（n∈[-N, N]，总共2N+1对）及其相应的透射深度帧对{D̂^l_{i+n}, D̂^r_{i+n}}作为输入来生成最终的透射帧对{T̂^l_i, T̂^r_i}。这样的过程可以描述为：

{T̂^l_i, T̂^r_i} = T({I^l_{i+n}, I^r_{i+n}}, {D̂^l_{i+n}, D̂^r_{i+n}}) (2)

观察图3，在T(·)的编码器侧，在多个特征图级别上设计了三个关键模块来进行特征增强。在每个特征级别，左右视图特征首先通过跨视角特征增强模块(CVEM)融合，然后融合特征通过深度引导特征增强模块(DGEM)与深度特征集成，最后由跨帧特征增强模块(CFEM)处理。在这项工作中，我们考虑将这三种类型的特征增强模块实现为具有不同门控控制器的统一结构，以探索局部和全局特征之间的相关性。特征图更新过程如图3所示，其中第m级特征图更新可以描述如下：

f̃^l_m, f̃^r_m, f^{lr}_m = CV(f^l_m, f^r_m),
f̃^{lr}_m, f̃^d_m, f^{lrd}_m = DG(f^{lr}_m, f^d_m),
f̃^{lrd}_m, f̃^f_m, f^{lrdf}_m = CF(f^{lrd}_m, f^f_m), (3)

其中CV(·)、DG(·)和CF(·)分别表示三个模块的映射函数。

---

## IV. DGR2-Net的架构

DGR2-Net的整体网络架构如图3所示。受DispBiNet[65]的启发，深度估计模块（详见图4）基于U-Net[66]结构设计。与DispBiNet不同，所提出的深度估计模块将混合视频帧对作为输入来生成透射深度帧对。此外，我们的设计允许解码器从高级特征开始，首先获得1/8比例的粗糙深度图。通过连续上采样和集成低级特征，它逐渐恢复透射深度图的细节。此外，应用2个残差块、4个扩张卷积层和2个卷积块注意力模块(CBAM)[67]来扩大感受野并丰富中间层卷积的多样性。

此外，剩余网络T(·)设计为编码器-解码器结构，由四个编码器和一个解码器组成。第一个编码器将当前左帧I^l_i和先前生成的左透射帧T̂^l_{i-1}（当i=0时使用I^l_0）作为输入，而第二个编码器将当前右帧I^r_i和先前生成的右透射帧T̂^r_{i-1}（当i=0时使用I^r_0）作为输入。第三个编码器使用当前透射深度帧对{D^l_i, D^r_i}和先前生成的透射深度帧对{D̂^l_{i-1}, D̂^r_{i-1}}作为输入。第四个编码器将当前帧对前后N帧{I^l_{i+n}, I^r_{i+n}}（n ∈ [-N, N]，总共2N+1对）及其相应的透射深度帧对{D̂^l_{i+n}, D̂^r_{i+n}}作为输入。观察图3，4个编码器共享相似的结构。编码器的每个分支采用三个特征提取块(FE)，每个由b个卷积块和b个CBAM（b=1,2,3）组成，然后是三个特征增强模块。然后解码器将融合和增强的特征图f̃^{lrd}_3作为输入，包括四个扩张卷积块、两个CBAM块，接着是两组反卷积和卷积块，以生成最终的透射帧{T̂^l_i, T̂^r_i}。

### A. 统一结构的架构

如图3所示，CVEM、DGEM和CFEM以级联方式在四个编码器分支之间建立关系。除了门控控制器的差异外，它们的结构是相似的。第k个CVEM将当前级别的左右视图特征图f^l_k和f^r_k作为输入并获得三个输出：f̃^l_k、f̃^r_k和f^{lr}_k。然后，DGEM接收由CVEM生成的增强特征f^{lr}_k和深度特征f^d_k，生成：f̃^{lr}_k、f̃^d_k和f^{lrd}_k。接下来，CFEM接收从DGEM获得的深度增强特征图f^{lrd}_k和帧间特征f^f_k，产生f̃^{lrdf}_k、f̃^f_k和f^{lrdf}_k。更新的特征图然后通过卷积块和CBAM处理，然后在更高维度中进行下一次特征增强。

接下来，我们使用一个DGEM作为例子来介绍每个模块内的具体操作（见图5）。设f^{lr}_k和f^d_k的k级特征上每个位置(x,y)的特征向量分别表示为f^{lr}_k(x,y) ∈ R^{1×c}和f^d_k(x,y) ∈ R^{1×c}，其中c表示嵌入维度。我们对特征图f^{lr}_k和f^d_k执行全局平均池化(GAP)以获得全局特征向量g^{lr}_k和g^d_k。对于每个位置(x,y)，我们连接特征向量f^{lr}_k(x,y)、f^d_k(x,y)、g^{lr}_k和g^d_k，形成点特征组：

G^d_k(x,y) = cat(f^{lr}_k(x,y), f^d_k(x,y), g^{lr}_k, g^d_k) (4)

其中cat(·)表示连接操作。

受多头注意力机制[68]的启发，我们采用多个头H_j(·)（j ∈ [1,J]）来分别处理每个点特征组G^d_k(x,y)。然后将它们连接起来并使用线性层来集成特征。因此过程可以表示如下：

f̃^{lr}_k(x,y), f̃^d_k(x,y) = linear(cat(H_1(G^d_k(x,y)), ..., H_J(G^d_k(x,y)))) (5)

在每个H_j(·)中，构造相似性矩阵M^d_j(x,y)以在四个组件之间建立关系。然后，相似性矩阵M^d_j(x,y)被放入门控控制器中以控制各种特征相关性提取的方向。CVEM、DGEM和CFEM的门控控制器设计将在下一部分说明。在门控控制器的作用下，网络学习四个组件之间的相关性，通过矩阵乘法动态调整特征向量组。接下来，向量组中调整后的特征向量然后被重新分配到它们相应的位置，产生更新的特征图：f̃^{lr}_k、f̃^d_k。为了获得融合特征并为后续特征增强模块提供全局引导，我们连接两个结果特征图并使用1×1卷积集成它们，产生融合特征图f^{lrd}_k。

### B. 门控控制器

三个特征增强模块以级联方式在四个编码器之间建立关系。门控控制器旨在控制三个不同任务的特征相关性探索范围。对于DGEM，用于提取特征图的视频帧对是点对点对齐的。该模块的门控控制器将第j个相似性矩阵M^d_j(x,y)作为输入并添加反对角矩阵M1。然后应用softmax层来约束反对角值接近0。这样的门控控制器G1(·)防止一个模态特征图的全局信息与另一个模态特征图的局部信息之间的交互。

G1(M^d_j(x,y)) = softmax(M^d_j(x,y) + M1) (6)

其中M1 = [[-100.0, 0, 0, 0], [0, -100.0, 0, 0], [0, 0, -100.0, 0], [0, 0, 0, -100.0]]

相反，CVEM和CFEM的输入配对特征图未对齐。在两个特征图中的每一个内探索局部和全局相关性是有意义的。具体来说，该模块的门控控制器G2(·)将第j个相似性矩阵M^f_j(x,y)作为输入，添加矩阵M2，然后应用softmax层，可以表示为：

G2(M^f_j(x,y)) = softmax(M^f_j(x,y) + M2) (7)

其中M2 = [[0, -100.0, 0, -100.0], [-100.0, 0, -100.0, 0], [-100.0, -100.0, -100.0, -100.0], [-100.0, -100.0, -100.0, -100.0]]

---

## V. 实验

### A. 数据准备

由于目前没有现成的双目视频反射移除数据集，我们构建了一个包含用于网络训练和测试的合成数据以及用于测试的真实数据的数据集。图6显示了数据集中每种数据类型的样本集。我们数据的详细信息如下。

**合成数据。** 由于视频通常包含物体运动或相机运动，准确获得混合视频的ground truth极具挑战性。我们选择立体模糊数据集[65]，包含配对的左右视图视频，来合成用于网络训练和测试的序列混合双目视频。它包含135个双目视频及其相应的深度图。创建每对混合双目视频需要两组双目视频作为透射和反射场景，然后基于alpha混合模型[27]逐帧合成。我们在[0.8, 1.0]中随机采样α，并应用伽马校正[69]来映射自然和线性颜色空间。我们总共合成了67组双目混合视频，表示为Syn-Dynamic，分辨率为256×256，其中50组用于训练，17组用于测试。每个混合视频包含40-100帧。我们在图6的第一列中展示了一对合成样本，包括左右混合图像、左透射和反射层及其相应的深度图。

**静态场景的真实数据。** 我们使用ZED[70]双目相机来捕获真实数据，它可以获得1280×720彩色图像并得出相应的深度图。首先，真实数据集包括一部分静态场景数据，这使得定量和定性比较我们的方法与现有单图像反射移除方法成为可能。该数据集表示为Real-Static，包括14组配对混合和清洁双目视频及相应深度图，通过添加和移除玻璃捕获，其中透射和反射场景都保持静态。每个视频有30帧。我们在图6的第二列中展示了一个样本。

**动态场景的真实数据。** 考虑到动态场景的多样性，我们分别收集具有相机运动的场景(Real-Camera-Motion)和具有物体运动的场景(Real-Object-Motion)用于方法的定性评估。Real-Camera-Motion和Real-Object-Motion数据集都有10组双目视频及相应深度图，通过ZED[70]双目相机通过玻璃捕获。两种类型的数据集都有150帧的长度。请注意，捕获的混合视频没有相应的ground truth，因为在移除玻璃后不可能记录相同的运动。因此，它们仅用于定性评估。一些例子显示在图6的第三列中。

### B. 实现细节和评估策略

**网络训练和损失函数。** 在训练期间，我们使用L1损失作为生成配对透射深度图{D̂^l_i, D̂^r_i}的监督，SSIM损失[8]、带伽马校正的重建损失[34][69]、MSE损失、由VGG19模型[71]计算的感知损失[27]作为透射帧{T̂^l_i, T̂^r_i}的监督，分别表示为：L1、Lssim、Lrec、Lmse和Lmp。总损失函数定义为：

L = ω1L1 + ω2Lssim + ω3Lrec + ω4Lmse + ω5Lmp (8)

其中ω1、ω2、ω3、ω4和ω5经验设置为：ω1 = 0.4、ω2 = 0.4、ω3 = 0.4、ω4 = 0.4和ω5 = 0.1。

我们的方法使用PyTorch工具箱[72]在NVIDIA GeForce RTX 3090 GPU上实现。我们采用Adam[73]优化器来训练我们的模型，批量大小为1。初始学习率设置为1e-4，在50个epoch后除以10。

**评估策略。** 我们在Syn-Dynamic数据集和Real-Static数据集上进行定量实验。我们采用四个评估指标：结构相似性指数(SSIM)[74]、峰值信噪比(PSNR)[75]、局部均方误差(LMSE)[76]和归一化交叉相关(NCC)[49]。SSIM、PSNR和LMSE是反射移除中三个常用的评估指标，而NCC基于统计测量计算两个图像之间的相关性。

### C. 与现有方法的比较

我们将我们的方法与两种多图像反射移除方法(MIRM[16]和Dual-Pixel[17])以及六种单图像反射移除方法(Dong[42]、YTMT[44]、MCDRNet[43]、HGRR[39]、RINet[10]和Zhu[45])进行比较。

**合成数据评估。** Syn-Dynamic数据集的定量结果显示在表I的第一组中。可以看出，我们的方法在所有指标上都超过了现有方法，这表明我们的方法在像素值准确性和透射场景结构一致性方面有效地移除反射并生成高质量的透射帧。一些定性结果显示在图7中。放大图中的细节，我们的方法在移除反射和保留透射帧细节方面超越其他方法变得更加清晰和直观。

**真实数据评估。** 对于Real-Static双目视频数据集，我们保持玻璃两侧的场景不变，相机位置固定，确保每帧的内容相同。这种设置使我们的算法能够与其他单图像反射移除方法在真实世界场景中进行定量比较。如表I的第二组所示，我们的方法在真实数据的大多数定量指标上超过其他比较方法。虽然我们的方法在LMSE得分上略低于MCDRNet[43]，但它在其他关键指标上取得了优异的结果，如PSNR、SSIM和NCC，这些指标反映了结构一致性、感知相似性和与ground truth的相关性。这些指标强调了我们方法在提供高质量反射移除方面的优势。观察图8，我们的方法最有效地移除了真实世界数据中的反射，展示了其对真实世界场景的更强适应性。此外，如图8的最后一列所示，我们的深度估计模块也产生了高质量的深度图，使我们的方法能够有效地利用深度信息进行引导反射移除。

在更一般的真实视频中获得混合双目视频的ground truth极其困难。这是因为在移除玻璃后不可能重现之前的相机或场景运动轨迹。因此，我们只在Real-Camera-Motion数据集和Real-Object-Motion数据集上进行定性比较。图9和图10说明了一些帧的定性结果。从最后一列可以明显看出，我们的方法估计了高质量的透射深度图，这允许在我们设计的统一结构(CVEM、DGEM和CFEM)内进行跨视角、深度引导和跨帧特征增强，导致优异的反射移除结果。此外，我们方法的优势在视频序列中反射移除结果的连续性方面也很明显。视频的具体实验结果在补充材料中提供。

### D. 消融研究

**深度引导的有效性。** 为了验证深度引导的有效性，我们在表II中报告了在不同实验设置下Syn-Dynamic数据集上的PSNR和SSIM指标。模型1表示不使用深度图的模型，其中通过移除深度估计模块生成结果。可以观察到，该模型显示出最差的PSNR和SSIM性能。当我们添加单目深度引导(表示为模型2)时，即模型取得了更好的结果。此外，在模型3中，我们只用连接操作替换DGEM与完整模型来评估深度引导方式。因此，在使用所有提出的组件的情况下，我们的完整模型(模型4)显示出最佳的PSNR和SSIM。此外，为了彻底评估我们深度引导的有效性，我们将我们方法的深度估计结果与现有强大的深度估计方法[77]进行比较。可视化比较结果显示在图11中。尽管这种单目深度估计方法在大多数场景中表现良好，但当输入包含反射时，它产生伪深度。

**引导序列的研究。** 在验证了表中深度引导的重要性之后，我们然后进行实验来确定何时引入深度引导，以及深度引导、跨视角和跨帧特征增强的最有效顺序。在表III中，我们展示了具有不同特征增强序列的六个不同模型的结果。实验结果表明完整模型取得了最佳性能。这一结果验证了我们的假设：首先执行跨视角增强以进行全面场景感知，然后引入深度引导为反射移除提供线索，最后应用跨帧特征增强产生最佳反射移除结果。

**统一结构的有效性。** 在表IV的模型1、2、3中，我们首先分别移除三个不同特征增强模块中的每一个来验证每个模块的有效性。结果表明每个模块都有助于整体模型性能的改善。接下来，我们构建模型4和模型5，其中从两种类型的统一结构模块中移除门控控制器，并在两种情况下都观察到性能下降。

**统一结构设计的研究。** 首先，设计实验来验证我们在统一结构内选择GAP还是最大池化作为全局表示操作。结果显示在表V中，显示当将GAP替换为最大池化时性能略有下降，强化了我们选择GAP作为更鲁棒的全局表示方法。此外，为了验证矩阵M1和M2中值的选择，我们使用其他超参数值进行实验，包括-10、-1000和-10000。表VI中的结果表明，当变化小于-100时，性能没有显著变化。因此证明-100足够小以抑制门控控制器中的相关性。然后，我们研究统一结构内头数J的影响。为此，我们训练具有不同头数J(J ∈ [2,5])的多个模型。如表VII所示，我们发现J=4产生最佳性能。当我们增大J时，性能不会增加而参数数量增加。因此，我们的完整模型用J=4训练。

### E. 模型复杂度分析

表VIII显示了在RTX 3090 GPU上实现的运行时间、参数和GFLOPs比较。为了公平比较，输入图像都设置为256×256。虽然我们的方法在这些方面没有显著优势，但与其他方法相比，运行时间、参数和GFLOPs的差异并不显著。我们的方法专门为双目视频反射移除设计，这需要提取和融合多方面特征，包括跨帧时间特征、跨视角空间特征和深度引导特征。这种额外的复杂性本质上增加了与其他方法相比模型的计算需求。在我们未来的工作中，我们将致力于通过优化我们的方法来改善效率同时保持其高性能来解决这些问题。

---

## VI. 结论

在本文中，我们提出了DGR2-Net，一种端到端的深度引导网络，用于双目混合视频的有效反射移除。受人类双目视觉系统的启发，我们的方法利用深度估计来区分真实和伪深度，实现精确的透射场景恢复。所提出的统一结构结合了深度引导、跨视角和跨帧特征增强，使用定制门控控制器来优化特征交互。我们构建了用于网络训练和测试的混合双目视频数据集，为未来研究提供了基准。在合成和真实世界数据集上的广泛实验表明，我们的方法超越了现有方法。

---

## 参考文献

[1] W.-Y. Hsu, and W.-J. Wu, "Object Detection Using Structure-Preserving Wavelet Pyramid Reflection Removal Network," IEEE Trans. Instrum. Meas., vol. 71, pp. 1-11, 2022.

[2] R. Wan, B. Shi, H. Li, L.-Y. Duan, and A. C. Kot, "Face Image Reflection Removal," Int. J. Comput. Vis., vol. 129, no. 2, pp. 385–399, 2021.

[3] B.-J. Han, and J.-Y. Sim, "Single Image Reflection Removal Using Non-Linearly Synthesized Glass Images and Semantic Context," IEEE Access, vol. 7, pp. 170796-170806, 2019.

[4] Y. Liu, Y. Li, S. You, and F. Lu, "Semantic Guided Single Image Reflection Removal," ACM Trans. Multim. Comput. Commun. Appl., vol. 18, no. 3S, pp. 151:1-151:23, 2022.

[5] A. Kosuge, L. Yu, M. Hamada, and T. KURODA, "A Deep Metric Learning-Based Anomaly Detection System for Transparent Objects Using Polarized-Image Fusion," IEEE Open J. Ind. Electron. Soc., vol. 4, pp. 205 - 213, 2023.

[6] T. P. Kapusi, L. Kovacs, and A. Hajdu "Deep learning-based anomaly detection for imaging in autonomous vehicles," in Proc. IEEE Conf. Inf. Technol. Data Science (CITDS), 2022, pp. 142-147.

[7] Q. Fan, J. Yang, G. Hua, B. Chen, and D. P. Wipf, "A generic deep architecture for single image reflection removal and image smoothing," in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), 2017, pp. 3238-3247.

[8] R. Wan, B. Shi, H. Li, L.-Y. Duan, A.-H. Tan, and A. C. Kot, "CoRRN: Cooperative reflection removal network," IEEE Trans. Pattern Anal. Mach. Intell., vol. 42, no. 12, pp. 2969-2982, 2019.

[9] R. Wan, B. Shi, H. Li, Y. Hong, L.-Y. Duan, and A. C. Kot, "Benchmarking Single-Image Reflection Removal Algorithms," IEEE Trans. Pattern Anal. Mach. Intell., vol. 45, no. 2, pp. 1424-1441, 2023.

[10] L. He, F. Li, R. Cong, and Y. Zhao, "Reflection intensity guided single image reflection removal and transmission recovery," IEEE Trans. Multim., vol. 26, pp. 5026–5039, 2024.

[11] J. Sun, Y. Chang, C. Jung, and J. Feng, "Multi-Modal Reflection Removal Using Convolutional Neural Networks," IEEE Signal Process. Lett., vol. 26, no. 7, pp. 1011–1015, 2019.

[12] R. Wan, B. Shi, A.-H. Tan, and A. C. Kot, "Depth of field guided reflection removal," IEEE Int. Conf. Image Process. (ICIP), 2016, pp. 21-25.

[13] O. L. Meur, T. Baccino, and A. Roumy, "Prediction of the inter-observer visual congruency(IOVC) and application to image ranking," ACM Int. Conf. multim. (MM), 2011, pp. 373-382.

[14] Y. Y. Schechner, N. Kiryati, and Ronen Basri, "Separation of Transparent Layers using Focus," Int. J. Comput. Vis., vol. 39, no. 1, pp. 25–39, 2000.

[15] Y. Y. Schechner, N. Kiryati, and Ronen Basri, "Separation of Transparent Layers using Focus," in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), 1998, pp. 1061-1066.

[16] T. Li, Y.-H. Chan, and D. P.-K. Lun, "Improved multiple-image-based reflection removal algorithm using deep neural networks," IEEE Trans. Image Process., vol. 30, pp. 68-79, 2021.

[17] A. Punnappurath, and M. S. Brown, "Reflection Removal Using a Dual-Pixel Sensor," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2019, pp. 1556-1565.

[18] S. Niklaus, X. C. Zhang, J. T. Barron, N. Wadhwa, R. Garg, F. Liu, and T. Xue, "Learned Dual-View Reflection Removal," in Proc. IEEE/CVF Wint. Conf. on Applic. of Comput. Vis. (WACV), 2021, pp. 3712–3721.

[19] Y. Chang, C. Jung, and J. Sun, "Joint reflection removal and depth estimation from a single image," IEEE Trans. Cybern., vol. 51, no. 12, pp. 5836-5849, 2021.

[20] A. Levin, A Zomet, and Y. Weiss, "Learning to perceive transparency from the statistics of natural scenes," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2002, pp. 1247-1254.

[21] A. Levin, and Y. Weiss, "User assisted separation of reflections from a single image using a sparsity prior," IEEE Trans. Pattern Anal. Mach. Intell., vol. 29, no. 9, pp. 1647-1654, 2007.

[22] Y. Li, and M. S. Brown, "Exploiting reflection change for automatic reflection removal," IEEE Int. Conf. Comput. Vis. (ICCV), 2013, pp. 2432-2439.

[23] Y. Li, and M. S. Brown, "Single image layer separation using relative smoothness," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2014, pp. 2752-2759.

[24] Y. Shih, D. Krishnan, F. Durand, and W. T. Freeman, "Reflection removal using ghosting cues," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2015, pp. 3193-3201.

[25] R. Wan, B. Shi, L.-Y. Duan, A.-H. Tan, W. Gao, and A. C. Kot, "Region-aware reflection removal with unified content and gradient priors," IEEE Trans. Image Process., vol. 27, no. 6, pp. 2927-2941, 2018.

[26] Y. Yang, W. Ma, Y. Zheng, J.-F. Cai, and W. Xu "Fast Single Image Reflection Suppression via Convex Optimization," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2019, pp. 8141-8149.

[27] X. C. Zhang, R. Ng, and Q. Chen, "Single image reflection separation with perceptual losses," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2018, pp. 4786-4794.

[28] K. Wei, J. Yang, Y. Fu, D. P. Wipf, and H. Huang, "Single image reflection removal exploiting misaligned training data and network enhancements," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2019, pp. 8178-8187.

[29] S. Kim, Y. Huo, and S.-E. Yoon, "Single image reflection removal with physically-based training images," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2020, pp. 5164-5173.

[30] Z. Wu, C. Zhuang, J. Shi, J. Guo, J. Xiao, X. Zhang, and D.-M. Yan, "Single-Image Specular Highlight Removal via Real-World Dataset Construction," IEEE Trans. Multim., vol. 24, pp. 3782-3793, 2022.

[31] C. Lei, X. Huang, M. Zhang, Q. Yan, W. Sun, and Q. Chen, "Polarized reflection removal with perfect alignment in the wild," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2020, pp. 1750-1758.

[32] H. Zhang, X. Xu, H. He, S. He, G. Han, J. Qin, and D. Wu, "Fast user-guided single image reflection removal via edge-aware cascaded networks," IEEE Trans. Multim., vol. 22, no. 8, pp. 2012-2023, 2019.

[33] D. Heydecker, G. Maierhofer, A. I. Aviles-Rivero, Q. Fan, et al., "Mirror, mirror, on the wall, who's got the clearest image of them all?—A tailored approach to single image reflection removal," IEEE Trans. Image Process., vol. 28, no. 12, pp. 6185-6197, 2019.

[34] Q. Wen, Y. Tan, J. Qin, W. Liu, G. Han, and S. He, "Single image reflection removal beyond linearity," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2019, pp. 3771-3779.

[35] Q. Zheng, B. Shi, J. Chen, X. Jiang, L.-Y. Duan, and A. C. Kot, "Single image reflection removal with absorption effect," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2021, pp. 13395-13404.

[36] C. Zhu, R. Wan, and B. Shi, "Neural Transmitted Radiance Fields," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2022, pp. 38994-39006.

[37] H. Duan, W. Shen, X. Min, Y. Tian, J. H. Jung, X. Yang, and G. Zhai, "Develop then rival: A human vision-inspired framework for superimposed image decomposition," IEEE Trans. Multim., 2022.

[38] Y. Hong, Q. Zheng, L. Zhao, X. Jiang, A. C. Kot, and B. Shi, "Panoramic image reflection removal," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2021, pp. 7762-7771.

[39] Y. Zhu, X. Fu, Z. Zhang, A. Liu, Z. Xiong, and Z. -J. Zha, "Hue Guidance Network for Single Image Reflection Removal," IEEE Trans. Neural Netw. Learn. Syst., early access, doi: 10.1109/TNNLS.2023.3270938.

[40] J. Yang, D. Gong, L. Liu, and Q. Shi, "Seeing deeply and bidirectionally: A deep learning approach for single image reflection removal," in Proc. Eur. Conf. Comput. Vis. (ECCV), 2018, pp. 654-669.

[41] C. Li, Y. Yang, K. He, S. Lin, and J. E. Hopcroft, "Single image reflection removal through cascaded refinement," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2020, pp. 3562-3571.

[42] Z. Dong, K. Xu, Y. Yang, H. Bao, W. Xu, and R. W. H. Laul, "Location-aware single image reflection removal," IEEE Int. Conf. Comput. Vis. (ICCV), 2021, pp. 4997-5006.

[43] B. Song, J. Zhou, and H. Wu, "Multistage curvature-guided network for progressive single image reflection removal," IEEE Trans. Circuits Syst. Video Technol., vol. 32, no. 10, pp. 6515-6529, 2022.

[44] Q. Hu, and X. Guo, "Trash or treasure? an interactive dual-stream strategy for single image reflection separation," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2021, pp. 24683-24694.

[45] Y. Zhu, X. Fu, P.-T. Jiang, H. Zhang, Q. Sun, J. Chen, Z.-J. Zha, and B. Li, "Revisiting single image reflection removal in the wild," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2024, pp. 25468-25478.

[46] B. H. P. Prasad, G. R. K. S, R. B. Lokesh, K. Mitra, and S. Chowdhury, "V-desirr: Very fast deep embedded single image reflection removal," IEEE Int. Conf. Comput. Vis. (ICCV), 2021, pp. 2390-2399.

[47] Y.-T. Peng, K.-H. Cheng, I-S. Fang, W.-Y. Peng, and J.-S. Wu, "Single image reflection removal based on knowledge-distilling content disentanglement," IEEE Signal Process. Lett., vol. 29, pp. 568-572, 2022.

[48] H. RahmaniKhezri, S. Kim, and M. Hefeeda, "Unsupervised single-image reflection removal," IEEE Trans. Multim., vol. 24, pp. 3782-3793, 2022.

[49] T. Xue, M. Rubinstein, C. Liu, and W. T. Freeman, "A computational approach for obstruction-free photography," ACM Trans. Graph., vol. 34, no. 4, pp. 79:1-79:11, 2015.

[50] S. K. Nayar, X.-S. Fang, and T. E. Boult, "Separation of Reflection Components Using Color and Polarization," Int. J. Comput. Vis., vol. 21, no. 3, pp. 163-186, 1997.

[51] N. Kong, Y.-W. Tai, and Joseph S. Shin, "A Physically-Based Approach to Reflection Separation: From Physical Modeling to Constrained Optimization," IEEE Trans. Pattern Anal. Mach. Intell., vol. 36, no. 2, pp. 209-221, 2014.

[52] Y. Lyu, Z, Cui, S. Li, M. Pollefeys, and B. Shi, "Reflection Separation using a Pair of Unpolarized and Polarized Images," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2019, pp. 14532-14542.

[53] C. Lei, X. Huang, M. Zhang, Q. Yan, W. Sun, and Q. Chen, "Polarized Reflection Removal With Perfect Alignment in the Wild," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2020, pp. 1747-1755.

[54] Y. Lyu, Z. Cui, S. Li, M. Pollefeys, and B. Shi, "Physics-Guided Reflection Separation From a Pair of Unpolarized and Polarized Images," IEEE Trans. Pattern Anal. Mach. Intell., vol. 45, no. 2, pp. 22151-2165, 2023.

[55] Y.-L. Liu, W.-S. Lai, M.-H. Yang, Y.-Y. Chuang, and J.-B. Huang, "Learning to See Through Obstructions," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2020, pp. 14203-14212.

[56] Y.-L. Liu, W.-S. Lai, M.-H. Yang, Y.-Y. Chuang, and J.-B. Huang, "Learning to See Through Obstructions With Layered Decomposition," IEEE Trans. Pattern Anal. Mach. Intell., vol. 44, no. 11, pp. 8387-8402, 2022.

[57] A. Nandoriya, M. A. Elgharib, C. Kim, M. Hefeeda, and Wojciech Matusik, "Video reflection removal through spatio-temporal optimization," in Proc. IEEE Int. Conf. Comput. Vis. (ICCV), 2017, pp. 2430-2438.

[58] K. Gai, Z. Shi, and C. Zhang, "Blind Separation of Superimposed Moving Images Using Image Statistics," IEEE Trans. Pattern Anal. Mach. Intell., vol. 34, no. 1, pp. 19-32, 2012.

[59] J. Yang, H. Li, Y. Dai, and R. T. Tan, "Robust Optical Flow Estimation of Double-Layer Images under Transparency or Reflection," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2016, pp. 1410-1419.

[60] Y. Chang, C. Jung, J. Sun, and F. Wang, "Siamese Dense Network for Reflection Removal with Flash and No-Flash Image Pairs," Int. J. Comput. Vis., vol. 128, no. 6, pp. 1673-1698, 2020.

[61] C. Lei, and Q. Chen, "Robust reflection removal with reflection-free flash-only cues," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2021, pp. 14811-14820.

[62] Y. Hong, Y. Lyu, S. Li, and B. Shi, "Near-Infrared Image Guided Reflection Removal," in Proc. IEEE Int. Conf. Multim. Expo. (ICME), 2020, pp. 1-6.

[63] Y. Hong, Y. Lyu, S. Li, G. Cao, and Boxin Shi, "Reflection Removal With NIR and RGB Image Feature Fusion," IEEE Trans. Multim., vol. 25, pp. 7101–7112, 2023.

[64] Y. Hong, Y. Chang, J. Liang, L. Ma, T. Huang, and B. Shi, "Light Flickering Guided Reflection Removal," Int. J. Comput. Vis., early access, 2024, doi: https://doi.org/10.1007/s11263-024-02073-z.

[65] S. Zhou, J. Zhang, W. Zuo, H. Xie, J. Pan, and J. S. Ren, "DAVANet: Stereo Deblurring With View Aggregation," in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogit. (CVPR), 2019, pp. 10996-11005.

[66] O. Ronneberger, P. Fischer, and T. Brox, "U-Net: Convolutional Networks for Biomedical Image Segmentation," in Medical Image Comput. Comput.-Assis Int. (MICCAI), 2015, vol. 9351, pp. 234–241.

[67] S. Woo, J. Park, J.-Y. Lee, and I. S. Kweon, "CBAM: Convolutional Block Attention Module," in Proc. Eur. Conf. Comput. Vis. (ECCV), 2018, vol: 11211, pp. 3-19.

[68] A. Vaswani, N. Shazeer, N. Parmar, J. Uszkoreit, L. Jones, A. N. Gomez, L. Kaiser, and I. Polosukhin, "Attention is All you Need," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2017, pp. 5998-6008.

[69] R. Wan. B. Shi, H. Li, Y. Hong, L.-Y. Duan, and A. C. Kot, "Benchmarking single-image reflection removal algorithms," in IEEE Int. Conf. Comput. Vis. (ICCV), 2017, pp. 3922-3930.

[70] Stereolabs. https://www.stereolabs.com/

[71] K. Simonyan, and A. Zisserman, "Very deep convolutional networks for large-scale image recognition," 2014, arXiv:1409.1556. [Online]. Available: http://arxiv.org/abs/1409.1556

[72] A. Paszke, S. Gross, F. Massa, A. Lerer, J. Bradbury, G. Chanan, T. Killeen, Z. Lin, N. Gimelshein, L. Antiga, A. Desmaison, A. Kopf, E. Z. Yang, Z. DeVito, M. Raison, A. Tejani, S. Chilamkurthy, B. Steiner, L. Fang, J. Bai, and S. Chintala, "PyTorch: An Imperative Style, High-Performance Deep Learning Library," in Proc. Adv. Neural Inf. Process. Syst. (NeurIPS), 2019, pp. 8024-8035.

[73] D. P. Kingma, and J. Ba, "Adam: A method for stochastic optimization," 2014, arXiv:1412.6980. [Online]. Available: http://arxiv.org/abs/1412.6980

[74] Z. Wang, A. C. Bovik, H. R. Sheikh, and E. P. Simoncelli, "Image quality assessment: from error visibility to structural similarity," IEEE Trans. Image Process., vol. 13, no. 4, pp. 600-612, 2004.

[75] Q. Huynh-Thu, M. Ghanbari, "Scope of Validity of PSNR in Image/Video Quality Assessment," Electron. lett., vol. 44 no. 13: 800-801, 2008.

[76] R. B. Grosse, M. K. Johnson, E. H. Adelson, and W. T. Freeman, "Ground truth dataset and baseline evaluations for intrinsic image algorithms," IEEE Int. Conf. Comput. Vis. (ICCV), 2009, pp. 2335-2342.

[77] L. Yang, B. Kang, Z. Huang, Z. Zhao, X. Xu, J. Feng, H. Zhao, "Depth Anything V2," 2024, arXiv:2406.09414. [Online]. Available: http://arxiv.org/abs/2406.09414
