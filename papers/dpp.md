# DPP: Deep predictor for price movement from candlestick charts
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/

[Chih-Chieh Hung](https://www.ncbi.nlm.nih.gov/pubmed/?term=Hung%20CC%5BAuthor%5D&cauthor=true&cauthor_uid=34153042), Writing – original draft<sup>1,</sup><sup>\*</sup> and  [Ying-Ju Chen](https://www.ncbi.nlm.nih.gov/pubmed/?term=Chen%20YJ%5BAuthor%5D&cauthor=true&cauthor_uid=34153042), Writing – review & editing<sup>2</sup>

### Chih-Chieh Hung

<sup>1</sup>
Department of Management Information Systems, National Chung Hsing University, Taichung City, Taiwan, 

Find articles by [Chih-Chieh Hung](https://www.ncbi.nlm.nih.gov/pubmed/?term=Hung%20CC%5BAuthor%5D&cauthor=true&cauthor_uid=34153042)

### Ying-Ju Chen

<sup>2</sup>
Department of Mathematics, University of Dayton, Dayton, Ohio, United States of America, 

Find articles by [Ying-Ju Chen](https://www.ncbi.nlm.nih.gov/pubmed/?term=Chen%20YJ%5BAuthor%5D&cauthor=true&cauthor_uid=34153042)

J E. Trinidad Segovia, Editor<sup></sup>

[Author information](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#) [Article notes](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#) [Copyright and License information](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#) [Disclaimer](https://www.ncbi.nlm.nih.gov/pmc/about/disclaimer/)

<sup>1</sup>
Department of Management Information Systems, National Chung Hsing University, Taichung City, Taiwan, 

<sup>2</sup>
Department of Mathematics, University of Dayton, Dayton, Ohio, United States of America, 

University of Almeria, SPAIN, 

**Competing Interests:** The authors have declared that no competing interests exist.

\* E-mail: [wt.ude.uhcn@nihsollams](mailto:dev@null)

Received 2020 Aug 13; Accepted 2021 May 16.

[Copyright](https://www.ncbi.nlm.nih.gov/pmc/about/copyright/) © 2021 Hung, Chen

This is an open access article distributed under the terms of the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/), which permits unrestricted use, distribution, and reproduction in any medium, provided the original author and source are credited.

This article has been [cited by](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/citedby/) other articles in PMC.

## Associated Data

<dl data-count="3" class="box-data-suppmats whole_rhythm no_bottom_margin">
    <dt>[Supplementary Materials](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#)</dt>
    <dd id="data-suppmats" style="display: none;">
        **S1 Data:** TX dataset. This dataset are from the Taiwan Futures Exchange (TAIFEX). The interval of this dataset is from July 21th, 1998 to December 27th, 2016, i.e., 4,625 trading days.

        (CSV)

        [pone.0252404.s001.csv](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.s001.csv) (113M)

        GUID: 39340240-09E5-4777-9E7D-EADF7C498B35

        **Attachment:** Submitted filename: _Review of the Manuscript PONE-D-20-24642.pdf_

        [pone.0252404.s002.pdf](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.s002.pdf) (358K)

        GUID: 43886185-CAF8-46D6-8C99-3CAC216409C1

        **Attachment:** Submitted filename: _response letter.pdf_

        [pone.0252404.s003.pdf](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.s003.pdf) (2.4M)

        GUID: FE6B91BB-EAC0-455F-AAC1-AE72EF33E37D
    </dd>
</dl>

<dl data-length="76" class="box-data-avail whole_rhythm no_bottom_margin">
    <dt>[Data Availability Statement](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#)</dt>
    <dd id="data-avl-stmnt" style="display: none;">
        All relevant data are within the paper and its [Supporting information](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#sec020) files.
    </dd>
</dl>

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## Abstract

<!--article-meta-->

Forecasting the stock market prices is complicated and challenging since the price movement is affected by many factors such as releasing market news about earnings and profits, international and domestic economic situation, political events, monetary policy, major abrupt affairs, etc. In this work, a novel framework: deep predictor for price movement (DPP) using candlestick charts in the stock historical data is proposed. This framework comprises three steps: 1. decomposing a given candlestick chart into sub-charts; 2. using CNN-autoencoder to acquire the best representation of sub-charts; 3. applying RNN to predict the price movements from a collection of sub-chart representations. An extensive study is operated to assess the performance of the DPP based models using the trading data of Taiwan Stock Exchange Capitalization Weighted Stock Index and a stock market index, Nikkei 225, for the Tokyo Stock Exchange. Three baseline models based on IEM, Prophet, and LSTM approaches are compared with the DPP based models.

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## Introduction

The stock market performance is one important indicator for the world economy. It provides an overall insight about the performance of all listed companies in a country. Stock market price forecasting has been grabbing a great amount of attention since the introduction of the first publicly shareholder company: The Dutch East India Company in the 17th century [[1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref001)] due to 1. it allows investors to maximize the profit in the stock market; 2. it helps large-scale enterprises to acquire small businesses or merge with another corporation at a good time point; 3. it aids investors, banks, and insurance companies to avoid potential risks on large fluctuation of stock prices.

However, such forecasting problem is complicated and challenging since the price movement is affected by many factors such as releasing market news about earnings and profits, international and domestic economic situation, political events, monetary policy, major abrupt affairs, etc. There are two main branches of study in the literature: Fundamental Analysis and Technical Analysis. Though the major purposes of these two methods are the same, the focuses of analytical tools are quiet different. The former focuses on both past and present data corresponding to economic reports, market news, and industry statistics, while the latter looks at statistical trends such as price movements from past data with chart analysis [[2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref002)]. In this article, we propose a deep learning framework applied in candlestick pattern analysis which is one of the popular tools of chart analysis in assistance of forecasting stock market price [[3](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref003)–[6](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref006)].

_Candlestick charts_ have been the most popular visualized tools that summarize daily price, currency movements, volumes, or values of technical indices. [Fig 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g001/) shows an example of a 20-day candlestick chart and [Fig 2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g002/) shows the essential components of candlesticks.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g001/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g001/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g001.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g001.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g001.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g001/?report=objectonly)

[Fig 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g001/)

<!--caption a7-->

<!--caption a8-->**A 20-day candlestick chart.**

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->

![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g002.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g002.jpg "An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g002.jpg")](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g002/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g002/)[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g002/?report=objectonly)

[Fig 2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g002/)

<!--caption a7-->

<!--caption a8-->**The basics of candlesticks.**

A candlestick chart consists of sticks for a specific period of time and each stick displays the range between opening and closing traded prices (body) and the highest and lowest traded prices for one day trading data. In addition, one should note that the use of colors for candlestick charts could be different depending on countries. Due to the simple structure of candlestick charts, they are straightforward and easy to read. It is easy to recognize visual trends from candlestick charts and use the corresponding information collected to help predict price movements. Although the literature has shown that candlestick pattern analysis is a successful approach in financial forecasting [[7](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref007)–[10](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref010)], predicting the price movements by reading the visual trends from candlestick charts is still challenging. One can argue that nuances are lost in the candlestick charts while candlestick charts simplifies complex analysis behind the scene. In fact, each stick reflects the difference between any two values among open, closing, highest and lowest traded prices and including candlesticks side-by-side would show the deviation between daily traded prices during the period of time. While the trading volume is not included in a candlestick chart, there is no clear evidence in the literature supporting that the trading volume improves the performance of forecasting stock price movements [[11](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref011)–[13](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref013)]. Zhu et al. [[13](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref013)] mentioned that including the information of total market trading volume does not contribute to the improvement of network forecasting since it may also contain any unnecessary or inter-correlated information.

When using candlestick charts to forecast the price movements, there are some challenges that need to be solved. The first challenge comes from the inclusive of the non-informative blank space in a candlestick chart as the focus should be the informative part of it, i.e., the candlesticks. Thus, the development of a refined pre-processing approach to read candlestick pattern is essential. The second challenge comes from the extraction of representative characteristics from sub-charts since individuals prefer to identify local trends at first glance instead of finding the global pattern. The third challenge is about learning the meta-patterns and series of local patterns in candlestick charts since they usually bring more attentions to humans when studying the price movements. Instead of reading the pre-decided patterns visually, the major contribution of this article is development of a predictive model to find features that are highly associated to the price movements using candlestick charts.

A deep learning framework DPP (_Deep Predictor for Price_ Movement) is introduced in this article to predict the price movement of a given day, say (_k_ + 1)-th day, by taking a _k_-day candlestick chart as an input. Latane et al. [[14](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref014)] defined the price movement by comparing the price of the (_k_ + 1)-day and the price trend of the past _k_-days. Specifically, the price movement is defined to be upward if the price of the (_k_ + 1)-th day is larger than _μ_<sub>_k_</sub> + _ασ_<sub>_k_</sub> where the _μ_<sub>_k_</sub> and _σ_<sub>_k_</sub> refer to the mean and standard variation of the price in the past _k_ days and _α_ is a user-specified parameter; otherwise, the price movement is defined to be downward [[14](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref014)]. For example, given [Fig 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g001/) which _k_ is set to be 20, the 20-day candlestick chart, DPP can be used to study the price movement of the 21st day is upward or downward.

The design of DPP is illustrated in [Fig 3](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g003/). It consists of a chart decomposer, a CNN-Autoencoder (abbreviated as CAE) and an RNN with GRU gating mechanism (abbreviated as GRU). CNN stands for Convolution Neural Network, RNN stands for Recurrent Neural Network, and GRU stands for Gated Recurrent Unit. The concept of DPP is to decompose the candlestick chart into sub-charts, extract the graphical features from these sub-charts, and predict the price movement by the time-series of these sub-charts. In the initial step, the chart decomposer splits a given _k_-day candlestick chart into multiple _m_-day sub-charts. The first challenge could be addressed by standardizing the sizes of the bodies and the shadows of candles for all _m_-day sub-charts. Then these sub-charts are adopted to train a _CNN-Autoencoder_ in the second step which can extract deep features from sub-charts. The second challenge is solved since the features extracted could be the best representative of the sub-charts. In the final step, _RNN with GRU gating mechanism_ is used to predict the (_k_ + 1)-th day price movement from the sequences of these deep features. Thus, the third challenge is clear up because the relationship between the price movement and the series of the deep features could be learned by RNN.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g003/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g003/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g003.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g003.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g003.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g003/?report=objectonly)

[Fig 3](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g003/)

<!--caption a7-->

<!--caption a8-->**Overview of the proposed framework.**

In order to assess the performance of DPP based models, two datasets are adopted, the trading data of Taiwan Stock Exchange Capitalization Weighted Stock Index and Nikkei 225 which is a stock market index for the Tokyo Stock Exchange, and three baseline approaches, IEM, Prophet, and LSTM, are considered. The result suggests that the overall performance of DPP approach is better than it of baseline approaches.

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## Related work

We will discuss some related work in the literature corresponding to time series forecasting of candlestick charts developed on the deep-learning approaches.

### Deep learning approaches for time series forecasting

Forecasting problems in time series have been studied in the field of Machine learning which has brought lots of attention in recent decade. Recurrent Neural Networks (RNN), a variant of neural network, is one of the popular models for solving such types of questions. Besides the flexibility in dealing with varying lengths of sequences, RNN also provides advantage of memorizing the features learned in different positions of sequences as its recursive architecture [[15](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref015), [16](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref016)]. These features make RNN heavily-used in time series forecasting tasks, such as natural language processing.

According to the number of inputs and outputs, RNN could be classified into four categories: one-to-one RNN, one-to-many RNN, many-to-one RNN, and many-to-many RNN. For example, many-to-one RNN accepts several inputs and gives one output. Since the problem addressed in this paper is to use many candlestick charts to predict the price movement in the (_k_ + 1)-th day, many-to-one RNN is adopted. Apart from the power of RNN, one of the main issues in training RNN is the gradient vanishing [[17](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref017)]. Gradient vanishing refers to the problem that the gradient components of the loss function approach zero which makes the network hard to train. This weakness makes RNN unable to capture long term dependencies in sequences. To overcome this issue, a modification of RNN architecture is needed, such as Long Short-Term Memory (LSTM) [[18](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref018)] and GRU (Gated Recurrent Unit) [[19](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref019)]. LSTM has three gates in each memory cell in RNN: an update gate, an input gate and an output gate. As each gate contains a sigmoid activation functions and pointwise multiplication operation, LSTM can add or remove information to the memory cell. GRU is similar to LSTM but it has two additional gates, update gate and reset gate, and an extra activation function (hyperbolic tangent, tanh) in each memory cell. Different from LSTM, GRU passes the memory content that is seen or used by other units to the next memory cell directly instead of being controlled by gates. Compared to LSTM, GRU takes less training time and needs fewer training data since GRU requires fewer parameters when GRU could achieve a similar performance according to previous empirical tests [[20](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref020)]. Therefore, GRU is selected to predict the price movement in our study.

### Analysis of candlestick charts

There have been lots of studies in forecasting the price tendency through candlestick charts. The candlestick-chart-formed data and pre-defined patterns are adopted to assess the performance of hybrid stock market forecasting models in Takenori Kamo et al. [[21](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref021)]. Karsten Martiny [[22](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref022)] introduced the tree-based pattern-search method in aims of discovering essential candlestick patterns and further predicting future price movements.

The original study that attempts to mimic how human traders make trading decisions through reading numerical candlestick-chart-formed data is from [[23](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref023), [24](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref024)], which conducted hybrid machine learning models to study timing of the stock markets. Reading candlestick charts allows traders to understand impacts of trends called _visual features rather than reading numerical raw data directly_. Some recent investigations manifest that analyzing visual characteristics of candlestick charts to predict stock market is still a hot topic, for examples, Hu et al. [[8](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref008)] summarize the historical financial data as images using candlestick charts and adopt the convolutional autoencoder for feature learning from the image data, Fengqian and Chao [[25](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref025)] apply K-line theory to characterize candlesticks as a generalization of price movements over a time period and then propose the deep reinforcement learning based system to reach adaptive control in the unknown environment, and Ananthi and Vijayakumar [[26](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref026)] proposed a system that generates signals on the candlesticks to predict market price movement by using regression and candlestick pattern detection. Furthermore, a novel variation of conventional candlesticks, RGBSticks, is introduced in [[27](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref027)] to predict the daily stock price of a company by using an autoencoder based on deep neural network.

Although the approaches above appear to be comparable to our work in this paper, one single settled time interval would not be considered by traders and long time period candlestick charts will be divided into several sub-charts for analysis.

This study is an extended version of our previous work [[28](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref028), [29](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref029)]. To our best knowledge, our previous work is the first study that uses _k_-day candlestick charts to predict the price movement which is defined as the difference of the close prices of _k_-th day and the (_k_ + 1)-th day [[28](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref028), [29](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref029)]. In this extended version, some improvements are made which can distinguish this paper from our previous study. First of all, we develop a chart-decomposer to crop sub-charts from a _k_-day candlestick chart, rather than using raw data to generate sub-charts, which is consistent with the scene of this paper: reading the candlestick to predict price movement. Secondly, the definition of price movement in this paper takes the mean and variance of prices of _k_-day history into account, rather than simply uses the difference of prices of the _k_-th day and the (_k_ + 1)-day, which can better represent the trend of the price movement. Thirdly, the predictor of the price movement is based on GRU, rather than 1D-CNN, which is more intuitive and brings higher accuracy in nested cross-validation. At last, nested cross-validation, rather than simply k-fold cross-validation, is used to validate models in the experiments in this paper, which could better capture the nature of temporal dependency in time-series data and reflect more reliable experimental results. In brief, we believe this extended version has made significant contributions compared to previous work.

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## Deep predictor for price movement (DPP)

In this section, the proposed framework DPP is introduced with the detailed procedures in each stage.

The target of prediction in this paper is the price movement. Let _C_<sub>_d_</sub> be the close price of _d_-th day and _d_ ≥ _k_ + 1, the price movement of the _d_-th day is defined as follows:

<nobr><span class="math" id="M1" overflow="scroll" style="width: 18.873em; display: inline-block;"><span style="display: inline-block; position: relative; width: 15.19em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(-0.603em, 1015.17em, 2.122em, -999.981em); top: -1.007em; left: 0em;"><span class="mrow" id="MathJax-Span-2"><span class="mtable" id="MathJax-Span-3"><span style="display: inline-block; position: relative; width: 14.887em; height: 0px; margin-right: 0.154em; margin-left: 0.154em;"><span style="position: absolute; clip: rect(2.374em, 1014.87em, 5.099em, -999.981em); top: -3.983em; left: 0em;"><span style="display: inline-block; position: relative; width: 14.887em; height: 0px;"><span style="position: absolute; clip: rect(2.374em, 1014.87em, 5.099em, -999.981em); top: -3.983em; right: 0em;"><span class="mtd" id="MathJax-Span-4"><span class="mrow" id="MathJax-Span-5"><span class="mrow" id="MathJax-Span-6"><span class="mi" id="MathJax-Span-7" style="font-family: MathJax_Math-italic;">t</span><span class="mi" id="MathJax-Span-8" style="font-family: MathJax_Math-italic;">a</span><span class="mi" id="MathJax-Span-9" style="font-family: MathJax_Math-italic;">r</span><span class="mi" id="MathJax-Span-10" style="font-family: MathJax_Math-italic;">g<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mi" id="MathJax-Span-11" style="font-family: MathJax_Math-italic;">e</span><span class="mi" id="MathJax-Span-12" style="font-family: MathJax_Math-italic;">t</span><span class="mrow" id="MathJax-Span-13" style="padding-left: 0.154em;"><span class="mo" id="MathJax-Span-14" style="font-family: MathJax_Main;">(</span><span class="mi" id="MathJax-Span-15" style="font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-16" style="font-family: MathJax_Main;">)</span></span><span class="mo" id="MathJax-Span-17" style="font-family: MathJax_Main; padding-left: 0.305em;">=</span><span class="mo" id="MathJax-Span-18" style="vertical-align: 0em; padding-left: 0.305em;"><span style="font-family: MathJax_Size3;">{</span></span><span class="mtable" id="MathJax-Span-19"><span style="display: inline-block; position: relative; width: 8.328em; height: 0px; margin-right: 0.154em; margin-left: 0.154em;"><span style="position: absolute; clip: rect(2.475em, 1000.69em, 5.099em, -999.981em); top: -3.983em; left: 0em;"><span style="display: inline-block; position: relative; width: 0.759em; height: 0px;"><span style="position: absolute; clip: rect(3.181em, 1000.69em, 4.342em, -999.981em); top: -4.639em; left: 0em;"><span class="mtd" id="MathJax-Span-20"><span class="mrow" id="MathJax-Span-21"><span class="mrow" id="MathJax-Span-22"><span class="mn" id="MathJax-Span-23" style="font-family: MathJax_Main;">1</span><span class="mo" id="MathJax-Span-24" style="font-family: MathJax_Main;">,</span></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span><span style="position: absolute; clip: rect(3.181em, 1000.69em, 4.342em, -999.981em); top: -3.227em; left: 0em;"><span class="mtd" id="MathJax-Span-37"><span class="mrow" id="MathJax-Span-38"><span class="mrow" id="MathJax-Span-39"><span class="mn" id="MathJax-Span-40" style="font-family: MathJax_Main;">0</span><span class="mo" id="MathJax-Span-41" style="font-family: MathJax_Main;">,</span></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span><span style="position: absolute; clip: rect(2.475em, 1006.75em, 4.947em, -999.981em); top: -3.983em; left: 1.567em;"><span style="display: inline-block; position: relative; width: 6.713em; height: 0px;"><span style="position: absolute; clip: rect(3.131em, 1006.75em, 4.342em, -999.981em); top: -4.639em; left: 0em;"><span class="mtd" id="MathJax-Span-25"><span class="mrow" id="MathJax-Span-26"><span class="mrow" id="MathJax-Span-27"><span class="msub" id="MathJax-Span-28"><span style="display: inline-block; position: relative; width: 1.163em; height: 0px;"><span style="position: absolute; clip: rect(3.131em, 1000.74em, 4.14em, -999.981em); top: -3.983em; left: 0em;"><span class="mi" id="MathJax-Span-29" style="font-family: MathJax_Math-italic;">C<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span><span style="position: absolute; top: -3.832em; left: 0.709em;"><span class="mi" id="MathJax-Span-30" style="font-size: 70.7%; font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span></span></span><span class="mo" id="MathJax-Span-31" style="font-family: MathJax_Main; padding-left: 0.305em;">&gt;</span><span class="mi" id="MathJax-Span-32" style="font-family: MathJax_Math-italic; padding-left: 0.305em;">μ</span><span class="mo" id="MathJax-Span-33" style="font-family: MathJax_Main; padding-left: 0.204em;">+</span><span class="mi" id="MathJax-Span-34" style="font-family: MathJax_Math-italic; padding-left: 0.204em;">α</span><span class="mo" id="MathJax-Span-35" style="font-family: MathJax_Main; padding-left: 0.204em;">×</span><span class="mi" id="MathJax-Span-36" style="font-family: MathJax_Math-italic; padding-left: 0.204em;">σ<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span><span style="position: absolute; clip: rect(3.131em, 1004.33em, 4.14em, -999.981em); top: -3.227em; left: 0em;"><span class="mtd" id="MathJax-Span-42"><span class="mrow" id="MathJax-Span-43"><span class="mrow" id="MathJax-Span-44"><span class="mi" id="MathJax-Span-45" style="font-family: MathJax_Math-italic;">o</span><span class="mi" id="MathJax-Span-46" style="font-family: MathJax_Math-italic;">t</span><span class="mi" id="MathJax-Span-47" style="font-family: MathJax_Math-italic;">h</span><span class="mi" id="MathJax-Span-48" style="font-family: MathJax_Math-italic;">e</span><span class="mi" id="MathJax-Span-49" style="font-family: MathJax_Math-italic;">r</span><span class="mi" id="MathJax-Span-50" style="font-family: MathJax_Math-italic;">w</span><span class="mi" id="MathJax-Span-51" style="font-family: MathJax_Math-italic;">i</span><span class="mi" id="MathJax-Span-52" style="font-family: MathJax_Math-italic;">s</span><span class="mi" id="MathJax-Span-53" style="font-family: MathJax_Math-italic;">e</span></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span></span></span><span class="mo" id="MathJax-Span-54"></span></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.989em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 1.012em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -1.248em; border-left: 0px solid; width: 0px; height: 3.131em;"></span></span></nobr>

(1)

where <nobr><span class="math" id="M2" overflow="scroll" style="width: 6.807em; display: inline-block;"><span style="display: inline-block; position: relative; width: 5.496em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(0.708em, 1005.5em, 2.724em, -999.997em); top: -2.165em; left: 0em;"><span class="mrow" id="MathJax-Span-56"><span class="mrow" id="MathJax-Span-57"><span class="mi" id="MathJax-Span-58" style="font-family: MathJax_Math-italic;">μ</span><span class="mo" id="MathJax-Span-59" style="font-family: MathJax_Main; padding-left: 0.305em;">=</span><span class="mfrac" id="MathJax-Span-60" style="padding-left: 0.305em;"><span style="display: inline-block; position: relative; width: 3.279em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.128em, 1003.18em, 4.388em, -999.997em); top: -4.635em; left: 50%; margin-left: -1.56em;"><span class="mrow" id="MathJax-Span-61"><span class="msubsup" id="MathJax-Span-62"><span style="display: inline-block; position: relative; width: 2.271em; height: 0px;"><span style="position: absolute; clip: rect(3.279em, 1000.71em, 4.337em, -999.997em); top: -3.979em; left: 0em;"><span class="mo" id="MathJax-Span-63" style="font-size: 70.7%; font-family: MathJax_Size1; vertical-align: 0em;">∑</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.48em, 1000.96em, 4.186em, -999.997em); top: -4.332em; left: 0.759em;"><span class="mrow" id="MathJax-Span-64"><span class="mi" id="MathJax-Span-65" style="font-size: 50%; font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-66" style="font-size: 50%; font-family: MathJax_Main;">−</span><span class="mn" id="MathJax-Span-67" style="font-size: 50%; font-family: MathJax_Main;">1</span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.48em, 1001.51em, 4.186em, -999.997em); top: -3.778em; left: 0.759em;"><span class="mrow" id="MathJax-Span-68"><span class="mi" id="MathJax-Span-69" style="font-size: 50%; font-family: MathJax_Math-italic;">t</span><span class="mo" id="MathJax-Span-70" style="font-size: 50%; font-family: MathJax_Main;">=</span><span class="mi" id="MathJax-Span-71" style="font-size: 50%; font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-72" style="font-size: 50%; font-family: MathJax_Main;">−</span><span class="mi" id="MathJax-Span-73" style="font-size: 50%; font-family: MathJax_Math-italic;">k</span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span></span></span><span class="msub" id="MathJax-Span-74" style="padding-left: 0.154em;"><span style="display: inline-block; position: relative; width: 0.759em; height: 0px;"><span style="position: absolute; clip: rect(3.329em, 1000.56em, 4.136em, -999.997em); top: -3.979em; left: 0em;"><span class="mi" id="MathJax-Span-75" style="font-size: 70.7%; font-family: MathJax_Math-italic;">C<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; top: -3.879em; left: 0.507em;"><span class="mi" id="MathJax-Span-76" style="font-size: 50%; font-family: MathJax_Math-italic;">t</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.329em, 1000.36em, 4.136em, -999.997em); top: -3.576em; left: 50%; margin-left: -0.199em;"><span class="mi" id="MathJax-Span-77" style="font-size: 70.7%; font-family: MathJax_Math-italic;">k</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1003.28em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 3.279em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.17em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.559em; border-left: 0px solid; width: 0px; height: 2.253em;"></span></span></nobr>, <nobr><span class="math" id="M3" overflow="scroll" style="width: 10.335em; display: inline-block;"><span style="display: inline-block; position: relative; width: 8.319em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(0.355em, 1008.32em, 3.077em, -999.997em); top: -2.165em; left: 0em;"><span class="mrow" id="MathJax-Span-79"><span class="mrow" id="MathJax-Span-80"><span class="mi" id="MathJax-Span-81" style="font-family: MathJax_Math-italic;">σ<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-82" style="font-family: MathJax_Main; padding-left: 0.305em;">=</span><span class="msqrt" id="MathJax-Span-83" style="padding-left: 0.305em;"><span style="display: inline-block; position: relative; width: 6.353em; height: 0px;"><span style="position: absolute; clip: rect(2.523em, 1005.35em, 4.589em, -999.997em); top: -3.979em; left: 1.011em;"><span class="mrow" id="MathJax-Span-84"><span class="mfrac" id="MathJax-Span-85"><span style="display: inline-block; position: relative; width: 5.144em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.128em, 1004.99em, 4.388em, -999.997em); top: -4.635em; left: 50%; margin-left: -2.518em;"><span class="mrow" id="MathJax-Span-86"><span class="msubsup" id="MathJax-Span-87"><span style="display: inline-block; position: relative; width: 2.271em; height: 0px;"><span style="position: absolute; clip: rect(3.279em, 1000.71em, 4.337em, -999.997em); top: -3.979em; left: 0em;"><span class="mo" id="MathJax-Span-88" style="font-size: 70.7%; font-family: MathJax_Size1; vertical-align: 0em;">∑</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.48em, 1000.96em, 4.186em, -999.997em); top: -4.332em; left: 0.759em;"><span class="mrow" id="MathJax-Span-89"><span class="mi" id="MathJax-Span-90" style="font-size: 50%; font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-91" style="font-size: 50%; font-family: MathJax_Main;">−</span><span class="mn" id="MathJax-Span-92" style="font-size: 50%; font-family: MathJax_Main;">1</span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.48em, 1001.51em, 4.186em, -999.997em); top: -3.778em; left: 0.759em;"><span class="mrow" id="MathJax-Span-93"><span class="mi" id="MathJax-Span-94" style="font-size: 50%; font-family: MathJax_Math-italic;">t</span><span class="mo" id="MathJax-Span-95" style="font-size: 50%; font-family: MathJax_Main;">=</span><span class="mi" id="MathJax-Span-96" style="font-size: 50%; font-family: MathJax_Math-italic;">d<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.003em;"></span></span><span class="mo" id="MathJax-Span-97" style="font-size: 50%; font-family: MathJax_Main;">−</span><span class="mi" id="MathJax-Span-98" style="font-size: 50%; font-family: MathJax_Math-italic;">k</span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span></span></span><span class="msup" id="MathJax-Span-99" style="padding-left: 0.154em;"><span style="display: inline-block; position: relative; width: 2.573em; height: 0px;"><span style="position: absolute; clip: rect(3.279em, 1002.22em, 4.337em, -999.997em); top: -3.979em; left: 0em;"><span class="mrow" id="MathJax-Span-100"><span class="mo" id="MathJax-Span-101" style="font-size: 70.7%; font-family: MathJax_Main;">(</span><span class="msub" id="MathJax-Span-102"><span style="display: inline-block; position: relative; width: 0.759em; height: 0px;"><span style="position: absolute; clip: rect(3.329em, 1000.56em, 4.136em, -999.997em); top: -3.979em; left: 0em;"><span class="mi" id="MathJax-Span-103" style="font-size: 70.7%; font-family: MathJax_Math-italic;">C<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; top: -3.879em; left: 0.507em;"><span class="mi" id="MathJax-Span-104" style="font-size: 50%; font-family: MathJax_Math-italic;">t</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span></span></span><span class="mo" id="MathJax-Span-105" style="font-size: 70.7%; font-family: MathJax_Main;">−</span><span class="mi" id="MathJax-Span-106" style="font-size: 70.7%; font-family: MathJax_Math-italic;">μ</span><span class="mo" id="MathJax-Span-107" style="font-size: 70.7%; font-family: MathJax_Main;">)</span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; top: -4.332em; left: 2.271em;"><span class="mn" id="MathJax-Span-108" style="font-size: 50%; font-family: MathJax_Main;">2</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.329em, 1001.21em, 4.186em, -999.997em); top: -3.576em; left: 50%; margin-left: -0.653em;"><span class="mrow" id="MathJax-Span-109"><span class="mi" id="MathJax-Span-110" style="font-size: 70.7%; font-family: MathJax_Math-italic;">k</span><span class="mo" id="MathJax-Span-111" style="font-size: 70.7%; font-family: MathJax_Main;">−</span><span class="mn" id="MathJax-Span-112" style="font-size: 70.7%; font-family: MathJax_Main;">1</span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1005.14em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 5.144em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.581em, 1005.29em, 3.884em, -999.997em); top: -5.34em; left: 1.011em;"><span style="display: inline-block; position: relative; width: 5.295em; height: 0px;"><span style="position: absolute; font-family: MathJax_Main; top: -3.979em; left: -0.098em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; font-family: MathJax_Main; top: -3.979em; left: 4.589em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 0.406em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 0.96em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 1.515em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 2.019em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 2.573em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 3.077em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 3.632em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="font-family: MathJax_Main; position: absolute; top: -3.979em; left: 4.186em;">−<span style="display: inline-block; width: 0px; height: 3.984em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(2.371em, 1001.01em, 5.093em, -999.997em); top: -4.181em; left: 0em;"><span style="font-family: MathJax_Size3;">√</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.17em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.997em; border-left: 0px solid; width: 0px; height: 3.128em;"></span></span></nobr>, and 0 and 1 represent downward and upward of price movement, respectively. If the close price of _d_-th day is greater than _α_ standard deviations above the mean of past _k_ days’ close prices, then the price movement is defined as upward. Otherwise, the price movement would be downward.

