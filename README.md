# notebooks
---

These notebooks complement the Risk papers [Differential Machine Learning](https://www.risk.net/cutting-edge/banking/7688441/differential-machine-learning-the-shape-of-things-to-come) and [Axes that matter](https://www.risk.net/cutting-edge/banking/7877231/axes-that-matter-pca-with-a-difference) by Brian Huge and [Antoine Savine](https://antoinesavine.com) (2020-21), including code, practical implementation considerations and extensions. 

**DifferentialML.ipynb** is the main demonstration notebook for the concepts and ideas of the working paper. We provide a simple, yet fully functional implementation of twin networks and differential training, and apply them to some textbook examples, including the reproduction of the Bachelier example in the section 3.1 of the article. We also discuss the details of a practical implementation, including the important matters of initialization, optimization and normalization, which are not covered in the paper. This notebook is based on TensorFlow 1.x and built to run on GPU, either locally or on Google Colab. 

<a href="https://colab.research.google.com/github/differential-machine-learning/notebooks/blob/master/DifferentialML.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

**DifferentialMLTF2.ipynb** is an upgrade to DifferentialML.ipynb for TensorFlow 2.x. Its current form does not run 'idiomatic' TensorFLow 2 code, what we do is really run TensorFlow 1 code in TensorFlow 2. Still, the new notebook benefits from the latest TensorFlow improvements resulting in a noticeable performance improvement. DifferentialML.ipynb will no longer be maintained going forward, bug fixes, improvements and extensions will be implemented directly in the TensorFlow 2 notebook.

<a href="https://colab.research.google.com/github/differential-machine-learning/notebooks/blob/master/DifferentialMLTF2.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

**DifferentialRegression.ipynb** applies differential learning in the context of classic regression models. In the article, we applied differential learning to deep neural networks only. This notebook applies it to polynomial regression to the basket option in a correlated Bachelier model of section 3,1. We see that, with regression too, differential training provides a massive performance improvement, without the need for additional regularization, or hyperparameter optimization. Differential regression is covered in detail in the upcoming follow-up article <b> Axes that matter: PCA with a difference</b>.

<a href="https://colab.research.google.com/github/differential-machine-learning/notebooks/blob/master/DifferentialRegression.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
 
**DifferentialPCA.ipynb** implements and illustrates differential dimension reduction covered in the follow-up article <b> Axes that matter: PCA with a difference</b>.

<a href="https://colab.research.google.com/github/differential-machine-learning/notebooks/blob/master/DifferentialPCA.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

**Bermudan5F.ipynb** applies differential regression and PCA to the determination of risk factors and continuation values of Bermudan options, giving a flavour of the application of differential ML to real-world problems. Factor dependence of Derivatives transactions and trading books, in particular, is usually identified by manual analysis. This notebook leverages synthetic data simulated with AAD, and the differential ML algorithms designed to correctly consume differential data, to perform this analysis automatically, from simulated data, with guaranteed reliability. This notebook uses differential regression and PCA developed in DifferentialRegression.ipynb and DifferentialPCA.ipynb, and it is recommended to read these two notebooks first. The numerical examples of the October 2021 Risk article <b> Axes that matter: PCA with a difference </b> were produced with this notebook.

<a href="https://colab.research.google.com/github/differential-machine-learning/notebooks/blob/master/Bermudan5F.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

We also posted additional material [here](https://differential-machine-learning.github.io/appendices/), including mathematical proofs, various extensions and considerations for an implementation in production.
          
[github.com/differential-machine-learning](https://github.com/differential-machine-learning)
<img src="differential.png">
