# Some cool open-source Python packages for Machine Learning EP 3

![moebius](moebius2.jpg)

There is a very rich ecosystem of Python libraries related to ML. Here is a list of some “active”, open-source packages that may be useful for ML day-to-day activities.

This post is following these ones:

* [Some cool open-source Python packages for Machine Learning EP 1](https://aetperf.github.io/2019/07/11/Some-cool-open-source-Python-packages-for-Machine-Learning.html) (2019/07/11)
* [Some cool open-source Python packages for Machine Learning EP 2](https://aetperf.github.io/2019/08/08/Some-cool-open-source-Python-packages-for-Machine-Learning-Ep-2.html) (2019/08/08)


(☞ﾟヮﾟ)☞

## Feature engineering

* [category_encoders](https://github.com/scikit-learn-contrib/categorical-encoding/) - a set of scikit-learn-style transformers for encoding categorical variables into numeric by means of different techniques.

## Time series

* [TSFRESH](https://github.com/blue-yonder/tsfresh) - automatically extracts 100s of features from time series. Those features describe basic characteristics of the time series such as the number of peaks, the average or maximal value or more complex features such as the time reversal symmetry statistic. To avoid extracting irrelevant features, the TSFRESH package has a built-in filtering procedure. This filtering procedure evaluates the explaining power and importance of each characteristic for the regression or classification tasks at hand.

## Auto-ML

* [Hyperopt](https://github.com/hyperopt/hyperopt) - a library for serial and parallel optimization over awkward search spaces, which may include real-valued, discrete, and conditional dimensions.
* [ray[tune]](https://github.com/ray-project/ray) - a library for hyperparameter tuning at any scale.

## Experimentation frameworks and tools

* [Ax](https://github.com/facebook/Ax) - an accessible, general-purpose platform for understanding, managing, deploying, and automating adaptive experiments.