Note that the price movement here borrows the concept of Bollinger Bands [[30](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref030)] which is a widely-used technical analysis tool to give a relative definition of high and low prices of a market, allowing traders to vary the response of the chart to the magnitude and frequency of price changes. Bollinger Bands consists of an _d_-period moving average (same as _μ_ here), an upper and lower band at _α_ times an _d_-period standard deviation (same as _σ_ here) above and below the moving average, respectively. To model the price prediction into a binary classification problem, our definition of the price movement can be viewed as a simplified Bollinger Bands.

In this paper, the default value of _k_ is set to be 20 and that of _α_ is set to be 1. The goal of this work is to maximize the accuracy of the predicted price movement over the actual price movement.

### Chart decomposer

In the first state, we decompose a given _k_-day candlestick chart into several _m_-day sub-charts. The specification of a sub-chart needs to be settled carefully since these sub-charts will be utilized to extricate features within the afterward stages.

The development of sub-charts in this paper takes after two standards: 1. produced sub-charts must comprise _m_ sticks and the corresponding shadow and body of the sticks are required to be plainly visible and 2. the dimension of produced sub-charts need to be as little as possible in aim of reducing the area of non-informative blank space. In this study, we expect to have high-quality candlestick charts and they are well-formed with consistent width. To decompose a given candlestick chart into sub-charts, the unnecessary part of the candlestick chart is firstly cropped by deriving a minimum bounding rectangle (MBR) of non-white pixels which have the height ℓ and the width _w_. Suppose that the candlestick chart is well-formatted. We can divide the derived MBR into 20 rectangles with height ℓ and width <nobr><span class="math" id="M4" overflow="scroll" style="width: 1.263em; display: inline-block;"><span style="display: inline-block; position: relative; width: 1.011em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(0.154em, 1001.01em, 1.565em, -999.997em); top: -1.006em; left: 0em;"><span class="mrow" id="MathJax-Span-114"><span class="mfrac" id="MathJax-Span-115"><span style="display: inline-block; position: relative; width: 0.809em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.531em, 1000.51em, 4.136em, -999.997em); top: -4.383em; left: 50%; margin-left: -0.249em;"><span class="mi" id="MathJax-Span-116" style="font-size: 70.7%; font-family: MathJax_Math-italic;">w</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.38em, 1000.66em, 4.136em, -999.997em); top: -3.627em; left: 50%; margin-left: -0.35em;"><span class="mn" id="MathJax-Span-117" style="font-size: 70.7%; font-family: MathJax_Main;">20</span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1000.81em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 0.809em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 1.011em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.559em; border-left: 0px solid; width: 0px; height: 1.503em;"></span></span></nobr>. Then, we scan the image of each rectangle line by line to identify the candlestick. Finally, given any consecutive _m_ candlesticks, we can generate an image with specific length and width.

