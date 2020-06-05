# Some cool open-source Python packages for Machine Learning EP 5

<p align="center">
  <img width="700" src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e9/Sombrero_Galaxy_in_infrared_light_%28Hubble_Space_Telescope_and_Spitzer_Space_Telescope%29.jpg/1920px-Sombrero_Galaxy_in_infrared_light_%28Hubble_Space_Telescope_and_Spitzer_Space_Telescope%29.jpg" alt="Moebius">    
</p>

*Image credit: NASA/JPL-Caltech and The Hubble Heritage Team (STScI/AURA)*


_  


There is a very rich ecosystem of Python libraries related to ML. Here is a list of some “active”, open-source packages that may be useful for ML day-to-day activities.

This post is following these ones:

* [Some cool open-source Python packages for Machine Learning EP 1](https://aetperf.github.io/2019/07/11/Some-cool-open-source-Python-packages-for-Machine-Learning.html) (2019/07/11)
* [Some cool open-source Python packages for Machine Learning EP 2](https://aetperf.github.io/2019/08/08/Some-cool-open-source-Python-packages-for-Machine-Learning-Ep-2.html) (2019/08/08)
* [Some cool open-source Python packages for Machine Learning EP 3](https://aetperf.github.io/2019/10/23/Some-cool-open-source-Python-packages-for-Machine-Learning-Ep-3.html) (2019/10/23)
* [Some cool open-source Python packages for Machine Learning EP 4](https://aetperf.github.io/2020/01/08/Some-cool-open-source-Python-packages-for-Machine-Learning-Ep-4.html) (2020/01/08)

(☞ﾟヮﾟ)☞

_


## Recommender systems

[Surprise](https://github.com/NicolasHug/Surprise) - a scikit building and analyzing recommender systems that deal with explicit rating data.

## Causal Inference

[Causal ML](https://github.com/uber/causalml) - a package that provides a suite of uplift modeling and causal inference methods using machine learning algorithms based on recent research. It provides a standard interface that allows user to estimate the Conditional Average Treatment Effect (CATE) or Individual Treatment Effect (ITE) from experimental or observational data. Essentially, it estimates the causal impact of intervention T on outcome Y for users with observed features X, without strong assumptions on the model form. Here is a quote from [Uber Engineering Blog](https://eng.uber.com/causal-inference-at-uber/):

> At a more granular level, causal inference enables data scientists and product analysts to answer causal questions based on observational data, especially when A/B testing is not possible, or gain additional insights from a well-designed experiment. For example, we may launch an email campaign that is open for participation to all customers in a market. In this case, since we don’t have a randomized control group, how do we measure the campaign’s effect? In another example, suppose we have a randomized, controlled A/B test experiment but not everyone in the treatment group actually receive the treatment (i.e., if they don’t open the email). How do we estimate the treatment effect for the treated? Causal inference enables us to answer these types of questions, leading to better user experiences on our platform.

## Data Annotation

[PigeonXT](https://github.com/dennisbakhuis/pigeonXT) -  an extention to the original [Pigeon](https://github.com/agermanidis/pigeon), created by [Anastasis Germanidis](https://pypi.org/user/agermanidis/). PigeonXT is a simple widget that lets you quickly annotate a dataset of unlabeled examples from the comfort of your Jupyterlab notebook. 

## Privacy & Security

[FATE](https://github.com/FederatedAI/FATE) - a project initiated by Webank's AI Department to provide a secure computing framework to support the federated AI ecosystem. It implements secure computation protocols based on homomorphic encryption and multi-party computation (MPC). It supports federated learning architectures and secure computation of various machine learning algorithms, including logistic regression, tree-based algorithms, deep learning and transfer learning.

Definition of federated learning from [Wikipedia](https://en.wikipedia.org/wiki/Federated_learning):

> Federated learning (aka collaborative learning) is a machine learning technique that trains an algorithm across multiple decentralized edge devices or servers holding local data samples, without exchanging their data samples. This approach stands in contrast to traditional centralized machine learning techniques where all data samples are uploaded to one server, as well as to more classical decentralized approaches which assume that local data samples are identically distributed.

> Federated learning enables multiple actors to build a common, robust machine learning model without sharing data, thus addressing critical issues such as data privacy, data security, data access rights and access to heterogeneous data. Its applications are spread over a number of industries including defense, telecommunications, IoT, or pharmaceutics. 



## NOT PYTHON

* [Flyte](https://github.com/lyft/flyte) - a container-native, type-safe workflow and pipelines platform optimized for large scale processing and machine learning written in Golang. Workflows can be written in any language, with out of the box support for Python.

