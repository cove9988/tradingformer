![Informer: Beyond Efficient Transformer for Long Sequence Time-Series Forecasting](https://pica.zhimg.com/v2-e0d3335bd0434aae2b4c899ac8e034db_1440w.jpg?source=172ae18b)

<article class="Post-Main Post-NormalMain" tabindex="-1">
    <header class="Post-Header">
        # Informer: Beyond Efficient Transformer for Long Sequence Time-Series Forecasting

        <meta itemprop="name" content="之乎者也">

        <meta itemprop="image" content="https://pic2.zhimg.com/v2-abed1a8c04700ba7d72b45195223e0ff_l.jpg?source=172ae18b">

        <meta itemprop="url" content="https://www.zhihu.com/people/zhi-hu-zhe-ye-59-68-87">

        <meta itemprop="zhihu:followerCount">[![之乎者也](https://pic2.zhimg.com/v2-abed1a8c04700ba7d72b45195223e0ff_xs.jpg?source=172ae18b)](https://www.zhihu.com/people/zhi-hu-zhe-ye-59-68-87)

        [之乎者也](https://www.zhihu.com/people/zhi-hu-zhe-ye-59-68-87)



        <button type="button" class="Button FollowButton Button--primary Button--blue"><span style="display:inline-flex;align-items:center">​<svg class="Zi Zi--Plus FollowButton-icon" fill="currentColor" viewBox="0 0 24 24" width="1.2em" height="1.2em"><path d="M13.491 10.488s-.012-5.387 0-5.998c-.037-1.987-3.035-1.987-2.997 0-.038 1.912 0 5.998 0 5.998H4.499c-1.999.01-1.999 3.009 0 3.009s5.995-.01 5.995-.01v5.999c0 2.019 3.006 2.019 2.997 0-.01-2.019 0-5.998 0-5.998s3.996.009 6.004.009c2.008 0 2.008-3-.01-3.009h-5.994z" fill-rule="evenodd"></path></svg></span>关注</button>



        <button type="button" class="Button Button--plain">4 人<!-- -->赞同了该文章</button>
    </header>

    **摘要：**

    许多实际应用需要对长时间序列进行预测，例如用电规划。 长序列时间预测（LSTF）要求模型具有较高的预测能力，即有效地捕捉输出和输入之间精确的长程依赖关系的能力。 最近的研究表明，Transformer有提高预测能力的潜力。 然而，Transformer存在几个严重的问题，使其无法直接适用于LSTF，包括二次方的时间复杂度、高内存使用量和编码器-解码器架构的固有限制。 为了解决这些问题，我们为LSTF设计了一个高效的基于Transformer的模型，命名为Informer，具有三个明显的特点。 (i) ProbSparse自注意力机制，在时间复杂度和内存使用方面达到了 ![[公式]](https://www.zhihu.com/equation?tex=O%28LlogL%29) ，并且在序列的依存关系排列上有相当的性能。 (ii)自注意力蒸馏通过将级联层的输入减半来突出主要注意力，并有效地处理极长的输入序列。 (iii) 生成式解码器虽然在概念上很简单，但它是在一次前向操作中预测长时序序列，而不是一步一步的方式，这极大地提高了长时序预测的推理速度。 在四个大规模数据集上进行的广泛实验表明，Informer明显优于现有方法，并为LSTF问题提供了新的解决方案。

    **介绍**

    <figure data-size="normal">![](https://pic1.zhimg.com/80/v2-d1d9ab1c3f4f8539e1e75f77cc1e9214_720w.jpg)</figure>

    时间序列预测是许多领域的关键要素，如传感器网络监测、能源和智能电网管理、经济和金融，以及疾病传播分析。 在这些情况下，我们可以利用大量的过去行为的时间序列数据来进行长期的预测，即长序列时间序列预测（LSTF）。 然而，现有的方法大多是针对短序列数据问题设计的，如预测48个点或更少。越来越长的序列使模型的预测能力受到挑战，以至于这种趋势阻碍了对LSTF的研究。 作为一个经验性的例子，图（1）显示了在一个真实数据集上的预测结果，LSTM网络预测了一个变电站的每小时温度，从短期（12点，0.5天）到长期（480点，20天）。 当预测长度大于48点时，整体性能差距很大（图（1b）中的实心星），MSE上升到不满意的性能，推理速度急剧下降，LSTM模型开始失效。

    LSTF的主要挑战是提高预测能力以满足日益增长的长序列需求，这需要  
    (a)非凡的长距离对齐能力  
    (b)对长序列输入和输出的高效操作。 

    Transformer模型在捕捉长距离的依赖性方面显示出比RNN模型更优越的性能。 自我关注机制可以将网络信号行进路径的最大长度减少到理论上最短的O(1)，并避免了递归结构，因此Transformer对LSTF问题显示出巨大的潜力。 然而，自我关注机制违反了要求(b)，因为它在L长度的输入/输出上有L的二次方的计算和内存消耗。 一些大规模的Transformer模型倾注了资源，并在NLP任务上产生了令人印象深刻的结果，但在几十个GPU上的训练和昂贵的部署成本使得这些模型在现实世界的LSTF问题上无法负担。 自我关注机制和Transformer架构的效率成为将其应用于LSTF问题的瓶颈。 因此，在本文中，我们试图回答这个问题。 我们能否改进Transformer模型，使其在计算、内存和结构上都能有效，同时保持更高的预测能力？

    Vanilla Transformer在解决LSTF时有三个明显的局限性：

    1.  **自我注意的二次方计算。** 自我注意机制的原子操作，即规范的点积，导致每层的时间复杂性和内存使用量为 ![[公式]](https://www.zhihu.com/equation?tex=O%28L%5E2%29) 。
    2.  **长输入的堆叠层中的内存瓶颈。** J个编码器/解码器层的堆叠使得总的内存使用量为 ![[公式]](https://www.zhihu.com/equation?tex=O%28J%C2%B7L%5E2%29) ，这限制了模型在接收长序列输入时的可扩展性。
    3.  **预测长输出的速度大幅下降。**普通Transformer的动态解码使得逐步推理的速度和基于RNN的模型一样慢(图(1b))。

    <figure data-size="normal">![](https://pic2.zhimg.com/80/v2-10104102ab4a88d0a7b18b8929787fd9_720w.jpg)</figure>

    过去一些工作都基于启发式的假设，对于attention的计算的选取是由固定的规则决定的，不能自适应得根据具体情况决定计算哪些attention，我们提出的Informer解决了这个问题。

    本文的贡献总结如下：

    * 我们提出Informer成功地增强LSTF问题中的预测能力，从而验证类Transformer的模型的潜在价值，以捕获长时间序列输出和输入之间的各个远程依赖性。
    * 我们提出了ProbSparse自注意力机制来有效地替换常规的自注意力，并实现 ![[公式]](https://www.zhihu.com/equation?tex=O%28LlogL%29) 时间复杂度和 ![[公式]](https://www.zhihu.com/equation?tex=O%28LlogL%29) 内存使用。
    * 我们提出了自注意力蒸馏操作来控制J个堆叠层中的注意分数，并将总空间复杂度急剧降低为 ![[公式]](https://www.zhihu.com/equation?tex=O%28%282-%CF%B5%29LlogL%29) 。
    * 我们提出使用“生成式解码器”来获取长序列输出，而只需要一个前向的步骤，同时避免在推理阶段累积误差的扩散。

    **方法**

    <figure data-size="normal">![](https://pic1.zhimg.com/80/v2-03ba0f2b93e5756396cb38ac474883b0_720w.jpg)</figure>

    **1.高效self-attention机制**

    <figure data-size="normal">![](https://pic3.zhimg.com/80/v2-732425bfe6af15ea3470c109c0b0501a_720w.jpg)</figure>

    Vaswani提出的常规自注意力可以表现为上面的公式，如果对Q中的每个元素分别讨论的话，可以将第i个Query的注意力定义为kernel平滑的概率形式：

    ![[公式]](https://www.zhihu.com/equation?tex=A%28q_i%2CK%2CV%29%3D%5Csum_j%7B%5Cfrac%7Bk%28q_i%2Ck_j%29%7D%7B%5Csum_lk%28q_i%2Ck_l%29%7D%7Dv_j%3D%5Cmathbb%7BE_%7Bp%28k_j%7Cq_i%29%7D%7D%5Bv_j%5D++++++++++%281%29)

    其中 ![[公式]](https://www.zhihu.com/equation?tex=k%28q_i%2Ck_j%29) 为 ![[公式]](https://www.zhihu.com/equation?tex=exp%28%5Cfrac%7B%7Bq_ik_j%5ET%7D%7D%7B%5Csqrt%7Bd%7D%7D%29) ,它需要二次乘积运算和 ![[公式]](https://www.zhihu.com/equation?tex=O%28L_QL_K%29) 内存使用，这是增强预测能力引入的主要缺点。

    先前的一些工作表明，自注意力的概率分布具有潜在的稀疏性，并且他们在所有 ![[公式]](https://www.zhihu.com/equation?tex=p%28k_j%7Cq_i%29) 上设计了一些“选择性”计数策略，而不会显着影响性能。

    <figure data-size="normal">![](https://pic4.zhimg.com/80/v2-d9cffa2dff74ae3c3092eb2c31b5b21b_720w.jpg)</figure>

    为了激发我们的方法，我们首先对典型的自注意力的学习注意模式进行定性评估。“稀疏”的自注意力得分形成了长尾分布。即，一些点积对引起了极大的注意力分数，而其他对则可以忽略。然后，下一个问题是如何区分它们？

    **（1）Query Sparsity Measurement**

    根据等式（1），第i个query对所有keys的注意力定义为概率 ![[公式]](https://www.zhihu.com/equation?tex=p%28k_j%7Cq_i%29) ，由于上面所述，自注意力的概率分布形成了长尾分布，因此是远离均匀分布的。作者使用KL散度来衡量相关性。删除常数后，我们将第i个query的稀疏度定义为：

    <figure data-size="normal">![](https://pic4.zhimg.com/80/v2-68c2700d5ec587b82c62915fb0135fbb_720w.jpg)</figure>

    **（2）ProbSparse Self-attention**

    <figure data-size="normal">![](https://pic2.zhimg.com/80/v2-e878d19f63e48a9f92d03fd12b6585b5_720w.png)</figure>

    根据所提出的度量，只允许Q中前u个query参与attention计算。其中 ![[公式]](https://www.zhihu.com/equation?tex=%5Coverline%7BQ%7D) 是稀疏处理的矩阵，根据M排序只包含前u个queries， ![[公式]](https://www.zhihu.com/equation?tex=u%3Dc%C2%B7lnL_Q) 。针对Log-Sum-Exp (LSE)的复杂计算和潜在的数值问题，论文又进行了进一步改进：

    <figure data-size="normal">![](https://pic2.zhimg.com/80/v2-7ccbfaa32b6e4c5c3fb5775dff4ab5a5_720w.jpg)</figure>

    **2.编码器：允许在内存使用限制下处理更长的输入序列**

    <figure data-size="normal">![](https://pic3.zhimg.com/80/v2-27f2d48eb809ac37b59c80ddf76e01d6_720w.jpg)</figure>

    **Self-attention Distilling**

    作为ProbSparse自注意力机制的自然结果，编码器的特征图具有V值的冗余组合。我们使用蒸馏操作突出主要特征，并在下一层生成focus的自注意力特征图，急剧地修剪输入在时间上的维度。受空洞卷积的启发，我们从第j层到第( j + 1 )层的“蒸馏”过程如下

    <figure data-size="normal">![](https://pic4.zhimg.com/80/v2-8cebcb746554e32ca4762ae4f5469d2b_720w.png)</figure>

    其中![[公式]](https://www.zhihu.com/equation?tex=%5B%5Ccdot%5D_%7BAB%7D)包含Multi-Head ProbSparse self-attention以及重要的attention block的操作。为了增强distilling操作的鲁棒性，我们构建了halving replicas，并通过一次删除一层（如上图）来逐步减少自关注提取层的数量，从而使它们的输出维度对齐。因此，我们将所有堆栈的输出串联起来，并得到encoder的最终隐藏表示。

    **3.解码器：通过一个前向过程生成长序列输出**

    <figure data-size="normal">![](https://pic1.zhimg.com/80/v2-03ba0f2b93e5756396cb38ac474883b0_720w.jpg)</figure>

    论文使用如图（2）所示的标准的解码器结构，它由2个相同的多头注意力层的堆栈组成。但是，在长时间预测中，采用了**生成推理**来缓解速度瓶颈。我们向解码器提供以下向量：

    <figure data-size="normal">![](https://pic1.zhimg.com/80/v2-1fe6f1c1f89785f2939f75f43361773c_720w.png)</figure>

    从长序列中采样一个 ![[公式]](https://www.zhihu.com/equation?tex=L_%7Btoken%7D) 的输出序列之前的片段，与 ![[公式]](https://www.zhihu.com/equation?tex=X_0%5Et) 拼接，输入decoder
</article>