It requires in general at least 3 candlesticks to identify patterns such that three line strikes and three black crows. Thus, we use 3-day sub-charts in our study and set _m_ to be 3 as the default value. [Fig 4](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g004/) gives an example of a 3-day sub-chart. In this paper, a 3-day sub-chart is a squared, grey-scaled image with the length 48 pixels where a while-colored stick means the price rises, a grey-colored stick means the price falls, and the background is black. For each stick, the width of shadow is 1 pixel and the width of body is 10 pixels.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g004/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g004/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g004.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g004.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g004.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g004/?report=objectonly)

[Fig 4](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g004/)

<!--caption a7-->

<!--caption a8-->**An illustrative example of a 3-day sub-chart.**

### CNN-autoencoder

We use a CNN-autoencoder (CAE) to extract the deep features from these sub-charts after acquiring a few _m_-day sub-charts in the first stage. CAE contains two parts: encoder and decoder which learn a representation from the data. For the encoding procedure, each sub-chart is converted to a deep feature using several convolutions and pooling layers in CNN. Then in the decoding procedure the sub-charts are reconstructed by striding transposed convolutions. The encoding and decoding procedures of CAE aim to obtain the best representation of the input-charts by recovering these sub-charts from the output images obtained from deep features.

The structure and corresponding parameters of the CAE in the study are illustrated in [Fig 5](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g005/). First, the input dimension of CAE is 48 × 48 × 1 because of the use of a 48 pixels gray-scaled image of 3-day sub-chart. Second, there are 3 components in the encoding process: a 2D convolution layer (Conv-2D), a 2D max pooling layer (MaxPooling-2D) with ReLu as its activation function, and the parameters of each convolution layer are appeared in its bottom. Third, as the network becomes deeper, the number of channels for the conventional CNN increases and its dimension of intermediate images diminishes. Fourth, the deep feature could be achieved to have the dimension of 3 × 3 × 64 via the average pooling in the 8th layer. The decoding process is proposed to be the reverse of the encoding process. Finally, the dimension of the decoder is 48 × 48 × 1. Here, we note that the loss function of the CAE selected is Binary Cross Entropy which is used to assess the difference between the original 3-day sub-charts (input) and the output images. Besides, the additional manual checking for the output images is required as the high likeness between the original sub-charts and the output images is not always guaranteed through minimizing the loss function. Besides, the additional manual checking for the output images is required as the high likeness between the original sub-charts and the output images is not promised through minimizing the loss function.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g005/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g005/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g005.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g005.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g005.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g005/?report=objectonly)

