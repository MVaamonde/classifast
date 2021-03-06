![alt text](https://image.ibb.co/nHb3Jd/Screenshot_from_2018_07_18_20_52_59.png)

The R package `classifast` is a side project that my friend [Manuel](https://github.com/MVaamonde "Manuel's GitHub profile") and I are starting. Basicaly, the main goal is to make a function that, given multivariate labeled data, gives you a quick overview of which classifiers are the best for your problem (based on several error criterious).

This minimal package is intended to be a project to both enhance our R skills and to make (hopefully) a usefull tool for Data Scientists. All help and feedback will be highly appreciated, so feel free to contact me on <richyrecarey@gmail.com> to get involved in the project.

## Instalation

`instal.packages(devtools)` <br />
`devtools::install_github("Richyrecarey/classifast")` <br />



## Usage

Given multivariate data in a matrix-like objet `x` (rows are observations, columns are variables) and its correct labels in a vector-like object `y`, the main function `classifast(x, y, method)` will train the desired statistical classifiers selected in the string vector `method`. Several options are:


* `method = "log"`: It will train binary or multinomial logistic regression, as needed. <br />
* `method = "svm"`: It will train Radial SVM. <br />
* `method = "knn"`: It will train the knn algorithm. <br />
* `method = "RandomForest"`: It will train Random Forest. <br />
* `method = "simple"`: It's the same as `method = c("log", "svm", "knn", "RandomForest)` <br />
* More methods are under development <br />


All the options and parameters available to tweak are available at `help(classifast)`.


Once trained, `classifast()` will return an object of class `classifast`, which has several methods implemented:

### summary.classifast()

```R
# Train several classifiers on the Iris dataset
output <- classifast(x = iris[-5], y = iris[5], method = "simple")

# Show retults of chosen methods
summary(output)
```
And the output should look somehow like this:

```
 k-fold accuracy was approximated using 10-fold validation 
 
 Accuracy (%) of the diferent methods used: 
 
        Method     kf %   Test % Train %
1          log    96.66    92.45     100
2          svm    65.92    62.54    99.7
3          knn    75.51    72.54    94.3
4 RandomForest    84.72    82.54    92.4

```


### predict.classifast()

Still developing




