# Encoding Time Series as Images

## Gramian Angular Field Imaging

[![Louis de Vitry](https://miro.medium.com/fit/c/96/96/1*GV215HyNcaabbvT1zIVClA.jpeg)](https://medium.com/@louisdevitry?source=post_page-----b043becbdbf3-----------------------------------)

[Louis de Vitry]


The Deep Learning boom is largely fueled by its success in computer vision and speech recognition. However, when it comes to time series, building predictive models can be gruesome ([Recurrent Neural Networks are difficult to train](https://www.coursera.org/lecture/neural-networks/why-it-is-difficult-to-train-an-rnn-kTsBP), research is less applicable, and no pre-trained models exist, 1D-CNN can be inconvenient).

To leverage the techniques and the insights brought by the recent developments of computer vision, I will present and discuss one way to encode time series as images: the **Gramian Angular Field.**

Beside the math pre-requisites (min-max scaler, dot-product and Gram Matrix), this post will contain explanations and solutions on:

* Why is the Gram matrix structure a good 2D representation of univariate time series?
* Why the Gram Matrix dot-product fail to represent data for CNN?
* What is the operation that makes Gram Matrix structure ready for CNN?

as well as Python gists of:

* Efficient numpy implementation of the Gramian Angular Field computations.
* GIFs generation using matplotlib + movieditor.

**TL:DR:** We perform a polar encoding of the data followed by a Gram Matrix like operation on the resulting angles.

![](https://miro.medium.com/max/1378/1*A0yHZ8GD47cQd1OACTiz6Q.gif)
Various steps of the Gramian Angular Field conversion (see below for the GIF code)

# Mathematics pre-requisites

Because the Mathematics of the Gramian Angular Field is intrisically linked to the inner product and the corresponding Gram Matrix, here is a reminder:

The Mathematics of this method being **intrinsically linked to the inner product and the corresponding Gram Matrix**, I write a brief reminder about its meaning.

## Dot product

The inner product is an **operation between two vectors**, which **measures their “similarity”**. It _allows the use_ of notions from traditional _Euclidian Geometry_: length, angles, orthogonality in dimension 2 and 3.

In the simplest case (2D space), the inner product between two vectors u and v is defined as:

![](https://miro.medium.com/max/60/1*7_HS3YaNpwHBfSmnSyTQVA.png?q=20)![](https://miro.medium.com/max/402/1*7_HS3YaNpwHBfSmnSyTQVA.png)
Dot product in 2D space
and it can be shown that:

![](https://miro.medium.com/max/60/1*we_-r0dEqLnSXU78tZbyVw.png?q=20)![](https://miro.medium.com/max/426/1*we_-r0dEqLnSXU78tZbyVw.png)
Alternative expression in 2D space

Therefore, if _u_ and _v_ are of norm _1_, we obtain:

![](https://miro.medium.com/max/60/1*xbxgTXvouS_z_u9rzeWwrQ.png?q=20)![](https://miro.medium.com/max/246/1*xbxgTXvouS_z_u9rzeWwrQ.png)
Inner product of units vector is characterized by their angular difference θ

Therefore, when dealing with **unit vectors**, their **inner product is solely characterized by the angle θ** (expressed in radian) between _u_ and _v_. Furthermore, the resulting value lies within [-1, 1].

This properties will prove to be useful in the rest of the article.

**Note:** In the Euclidian setting (dimension n), the inner product of two vectors _u_ and _v_ is formally defined by

![](https://miro.medium.com/max/60/1*HEj0qy_q2k6BpHmOjl8aFw.png?q=20)![](https://miro.medium.com/max/270/1*HEj0qy_q2k6BpHmOjl8aFw.png)
Inner product between _u_ and v

## Gram Matrix

The **Gram Matrix** is a useful tool in Linear Algebra and Geometry. Among others, it is frequently used to compute the _linear dependence of a set of vectors_.

**Definition:** the _Gram Matrix_ of a set of _n_ vectors is a matrix defined by the dot-product (_see similarity_) of every couple of vectors. Mathematically, this translates to:

![](https://miro.medium.com/max/60/1*RtbJowmRgoETCOoH6IjKxQ.png?q=20)![](https://miro.medium.com/max/370/1*RtbJowmRgoETCOoH6IjKxQ.png)
Gram Matrix of a set of n vectors

Again, assuming that all 2D vectors are of norm one, we obtain:

![](https://miro.medium.com/max/60/1*lYbwYSLrPqYVbkI8XVySjw.png?q=20)![](https://miro.medium.com/max/408/1*lYbwYSLrPqYVbkI8XVySjw.png)
Gram Matrix of units vector

where Φ_(i, j)_ is the angle between vectors _i_ and _j_.

**Key takeaway: Why use the Gram Matrix?**

The Gram Matrix preserves the temporal dependency</mark>. Since time increases as the position moves from top-left to bottom-right, the time dimension is encoded into the geometry of the matrix.

![](https://miro.medium.com/freeze/max/60/1*xrmFSfNnX0m4Y5poN-Xtqw.gif?q=20)![](https://miro.medium.com/max/700/1*xrmFSfNnX0m4Y5poN-Xtqw.gif)

Known GAF values at different timesteps

**Note:** 

This article is also motivated by the intuition that univariate time series somehow fail to explain the co-occurence and the latent states of the data; we should aim to find alternate and richer representations.

# Naïve implementation

Let’s compute the Gram Matrix of the time series values:

![](https://miro.medium.com/max/60/1*aRSdlEkCVwPWJcG87b5pAQ.png?q=20)![](https://miro.medium.com/max/280/1*aRSdlEkCVwPWJcG87b5pAQ.png)

## Scale the serie with a Min-Max scaler onto [-1, 1]

So that the inner product is not biased in favor of the observation with the largest value, we need to scale the data:

![](https://miro.medium.com/max/60/1*2kGHaVLv77fxfObkf-1gSA.png?q=20)![](https://miro.medium.com/max/454/1*2kGHaVLv77fxfObkf-1gSA.png)
Min-Max scaling

The _standard scaler is not an appropriate_ _candidate_ in this use case, because both its output range and the resulting inner products can exceed [-1, 1].

However, coupled with the Min-Max scaler, the inner product does preserve the output range:

![](https://miro.medium.com/max/60/1*IERV45qNvJ1sXe0mfi4nDA.png?q=20)![](https://miro.medium.com/max/282/1*IERV45qNvJ1sXe0mfi4nDA.png)

The dot product preserves the range


The choice of having dot products within [-1, 1] is not innocuous. A range of [-1, 1] is extremely desirable, if not necessary, as input range for Neural Networks.

## Noisy images?

Now that the time series is scaled, we can **compute pairwise dot-products** and store them in the Gram Matrix:

![](https://miro.medium.com/max/60/1*MiyM95NJ7HnSFjNocYBDrg.png?q=20)![](https://miro.medium.com/max/352/1*MiyM95NJ7HnSFjNocYBDrg.png)

Gram Matrix of the scaled time serie

Let’s gain insights about this imaging by inspecting the values of G:

![](https://miro.medium.com/max/60/1*ProGxA01maOVgDcK6EeNkQ.png?q=20)![](https://miro.medium.com/max/700/1*ProGxA01maOVgDcK6EeNkQ.png)

Gram Matrix values follow a gaussian distribution (time series is a cosinus)

We observe two things:

1.  The **outputs** seem to **follow a gaussian distribution** centered around 0.
2.  The **resulting image is noisy**.

The **former explains the latter**, because the more Gaussian the data is, the harder it gets to distinguish it from Gaussian noise.

This will be a problem for our Neural Networks. Additionally, it has been established that [CNN work better with sparse data](https://www.quora.com/Why-are-deep-neural-networks-so-bad-with-sparse-data).

## The origin of non-sparsity

The Gaussian distribution is not very surprising. When looking at the 3D plot of the inner product values _z_, for every possible combination of (_x_, _y_) ∈ R², we obtain:

![](https://miro.medium.com/max/60/1*mU3tWzMdXpT5bGQ9U3W7xQ.png?q=20)![](https://miro.medium.com/max/700/1*mU3tWzMdXpT5bGQ9U3W7xQ.png)

3D surface of the dot product

Under the assumption that **the values** of the time series follow a Uniform distribution [-1, 1], the Gram Matrix values follow a Gaussian-like distribution. Here are **histograms of the outputs** of the Gram Matrix valued for different time series lengths _n_:

![](https://miro.medium.com/max/60/1*-4P1xRryR_RYmSWt3CqlXA.png?q=20)![](https://miro.medium.com/max/700/1*-4P1xRryR_RYmSWt3CqlXA.png)

Gram Matrix output for time series of length n (in red is the density of N(0, 0.33))

# Preliminary Encoding

## Why do we need one?

As univariate time series are in 1D and the dot product fails to distinguish the valuable informations from Gaussian noise, there is no other way to take advantage of “angular” relations than changing the space.

We must therefore encode the time serie into a space of at least 2 dimensions, prior to using Gram Matrix like constructs. To do so, we will construct a **bijective mapping** between our 1D time serie and a 2D space, so as not to lose any informations.

> This encoding is largely inspired from **polar coordinates transformations**, except in this case, the radius coordinate expresses time.

## Step 1: Scale the serie onto [-1, 1] with a Min-Max scaler

We proceed similarly than in the naïve implementation. Coupled with the Min-Max scaler, our polar encoding will be bijective, the use the _arccos_ function bijective (see next step).

## **Step 2: Convert the scaled time serie into “polar coordinates”**

Two quantities need to be accounted for, the **value of the time series** and its **corresponding timestamp**. These two variables will be expressed respectively with the **angle** and the **radius**.


![](https://miro.medium.com/max/60/1*HTAk4ptd0a9Tp9wFc5scXg.png?q=20)![](https://miro.medium.com/max/510/1*HTAk4ptd0a9Tp9wFc5scXg.png)

Polar Encoding for time series

Assuming our time series is composed of **_N_** timestamps **_t_** with corresponding values **_x_**_, then:_

* The angles are computed using **_arccos(x)._** They lie within [0, ∏].
* The radius variable is computed by first, we divide the interval [0, 1] into _N_ equal parts. We therefore obtain _N+1_ delimiting __points {0, …, 1}. We then discard 0 and associate consecutively these points to the time series.

Mathematically, it translates to this:

![](https://miro.medium.com/max/60/1*_E5pxbxn6BlXBxcQZB7NSw.png?q=20)![](https://miro.medium.com/max/296/1*_E5pxbxn6BlXBxcQZB7NSw.png)

2D Encoding of the scaled time serie

These encoding has several **advantages**:

1.  The whole encoding is **bijective** (as a composition of bijective functions).
2.  It **preserves temporal dependency** through the _r_ coordinate. This will proved to be extremely useful[*].

# An inner product for time series?

Now that we are in a 2D space, the ensuing question is how can we use the inner product like operations to work with sparsity.

## Why not the inner product of the polar encoded values?

The inner product in the 2D polar space has several limitations, because the norm of each vector has been adjusted for the time dependency. More precisely:

* An inner product between two distinct observations will be biased in favor of the most recent one (because the norm increases with time).

* When computing the inner product of an observation with itself, the resulting norm is biased as well.

Therefore, if an inner product like operation was to exist, it should solely depend on the angle.

## Using angles

As any inner product like operations irremediably casts the information of two distinct observations into one value, we cannot preserve the information given by the two angles altogether. We have to make some concessions.

To explain at best the individual and joined informations on the two angles, the author defines **an alternative operation to the inner product**:

<figure class="jh ji jj jk jl dl cs ct paragraph-image">
    ![](https://miro.medium.com/max/60/1*5jioAqHCGmogS9JjpKgudg.png?q=20)![](https://miro.medium.com/max/176/1*5jioAqHCGmogS9JjpKgudg.png)
    <figcaption class="jm jn cu cs ct jo jp bo b fu bq br" data-selectable-paragraph="">Custom operation</figcaption>
</figure>

where the _θ_ are the respective angles from _x_ and _y_ encoding.

**Note:** I choose a different symbol rather than using the inner product for reasons because this operation does not satisfy the [requirements of an inner product](https://en.wikipedia.org/wiki/Inner_product_space#Definition) (linearity, definite positive).

This results in the following Gram-like Matrix:

<figure class="jh ji jj jk jl dl cs ct paragraph-image">
    ![](https://miro.medium.com/max/60/1*5Q2XaC-BqDimZ-2TKz9mbg.png?q=20)![](https://miro.medium.com/max/506/1*5Q2XaC-BqDimZ-2TKz9mbg.png)
</figure>

> The author motivates his choice by : “Second, as opposed to Cartesian coordinates, polar coordinates preserve absolute temporal relations.”

## Advantages

1.  The **diagonal is made of the original value** of the scaled time series (we will approximately reconstruct the time series from the high level features learned by the deep neural network.)
2.  Temporal correlations are accounted for with the relative correlation by superposition of directions with respect to time interval k. PRECISE

## Toward a sparser representation?

Let’s now plot the density of the Gramian Angular Field values:

![](https://miro.medium.com/max/60/1*S22TPejs15CZpTdEiWA8lQ.png?q=20)![](https://miro.medium.com/max/700/1*S22TPejs15CZpTdEiWA8lQ.png)

The Gramian Angular Field is less noisy / sparser than the Gram Matrix.

As we can see from the plot above, the Gramian Angular Field is much sparser. To explain this, let’s re-express _u_ ⊕ _v_ in Cartesian coordinates:

![](https://miro.medium.com/max/60/1*The8P4Pigt7h9LVsY-mgPQ.png?q=20)![](https://miro.medium.com/max/424/1*The8P4Pigt7h9LVsY-mgPQ.png)

Converting back the expression in Cartesian coordinates</figcaption>
</figure>

We notice in the last term above that the **newly constructed operation** corresponds to a **penalized version of the conventional inner product:**

![](https://miro.medium.com/max/60/1*CHzcDqJ9-HbtH6gKgxMsjw.png?q=20)![](https://miro.medium.com/max/594/1*CHzcDqJ9-HbtH6gKgxMsjw.png)
    <figcaption class="jm jn cu cs ct jo jp bo b fu bq br" data-selectable-paragraph="">New operation = Penalized Inner Product</figcaption>
</figure>

Let’s gain some insights on the role of this penalty. Let’s first have a look at the 3D plot of the full operation:

![](https://miro.medium.com/max/60/1*1w277Py5sl0wQPDKEI2mAQ.png?q=20)![](https://miro.medium.com/max/700/1*1w277Py5sl0wQPDKEI2mAQ.png)
    <figcaption class="jm jn cu cs ct jo jp bo b fu bq br" data-selectable-paragraph="">3D plot of the operation</figcaption>
</figure>

As we can see:

* The penalty shifts the mean output towards -1.
* The closer x and y are to 0, the larger is the penalty. The main consequence is that points which were closer to the gaussian noise … (with the dot) are (with the penalized dot)
* For x = y: it is casted to -1
* The outputs are easily distinguishable from Gaussian Noise.

## **Drawbacks**

* With the main diagonal, however, the generated GAM is large due to the augmentation n ⟼n², where the length of the raw time series is n. The author suggests to reduce the size of the GAF by applying Piecewise Aggregation Approximation (Keogh and Pazzani 2000).
* It is not an inner product..

# Show me the code!

A numpy implementation to convert univariate time series into an image and other python code used for this article can be found [here](https://github.com/devitrylouis/imaging_time_series).

As for the gif, I will release it soon (implemented with matplotlib, numpy and moviepy).

# Sources

> This blogpost is largely inspired from the [detailed paper](https://aaai.org/ocs/index.php/WS/AAAIW15/paper/viewFile/10179/10251) Encoding Time Series as Images for Visual Inspection and Classification Using Tiled Convolutional Neural Networks, by Zhiguang Wang and Tim.
>
> This paper also mentions another interesting encoding technique: Markov Transition Field. This encoding will not be covered in this article.

[## [1403.6382] CNN Features off-the-shelf: an Astounding Baseline for Recognition

### Abstract: Recent results indicate that the generic descriptors extracted from the convolutional neural networks are…

arxiv.org](https://arxiv.org/abs/1403.6382)

[## [1411.1792] How transferable are features in deep neural networks?

### Abstract: Many deep neural networks trained on natural images exhibit a curious phenomenon incommon: on the first…

arxiv.](https://arxiv.org/abs/1411.1792)

https://arxiv.org/pdf/1506.00327.pdf

https://stats.stackexchange.com/questions/47051/sparse-representations-for-denoising-problems