[Fig 5](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g005/)

<!--caption a7-->

<!--caption a8-->**CNN-autoencoder.**

### RNN with GRU gating mechanism

In the third stage of the proposed framework, GRU is used to predict the price movement after transforming sub-charts into deep feature vectors. To achieve this goal, given a _k_-day candlestick chart, there would be _k_ − _m_ + 1 deep feature vectors obtained by transforming _k_ − _m_ + 1 sub-charts through CAE. Since these sub-charts are time-ordered, a sequence of the corresponding _k_ − _m_ + 1 deep feature vectors is taken as the input of the GRU and the output of the GRU is the predicted price movement (up/down).

As one of the famous deep learning mechanism for time-series classification problems, RNN faces the gradient vanishing problem so that it usually can not achieve satisfiable performance especially when the input is a long sequence. Many gating mechanisms are invented to overcome the gradient vanishing problem. The GRU, as the state-of-art gating mechanism, is like a long short-term memory (LSTM) with a forget gate but has fewer parameters than LSTM [[19](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref019)] has. Since GRU is reported to be able to achieve a similar performance but has better training efficiency compared to LSTM, GRU is selected to forecast the price movement in this paper.

[Fig 6](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g006/) displays the implementation of GRU in this paper where the red-colored values are the possible values for hyper-parameters. For the demonstration purpose, _k_ is chosen to be 20 and _m_ is chosen to be 3. A 20-day candlestick chart is transformed into 18 deep feature vectors by CAE such that the size of each deep feature vector is 3 × 3 × 64 = 576 pixels. The RNN is composed of 1-layer GRU which takes 18 sequential deep features from CAE and then outputs a deep feature vector, and a fully connected layer is followed to classify the price movement of the 21st day. Here, the fully connected layer is composed of one input layer whose size is the same as the number of hidden features in GRU, and one output layer whose size is 1 neuron. The dropout and weight normalization in fully-connected layer are also used to prevent the fully-connected-layered classifier from overfitting problem [[31](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref031), [32](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref032)]. The final output is a binary value, telling up or down. Note that there are several hyper-parameters to be tuned by cross validation. The performance of different settings for hyper-parameters used here will be discussed in latter section.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g006/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g006/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g006.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g006.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g006.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g006/?report=objectonly)

