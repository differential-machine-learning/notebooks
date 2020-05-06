# appendices
---

These documents complement the working paper [Differential Machine Learning](https://arxiv.org/abs/2005.02347) by Brian Huge and [Antoine Savine](https://antoinesavine.com) (2020), including mathematical proofs, various extensions and considerations for an implementation in production.

[**App1-LSM.pdf**](https://github.com/differential-machine-learning/appendices/blob/master/App1-LSM.pdf) recalls the details of the classic Least Square Method (LSM) of Longstaff-Schwartz (2001) and formalizes it in machine learning terms. The convergence of approximators trained on LSM datasets is demonstrated with both standard and differential training. 

[**App2-Preprocessing.pdf**](https://github.com/differential-machine-learning/appendices/blob/master/App2-Preprocessing.pdf) discusses data preparation in the context of differential deep learning, and introduces differential PCA, a powerful algorithm capable of significantly improving training with appropriate preparation, and also useful in its own right, e.g. in finance, where differential PCA provides an effective latent representation of the *risk factors* of a given transaction from simulated data alone.

[**App3-Regression.pdf**](https://github.com/differential-machine-learning/appendices/blob/master/App3-Regression.pdf) derives the svd regression formulas for standard, ridge and differential regression, based on eigenvalue decomposition. These formulas are implemented verbatim in the notebook [DifferentialRegression.ipynb](https://github.com/differential-machine-learning/notebooks/blob/master/DifferentialRegression.ipynb).

[**App4-UnsupervisedTraining.pdf**](https://github.com/differential-machine-learning/appendices/blob/master/App4-UnsupervisedTraining.pdf) addresses the important matter of an automated implementation of training algorithms in production systems, in particular it establishes worst case convergence guarantees and asymptotic control necessary for training a special breed of neural networks *without supervision*.

We also posted [here](https://differential-machine-learning.github.io/notebooks/) a working TensorFlow implementation, along with extensions and practical implementation details. 

[github.com/differential-machine-learning](https://github.com/differential-machine-learning)
<img src="differential.png">

# Automatic Adjoint Differentiation (AAD)
---

Everything in the working paper and its complements relies on *differential labels*, the gradients of training labels to training inputs, fed to the machine learning model in an augmented dataset. We have seen that training on differentials offers a massive performance improvement, but, of course, the differential labels must be computed first.

In particularly simple textbook contexts, like a European call in Black & Scholes or a basket option in multi-dimensional Bachelier, differential labels are easily computed in explicit form. In low dimension, they could be computed by finite differences. In a general case with an arbitrary schedule of complex cash-flows simulated in an arbitrarily sophisticated model, closed form differentials are not available and finite differences are far too slow. In dimension 100, every training example must be computed 101 times to estimate differentials by finite differences. In addition, differentials approximated by finite differences may not be accurate enough for the purpose of training: we don't want the optimizer chasing imprecise differentials.

Introduced to finance by the ground breaking *Smoking Adjoints* (Giles and Glasserman, Risk 2006), AAD is a game changing technology allowing to compute differentials of arbitrary computations, automatically, with analytic precision, and for a computation cost of around 2 to 5 times one evaluation, depending on implementation, and *independently on the dimension of the gradient*. 

AAD arguably constitutes the most significant progress in computational finance of the past 20 years. It gave us real-time risk reports for complex Derivatives trading books and regulations like XVA, as well as instantaneous calibrations. It made differentials massively available for research and development in finance. Quoting the conclusion of our Wilmott piece *Computation graphs for AAD and Machine Learning parts 1, 2 and 3* (Savine, Wilmott Magazine, 2019-2020):

*New implementations of AAD are pushing the limits of its efficiency, while quantitative analysts are leveraging them in unexpected ways, besides the evident application to risk sensitivities or calibration.*

To a large extent, differential machine learning is another strong application of AAD. It is AAD that gave us the massive number of accurate differentials necessary to implement it, for a very cheap computation cost, and is ultimately responsible for the spectacular performance improvement. The real-world examples in the Risk paper, sections 3.2 and 3.3, were trained on AAD differential labels.

The Risk paper or the complements do not cover AAD. Readers are referred to the (stellar) founding paper. [This textbook](https://www.amazon.com/Modern-Computational-Finance-Parallel-Simulations-dp-1119539455/dp/1119539455) provides a complete, up to date overview of AAD, its applications in finance, and a complete, professional implementation in modern C++.

The video tutorial below introduces the core ideas in 15 minutes. Click on the picture to play. 

[<Automatic Differentiation Explained in 15min src="https://miro.medium.com/max/1400/1*bHsIA1jy08p71uZcg8HiIQ.png"](https://towardsdatascience.com/automatic-differentiation-15min-video-tutorial-with-application-in-machine-learning-and-finance-333e18c0ecbb)

