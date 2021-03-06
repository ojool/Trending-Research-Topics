



# 论文信息简介

## 标题

《Building Robust Phishing Detection System: an Empirical Analysis》

~~翻译：构建一个强大的网络钓鱼攻击检测系统：一个经验分析~~

## 作者

Jehyun Lee, Pingxiao Yey, Ruofan Liu, Dinil Mon Divakarany, Mun Choon Chan

## 出处

[NDSS Symposium 2020 Programme](https://www.ndss-symposium.org/wp-content/uploads/2020/02/23007.pdf)

## 笔者

[殇AD](https://github.com/LCX666)

------



# 论文摘要

本文主要讲述了近年来检测网络钓鱼攻击引入了机器学习的技术来进行辅助，并取得了较好的检测结果。但是其分类器也容易受到攻击者利用机器学习的手段来进行对抗攻击。所以，本文提出了自己的方法来改进机器学习的应用方法，在前面的工作基础上，采取了投票系统，并加入了很多相应的规避策略。

------



# 论文框图

![框架](./框架.png)

本文通过一个背景介绍引入当前机器学习在网络钓鱼链接检测中的应用优势与缺陷不足。并将自己考虑到的威胁模型英语与传统的检测方式进行实验，证明了传统的检测方法会受到攻击抵抗来逃避攻击。为了减少这些攻击的逃逸，作者还添加了相应的对策，构建了一个新系统。作者构建的新系统确实提高了系统的鲁棒性和灵活性。并将新系统在不同的规避策略下进行评估，进而得到一些结论。在这些策略讨论的基础上，还得出了一些未来潜在的研究方向。

------



# 主要内容

本文主要讲述了传统的利用机器学习。将网络钓鱼页面与良心页面的信息提取出来，并将这些页面的url和大型数据标签构建成了一个训练集，并在这个集合上进行训练，进而可以构建一个二进制分类器。

而这种解决方案也很容易受到网络的攻击，攻击者可以利用自己的知识，构建一个与良性网页相似的特征值来逃避分类器的筛选，并且还可以主动进行针对训练。并且由于检测系统是公共公开的，攻击者可以很方便的检测到自己的攻击结果。并对被捕获的特征进行修改。这些方法经过最近的工作证明，确实可以降低传统机器学习特征分类器的检测性能。

未来避免对抗攻击和攻击检测逃逸，作者写了两个方向的对策。一个是提出更具有特点的网页页面特征值，这使得攻击者更难模仿和复制。二是减少一些重要特征的权重值，使得这些很容易被利用的值不会完全决定分类器决定。

而本文作者就是采用了第二种方法，降低了分类检测器训练集中的特征权重，使得特征数量增多而单个特征的决定权降低。此外，未来避免攻击者的采用相同的训练集对分类器的训练特征进行捕获，作者提出，在特征里面随机的选取一些来作为评判的标准，这样可以极大的提升分类系统的不确定性，进而提高系统的准确性和鲁棒性。

作者在后续部分详细地介绍了整个实验的过程，以及对各个规避策略对系统的影响的检测结果，最后对每个检测的结果进行分析，计算，得到了这个新系统具有更加优良的性能，更能抵抗攻击者的对抗攻击，进而进行检测逃避。整个新系统具有很高的通用性、鲁棒性和有效性。

最后作者还通过对新规避方法的实验检测，得出了一些未来发展的方向和规避策略的形势。并展示了一部分的相关作品。

------



# 创新点

1. 特征等级差异化
2. 随机化引入特征排序
3. 相同训练集创建出不同检测器
4. 采用多投票的方式来综合评估

------



# 目前缺点

1. 随机化的特征排序方法具有不确定性，很难确定随机系统分配到的特征值等级是否合理。
2. 系统只能应用于与机器学习的抵抗线网络钓鱼攻击，对于人工的专一的网络钓鱼攻击并未进行验证。

------



# 可能的解决方案

1、针对上述缺点1，可以通过在实际使用前对随机化参数进行检验，通过实践的反馈来了解随机的参数是否合理，并通过设计梯度下降等方法来减小随机数的合理范围。也可以使用伪随机数，通过只在某些特定的范围内的数值，来定向得到优秀参数，并同时兼顾随机性。



2、针对上述缺点2，对于人工构造的攻击来讲，单纯应用机器学习的方式，以机器来对抗机器不能全部解决这个问题，或许可以在机器中间加入部分的随机人为检测来协调机器的行为。

------



# 总结

本篇论文提出的方法设计了一个网络钓鱼链接的识别检测系统，通过自己设计的随机参数来使得系统的工作稳定性和随机性得到了提升，进而提升了系统的有效性。同时通过研究逃避策略，引入机器学习的样本，对样本数据进行分析和训练，提高了系统的鲁棒性。为网络钓鱼识别提供了一种比较不错的平台和方法。具有一定的高效性。