[Fig 6](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g006/)

<!--caption a7-->

<!--caption a8-->**RNN with GRU gating mechanism.**

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## Experiment results

In this section, the performance of the proposed method DPP will be assessed in comparison with three baseline methods. The setting of the experiments, the preparation of data, the assessment of model performance as well as the sensitivity analysis for hyper parameters in DPP will be covered.

### Settings and datasets

#### Baselines 

We will compare the proposed approach DPP with the three baselines _IEM_,_Prophet_, and _LSTM_. The overview of the baseline models is provided as follows:

<!--
list-behavior=unordered
prefix-word=
mark-type=disc
max-label-size=0
-->
* IEM [[33](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref033)] is an index-based approach by taking 10 traditional indices into account, which are simple moving average (SMA), weighted moving average, momentum, stochastic K, stochastic D, RSI, MACD, Lary William’s R, A/D(Accumulation/Distribution) Oscillator, and CCI. Given a historical trading data set, IEM firstly uses 10 indices to determine the price movement, according to human-specified thresholds set by domain experts, and then it trains 1 classifier to ensemble the results from 10 decisions to generate the prediction of the price movement. In the following experiment, the classifier in IEM model is chosen to be Support Vector Machine (SVM) as it achieves the highest accuracy in nested cross-validation based on the data sets selected.

* Prophet [[34](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref034)] is an additive model to predict time-series data. Specifically, a time series model can be decomposed into three additive components: _y_(_t_) = _g_(_t_) + _s_(_t_) + _h_(_t_) + _ϵ_ where _y_(_t_) is the value of a time series at time t, _g_(_t_) is a trend function that models non-periodic changes, _s_(_t_) is a seasonality function that models the periodic changes, _h_(_t_) is the function which reflects the effect of holiday, and _ϵ_ is the error. In this experiment, we use the open-sourced implementation of Prophet model [[34](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref034)] by setting _y_(_t_) as the close price on day _t_, _g_(_t_) as the piecewise logistic growth model, _s_(_t_) as Fourier series, and _h_(_t_) as the normal distribution with zero mean.

* LSTM (Long Short Term Memory networks) [[35](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref035)] is a variant of recurrent neural networks that can learn long-term dependencies. Many existing studies for stock price prediction take LSTM as their baseline model. Following the suggestion in [[35](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref035)], in our study the model LSTM takes 10 features as inputs, including the raw data (Open, High, Low, Close prices, Volume), and indices (EMA12, EMA25, MACD, BollingerUp and Bollinger Down), to predict the close price of the next day. Then, we apply [Eq 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.e001) to generate the prediction target (i.e., upward and downward).

#### Datasets 

Two datasets are used to explore the performance of DPP based models and baseline models. The first dataset (TX dataset) is composed of four futures: TX (TAIEX Futures), MTX (Mini-TAIEX Futures), TE (Electronic Sector Index Futures), and TF (Finance Sector Index Futures). These futures are issued by the Taiwan Futures Exchange which offers futures and options on major Taiwan stock indices, government bond futures, equity options and 30-day CP interest rate futures. As TX is one of the most active domestic investment products in Taiwan, we predict the price movement of TX in this experiment while other futures are used in model training. The interval of TX dataset is from July 21th, 1998 to December 27th, 2016, i.e., 4,625 trading days. Since TX dataset includes four futures, TX dataset includes trading data for 18,500 trading days totally. The close price of TX dataset in the interval is shown in [Fig 7](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g007/).

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g007/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g007/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g007.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g007.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g007.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g007/?report=objectonly)

[Fig 7](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g007/)

<!--caption a7-->

<!--caption a8-->**Close prices over years (TX dataset).**

The second dataset (NI225 dataset) is Nikkei 225, which is a stock market index for the Tokyo Stock Exchange. NI225 measures the performance of 225 large, publicly owned companies in Japan from a wide array of industry sectors. The choice of this data set is based on the similarities between the economies and cultures of Taiwan and Japan as well as sharing the same color theme in the candlesticks (Red for up and Green for down). The time interval of NI225 dataset is from January 5th, 2001 to November 30th, 2020, i.e., 4,983 trading days in total. The close price of NI225 dataset in the interval is shown in [Fig 8](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g008/).

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g008/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g008/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g008.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g008.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g008.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g008/?report=objectonly)

[Fig 8](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g008/)

<!--caption a7-->

<!--caption a8-->**Close prices over years (NI225 dataset).**

We note that there does not exist class imbalance issues in both datasets. The proportions of prices moving up and moving down are about the same in all merchandises.

#### Metrics 

In order to assess the performance of models, five performance measures are used: accuracy, precision, recall, true positive rate and false positive rate. Because forecasting price movements can be modeled as a dichotomous classification problem, four values _FP_, _TN_, _FN_, and _TP_ can be calculated directly given a classification model, where _FP_ is the number of false positives, _TN_ is the number of true negatives, _FN_ is the number of false negatives and _TP_ is the number of true positives. The definition of the five performance metrics can be calculated directly as follows:

<!--
list-behavior=unordered
prefix-word=
mark-type=disc
max-label-size=0
-->
* accuracy: <nobr><span class="math" id="M5" overflow="scroll" style="width: 7.916em; display: inline-block;"><span style="display: inline-block; position: relative; width: 6.353em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(-0.098em, 1006.35em, 1.615em, -999.997em); top: -1.006em; left: 0em;"><span class="mrow" id="MathJax-Span-119"><span class="mfrac" id="MathJax-Span-120"><span style="display: inline-block; position: relative; width: 6.152em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.329em, 1002.72em, 4.186em, -999.997em); top: -4.433em; left: 50%; margin-left: -1.358em;"><span class="mrow" id="MathJax-Span-121"><span class="mi" id="MathJax-Span-122" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-123" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mo" id="MathJax-Span-124" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-125" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-126" style="font-size: 70.7%; font-family: MathJax_Math-italic;">N<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.329em, 1006em, 4.186em, -999.997em); top: -3.576em; left: 50%; margin-left: -3.022em;"><span class="mrow" id="MathJax-Span-127"><span class="mi" id="MathJax-Span-128" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-129" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mo" id="MathJax-Span-130" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-131" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-132" style="font-size: 70.7%; font-family: MathJax_Math-italic;">N<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mo" id="MathJax-Span-133" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-134" style="font-size: 70.7%; font-family: MathJax_Math-italic;">F<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mi" id="MathJax-Span-135" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mo" id="MathJax-Span-136" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-137" style="font-size: 70.7%; font-family: MathJax_Math-italic;">F<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mi" id="MathJax-Span-138" style="font-size: 70.7%; font-family: MathJax_Math-italic;">N<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1006.15em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 6.152em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 1.011em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.622em; border-left: 0px solid; width: 0px; height: 1.878em;"></span></span></nobr>

* precision: <nobr><span class="math" id="M6" overflow="scroll" style="width: 3.682em; display: inline-block;"><span style="display: inline-block; position: relative; width: 2.976em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(-0.048em, 1002.98em, 1.615em, -999.997em); top: -1.006em; left: 0em;"><span class="mrow" id="MathJax-Span-140"><span class="mfrac" id="MathJax-Span-141"><span style="display: inline-block; position: relative; width: 2.775em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.329em, 1001.01em, 4.136em, -999.997em); top: -4.383em; left: 50%; margin-left: -0.502em;"><span class="mrow" id="MathJax-Span-142"><span class="mi" id="MathJax-Span-143" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-144" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.329em, 1002.62em, 4.186em, -999.997em); top: -3.576em; left: 50%; margin-left: -1.308em;"><span class="mrow" id="MathJax-Span-145"><span class="mi" id="MathJax-Span-146" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-147" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mo" id="MathJax-Span-148" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-149" style="font-size: 70.7%; font-family: MathJax_Math-italic;">F<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mi" id="MathJax-Span-150" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1002.77em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 2.775em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 1.011em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.622em; border-left: 0px solid; width: 0px; height: 1.753em;"></span></span></nobr>

* recall: <nobr><span class="math" id="M7" overflow="scroll" style="width: 3.833em; display: inline-block;"><span style="display: inline-block; position: relative; width: 3.077em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(-0.048em, 1003.08em, 1.615em, -999.997em); top: -1.006em; left: 0em;"><span class="mrow" id="MathJax-Span-152"><span class="mfrac" id="MathJax-Span-153"><span style="display: inline-block; position: relative; width: 2.876em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.329em, 1001.01em, 4.136em, -999.997em); top: -4.383em; left: 50%; margin-left: -0.502em;"><span class="mrow" id="MathJax-Span-154"><span class="mi" id="MathJax-Span-155" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-156" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.329em, 1002.72em, 4.186em, -999.997em); top: -3.576em; left: 50%; margin-left: -1.358em;"><span class="mrow" id="MathJax-Span-157"><span class="mi" id="MathJax-Span-158" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-159" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mo" id="MathJax-Span-160" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-161" style="font-size: 70.7%; font-family: MathJax_Math-italic;">F<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mi" id="MathJax-Span-162" style="font-size: 70.7%; font-family: MathJax_Math-italic;">N<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1002.88em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 2.876em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 1.011em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.622em; border-left: 0px solid; width: 0px; height: 1.753em;"></span></span></nobr>

* true positive rate: <nobr><span class="math" id="M8" overflow="scroll" style="width: 3.833em; display: inline-block;"><span style="display: inline-block; position: relative; width: 3.077em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(-0.048em, 1003.08em, 1.615em, -999.997em); top: -1.006em; left: 0em;"><span class="mrow" id="MathJax-Span-164"><span class="mfrac" id="MathJax-Span-165"><span style="display: inline-block; position: relative; width: 2.876em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.329em, 1001.01em, 4.136em, -999.997em); top: -4.383em; left: 50%; margin-left: -0.502em;"><span class="mrow" id="MathJax-Span-166"><span class="mi" id="MathJax-Span-167" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-168" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.329em, 1002.72em, 4.186em, -999.997em); top: -3.576em; left: 50%; margin-left: -1.358em;"><span class="mrow" id="MathJax-Span-169"><span class="mi" id="MathJax-Span-170" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-171" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mo" id="MathJax-Span-172" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-173" style="font-size: 70.7%; font-family: MathJax_Math-italic;">F<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mi" id="MathJax-Span-174" style="font-size: 70.7%; font-family: MathJax_Math-italic;">N<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1002.88em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 2.876em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 1.011em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.622em; border-left: 0px solid; width: 0px; height: 1.753em;"></span></span></nobr>

* false positive rate: <nobr><span class="math" id="M9" overflow="scroll" style="width: 3.833em; display: inline-block;"><span style="display: inline-block; position: relative; width: 3.077em; height: 0px; font-size: 124%;"><span style="position: absolute; clip: rect(-0.048em, 1003.08em, 1.615em, -999.997em); top: -1.006em; left: 0em;"><span class="mrow" id="MathJax-Span-176"><span class="mfrac" id="MathJax-Span-177"><span style="display: inline-block; position: relative; width: 2.876em; height: 0px; margin-right: 0.103em; margin-left: 0.103em;"><span style="position: absolute; clip: rect(3.329em, 1001.06em, 4.136em, -999.997em); top: -4.383em; left: 50%; margin-left: -0.552em;"><span class="mrow" id="MathJax-Span-178"><span class="mi" id="MathJax-Span-179" style="font-size: 70.7%; font-family: MathJax_Math-italic;">F<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mi" id="MathJax-Span-180" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(3.329em, 1002.72em, 4.186em, -999.997em); top: -3.576em; left: 50%; margin-left: -1.358em;"><span class="mrow" id="MathJax-Span-181"><span class="mi" id="MathJax-Span-182" style="font-size: 70.7%; font-family: MathJax_Math-italic;">F<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span><span class="mi" id="MathJax-Span-183" style="font-size: 70.7%; font-family: MathJax_Math-italic;">P<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mo" id="MathJax-Span-184" style="font-size: 70.7%; font-family: MathJax_Main;">+</span><span class="mi" id="MathJax-Span-185" style="font-size: 70.7%; font-family: MathJax_Math-italic;">T<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.103em;"></span></span><span class="mi" id="MathJax-Span-186" style="font-size: 70.7%; font-family: MathJax_Math-italic;">N<span style="display: inline-block; overflow: hidden; height: 1px; width: 0.053em;"></span></span></span><span style="display: inline-block; width: 0px; height: 3.984em;"></span></span><span style="position: absolute; clip: rect(0.859em, 1002.88em, 1.212em, -999.997em); top: -1.258em; left: 0em;"><span style="display: inline-block; overflow: hidden; vertical-align: 0em; border-top: 1.3px solid; width: 2.876em; height: 0px;"></span><span style="display: inline-block; width: 0px; height: 1.061em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 1.011em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.622em; border-left: 0px solid; width: 0px; height: 1.753em;"></span></span></nobr>

#### Validation 

Since data from financial indices are time series, nested cross validation is used to validate the model performance [[36](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/#pone.0252404.ref036)]. Due to the nature of time series data, the training data and test data should be split chronologically. This aims to simulate the situation that we stand in the present and forecast the future so that the data after “the present” should not be used for fitting the model.

In our experiment, the TX data from 1998 to 2007 are first considered. The TX data in this time period are split into three sets: the training data consist of the data from 1998 to 2005, the data for 2006 are used for the validation of models, and the 2007 data are served as test data. After that, the considered time period keeps extended by one year until 2016 and the data in the corresponding time period are split in the same way as described above. Similarly, for the NI225 dataset, we first consider data from 2001 to 2009. The training data consist of the data from 2001 to 2009, the validation data is the data of 2010, the testing data is the 2011 data. The considered time period keeps extended by one year until 2019. Features used in each model could be derived from merchandises data and response variable is the price movement for a given index on a selected date. The generation of features in different models may need data from various number of trading dates. For example, suppose the duration of trading dates in the TX data are from 2015/1/1 to 2015/1/20, the feature used in DPP is the 20-day candlestick chart built by the trading data between 2015/1/1 to 2015/1/20.

The parameters used in our study are set to be _k_ = 20 and _m_ = 3 in DPP. The assessment measure reported is the average of performance measures obtained from five randomly selected training and test data sets.

### Performance evaluation

In this section, we examine the performance of the proposed DPP based model, the index-based ensemble model IEM, the additive model Prophet, and the recurrent neural network based model LSTM. Each value reported in Tables [​Tables11](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t001/) and [​and22](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t002/) is the proportion of correct predictions made by a prediction model for the entire year.

<!--table ft1-->

<!--table-wrap mode="anchored" t5-->

### Table 1

<!--caption a7-->

<!--caption a8-->**Accuracy comparison for each year (TX dataset).**

                 Year                  | Experiment
                 DPP                   |    IEM     | Prophet |  LSTM 
:--------------------------------------:|:----------:|:-------:|:------:|:------:
                 2007                  |   79.76%   | 82.80%  | 52.43% | 54.46%
                 2008                  |   82.28%   | 84.94%  | 48.79% | 61.94%
                 2009                  |   78.47%   | 73.37%  | 44.62% | 52.63%
                 2010                  |   77.46%   | 78.75%  | 51.79% | 54.82%
                 2011                  |   76.34%   | 80.77%  | 51.01% | 52.23%
                 2012                  |   84.09%   | 82.06%  | 57.62% | 55.94%
                 2013                  |   86.00%   | 78.52%  | 49.59% | 49.76%
                 2014                  |   79.68%   | 77.49%  | 56.45% | 58.22%
                 2015                  |   82.23%   | 81.63%  | 53.27% | 57.01%
                 2016                  |   81.86%   | 79.42%  | 52.04% | 56.56%
     Overall Average (2007–2016)       |   80.82%   | 79.98%  | 51.76% | 55.36%
Most Recent 5-Year Average (2012–2016) |   82.78%   | 79.83%  | 53.79% | 55.50%

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t001/?report=objectonly)

<!--table ft1-->

<!--table-wrap mode="anchored" t5-->

### Table 2

<!--caption a7-->

<!--caption a8-->**Accuracy comparison for each year (NI225 dataset).**

                 Year                  | Experiment
                 DPP                   |    IEM     | Prophet |  LSTM 
:--------------------------------------:|:----------:|:-------:|:------:|:------:
                 2011                  |   65.60%   | 55.00%  | 51.16% | 50.00%
                 2012                  |   66.37%   | 52.77%  | 38.63% | 57.33%
                 2013                  |   65.92%   | 53.36%  | 60.46% | 55.85%
                 2014                  |   65.90%   | 54.38%  | 55.81% | 54.75%
                 2015                  |   67.95%   | 54.97%  | 45.23% | 51.58%
                 2016                  |   66.36%   | 55.00%  | 54.76% | 54.05%
                 2017                  |   66.73%   | 49.36%  | 41.67% | 52.96%
                 2018                  |   67.51%   | 57.45%  | 50.00% | 53.15%
                 2019                  |   66.49%   | 57.41%  | 64.76% | 53.21%
     Overall Average (2011–2019)       |   66.53%   | 54.41%  | 51.39% | 53.65%
Most Recent 5-Year Average (2015–2019) |   67.08%   | 54.84%  | 51.28% | 52.99%

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t002/?report=objectonly)

#### Evaluation on the TX dataset 

To achieve the optimal results, we use data of all four futures in the TX dataset (i.e., TX, Mini-TX, TE and TF) to train DPP, IEM, and LSTM. With large number of parameters, deep learning models usually require more data in their training process to achieve satisfactory accuracy. Note that this is based on the assumption that different products with similar patterns in candlestick charts may lead to similar price movements. In contrast, only the TAIEX futures (i.e, TX, 4,625 records in total) are used to train Prophet since Prophet predicts the close price by extracting the characteristics of the time series of historical close prices. [Table 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t001/) shows the accuracy values of 4 models in each year of the TX dataset using nested cross-validation.

First, it is evident that Prophet and LSTM models are not comparable with DPP and IEM based models due to the relatively low accuracy values in [Table 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t001/). It can be seen that the accuracy values of DPP and IEM are comparable when data in the period from 2007 to 2016 are used, though DPP performs slightly better. However, DPP outperforms IEM by about 3% when the 2012–2016 data are used. An interesting finding here is that the accuracy of DPP in the recent five years (82.78%) is higher than that in the recent ten years (80.82%). On the contrary, the accuracy of IEM in the recent five years (79.83%) makes no significant difference compared to that in the recent ten years (79.98%). We find that DPP can achieve higher accuracy values than IEM in six out of ten years and this could imply that increase of the size in training data could bring more advantage to DPP than IEM as more data could be used for model training in latter years in nested cross-validation. In general, deep-learning models have more parameters and require more data to tune these parameters to improve performance. As a deep-learning-based approach, DPP could achieve better accuracy with the increase of training data whereas IEM may not be able to do so in this experiment.

In addition, the receiver operating characteristic (ROC) curves and precision-recall (PR) curves of these four models based on the TX dataset are provided in Figs [​Figs99](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g009/) and [​and10.10](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g010/). Both figures show that the largest area under either ROC or PR curves is based on our proposed method DPP, which supports that the DPP based model is preferable compared to the other 3 models.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g009/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g009/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g009.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g009.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g009.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g009/?report=objectonly)

[Fig 9](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g009/)

<!--caption a7-->

<!--caption a8-->**ROC curve (TX dataset).**

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g010/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g010/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g010.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g010.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g010.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g010/?report=objectonly)

[Fig 10](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g010/)

<!--caption a7-->

<!--caption a8-->**PR curve (TX dataset).**

We can further compare the accuracy values over all approaches using the TX dataset by observing the accuracy report in [Table 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t001/) and the run chart in [Fig 7](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g007/). In year 2007, IEM outperforms all other approaches. The price in year 2007 has three big jumps and two big drops. Inferring the price trend by indices works well in this situation. In year 2008, IEM and DPP can predict the trend well when the price goes down with consecutive big drops. In year 2009 and year 2010, all accuracy values are relative lower compared to them in other years. The run chart shows that the price at the beginning of year 2009 is around the lowest price (about 4K) among the recent five years but the price keeps going up and the highest price is about 8K. The price movement is also choppy on mixed results and such a situation makes the prediction of the price movement more difficult for all approaches. Move to the results in year 2012 and year 2013, DPP reaches the highest accuracy whereas the accuracy of IEM drops suddenly in year 2013. We can observe that the price in year 2013 vibrates frequently although it presents a upward trend. This implies that DPP would outperform other approaches in such a situation.

#### Evaluation on the NI225 dataset 

Since the NI225 dataset only includes open, close, high, and low prices, all models use all price measures in their training process. [Table 2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t002/) shows the accuracy values of 4 models in each year of the NI225 dataset using nested cross-validation.

Contrast to the previous case using the TX dataset, it is clear that the DPP based models outperform the models using the other 3 approaches by about 10% or higher of the accuracy values. Figs [​Figs1111](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g011/) and [​and1212](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g012/) shows ROC and PR curves of these four models based on the NI225 dataset individually. Again, the largest area under either ROC or PR curves appears on the one based on DPP method, which indicates that DPP based model is superior to the other 3 models.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g011/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g011/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g011.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g011.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g011.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g011/?report=objectonly)

[Fig 11](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g011/)

<!--caption a7-->

<!--caption a8-->**ROC curve (NI225 dataset).**

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g012/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g012/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g012.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g012.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g012.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g012/?report=objectonly)

[Fig 12](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g012/)

<!--caption a7-->

<!--caption a8-->**PR curve (NI225 dataset).**

From the accuracy report in [Table 2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/table/pone.0252404.t002/) and the run chart in [Fig 8](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g008/), we can observe that in year 2012, DPP can reach a relative high accuracy (66.37%) whereas IEM are with the lowest accuracy values (52.77% and 38.63%). A similar case is in year 2017 where the frequency and amplitude of price vibration are increasing over time. From both cases, DPP works well under the situation of frequent vibration of prices in the NI225 dataset whereas IEM suffers from this situation. The accuracy values for DPP are slightly lower in both year 2013 and year 2014 as the price climbs from the lowest price among five years in the beginning of year 2013 to the relative highest price in the end of year 2014.

### Sensitivity analysis

We conduct the sensitivity analysis in this section. The results of models exposed to different time frames and data sources are firstly presented. The choice of hyper-parameters in DPP are then discussed.

This experiments start from how the accuracy of DPP and IEM in the TX dataset and the NI225 dataset changes in two different markets in the same time period. Here, we omit Prophet and LSTM since their accuracy values are not comparable to DPP and IEM. Since Taiwan and Japan are neighboring countries in Asia, they share a part of similar markets in their economic activities so that their state economies are usually correlated. Therefore, we can further identify the appropriate time when to use a model by such comparisons. We first select the price information from both datasets during 2011/1/1 to 2016/12/31. We then use Z-scores to normalize the prices for both datasets as shown in [Fig 13](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g013/). In year 2011, the prices in both datasets are down-trended. The amplitude of the TX dataset (1.62) is much larger than that of NI225 dataset (0.47). Moreover, there is a sudden drop in the middle of year 2001 in the TX dataset. In this case, IEM can reach 3% higher accuracy than DPP. On the other hand, the price movement in the NI225 dataset is relatively stable. In this case, the accuracy of DPP is 10% higher than IEM. In year 2013, the price in the TX dataset goes up with many small bumps. In this case, DPP achieves the best accuracy (86.00%), which shows small bumps would not affect the prediction of DPP. On the other hand, the price in the NI225 dataset has a big jump in the first half of year 2013 and many bumps in the second half of this year. The accuracy of DPP (65.92%) and IEM (53.36%) in this year are relative lower than those in the other years. This shows the limitation of DPP and IEM.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g013/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g013/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g013.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g013.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g013.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g013/?report=objectonly)

[Fig 13](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g013/)

<!--caption a7-->

<!--caption a8-->**The movement of close prices in TX dataset and NI225 dataset from 2011/1/1 to 2016/12/31.**

This series of experiments explore how the accuracy of DPP varies as the hyper-parameters of the number of hidden features in GRU (denoted as _Nh_), the learning rate _ρ_ (denoted as rho) for RMSProp and the dropout rate are changed. Observing such evolution of hyper-parameters can help the selection of proper parameters to achieve the best accuracy using different datasets.

First, the TX dataset is considered. [Fig 14](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g014/) shows the accuracy values when the learning rate _ρ_ varied and the dropout rate is 0.5. The highest accuracy is around 81% when _ρ_ = 0.9 and _Nh_ = 128 and the accuracy seems to be sensitive to the change of _Nh_ but somehow less sensitive to the choice of _ρ_ when the dropout rate is 0.5. [Fig 15](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g015/) shows the accuracy values when the dropout rate varies and _ρ_ is 0.9. We find that the highest accuracy is around 81% when _Nh_ = 128 and the accuracy is sensitive to the change of _Nh_ but less sensitive to the choice of the dropout rate when _ρ_ is 0.9. To conclude, the best combination of hyper-parameters among our choices using the TX dataset is that _ρ_ is 0.9, the dropout rate is 0.5, and _Nh_ is 128.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g014/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g014/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g014.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g014.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g014.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g014/?report=objectonly)

[Fig 14](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g014/)

<!--caption a7-->

<!--caption a8-->**Accuracy with _ρ_ varied (TX dataset).**

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g015/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g015/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g015.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g015.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g015.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g015/?report=objectonly)

[Fig 15](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g015/)

<!--caption a7-->

<!--caption a8-->**Accuracy with droupout rate varied (TX dataset).**

Second, the NI225 dataset is considered. [Fig 16](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g016/) shows the accuracy values as _ρ_ varies and the dropout rate is 0.7, while [Fig 17](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g017/) shows the accuracy as the dropout rate varies but _ρ_ is 0.99. We observe that the accuracy is sensitive to the choice of _Nh_ but slightly insensitive to the selection of _ρ_ when the dropout rate is 0.7. Similarly, the accuracy is again sensitive to the choice of _Nh_ and relatively insensitive to the selection of the dropout rate when _ρ_ is 0.99. In addition, the best combination of hyper-parameters among our choices using the NI225 dataset is that _ρ_ is 0.99, the dropout rate is 0.7, and _Nh_ is 64.

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g016/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g016/)[![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g016.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g016.jpg "Click on image to zoom")](https://www.ncbi.nlm.nih.gov/core/lw/2.0/html/tileshop_pmc/tileshop_pmc_inline.html?title=Click%20on%20image%20to%20zoom&p=PMC3&id=8216512_pone.0252404.g016.jpg)

[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g016/?report=objectonly)

[Fig 16](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g016/)

<!--caption a7-->

<!--caption a8-->**Accuracy with _ρ_ varied (NI225 dataset).**

<!--fig ft0-->

<!--fig mode=article f1-->

[<!--fig/graphic|fig/alternatives/graphic mode="anchored" m1-->

![An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g017.jpg](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.g017.jpg "An external file that holds a picture, illustration, etc.
Object name is pone.0252404.g017.jpg")](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g017/)

[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g017/)[Open in a separate window](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g017/?report=objectonly)

[Fig 17](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/figure/pone.0252404.g017/)

<!--caption a7-->

<!--caption a8-->**Accuracy with droupout rate varied (NI225 dataset).**

Note that the size of the NI225 dataset is around one-fourth of that of the TX dataset. The experimental results show that the optimal setting _Nh_ using the NI225 dataset is smaller than that using the TX dataset. A proper size of hidden features usually depends on the size of data. Learning a large size of hidden features from a small dataset usually suffers from the issue of over-fitting. We can also find that the optimal settings of _ρ_ and the learning rate using the NI225 dataset are larger than those using the TX dataset, respectively. A larger _ρ_ can help gradient to take more of the historical gradient than the coming gradient into account, which is helpful to find the optimal solution for a smaller dataset. A larger dropout rate is also a common way to prevent the over-fitting problem when the data size is relatively small.

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## Conclusion

Technical analysis is used to predict price movements in the financial markets by using historical price charts and market statistics. Candlestick charts have been one of the most widely used charts as they contain many useful and explainable visual patterns for decision making. This paper proposed a framework DPP to predict the price movement by taking the candlestick charts as its input. Specifically, DPP firstly decomposes a given candlestick chart into several sub-charts, derives the best representation of sub-charts by a CNN autoencoder, and predicts the price movement by GRU. Extensive experiments are conducted using the Taiwan Exchange Capitalization Weighted Stock index and Nikkei 225, a stock index in Japan. The experimental results not only show that DPP outperforms the state-of-the-art methods but also discuss the effect of different stock markets to DPP.

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## Supporting information

<!--/article/body/sec/-->

#### S1 Data

<!--caption a9-->**TX dataset.** 

This dataset are from the Taiwan Futures Exchange (TAIFEX). The interval of this dataset is from July 21th, 1998 to December 27th, 2016, i.e., 4,625 trading days.

(CSV)

[Click here for additional data file.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/bin/pone.0252404.s001.csv)<sup>(113M, csv)</sup>

[Go to:](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8216512/# "Go to other sections in this page")

## 