---
layout: post
title:  "Machine Learning using CASP dataset"
date:   2021-02-06 12:27:32 +0530
categories: jekyll update
permalink: "ml-casp"
---


**Machine Learning for prediction of the RMSD (Root Mean Square Deviation) of a decoy set using Physicochemical Properties of Protein Tertiary Structure Data Set**

The workflow followed here is adapted from the book [Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow](https://g.co/kgs/bvvihi) by **Aurélien Geron**.

**Scope of this work** : To layout the Machine Learning workflow from start to end. 

**Target Audience** : This piece of work is intended for someone with minimal knowledge in machine learning practices. This is not a tutorial for an absolute beginner.

**Requirements** : ScikitLearn, Numpy, Matplotlib and Pandas (see attached `requirements.txt` file for the complete list)

*The dataset is downloaded from this link [Physicochemical Properties of Protein Tertiary Structure Data Set](https://archive.ics.uci.edu/ml/datasets/Physicochemical+Properties+of+Protein+Tertiary+Structure).* 

*This notebook is divided into two sections:*
1. **Data preprocessing** *- Explore the dataset and prepare it before regression*
2. **Model selection, training and fine tuning** *- Try with various models, compare their performance and fine tune them*

<table>
  <td>
    <a target="_blank" href="https://colab.research.google.com/github/aniket-cfd/Machine-Learning-CASP-Dataset/blob/master/Machine%20Learning%20for%20the%20prediction%20of%20Protein%20Structure.ipynb"><img src="https://www.tensorflow.org/images/colab_logo_32px.png" />Run in Google Colab</a>
  </td>
  <td>
    <a target="_blank" href="https://nbviewer.jupyter.org/github/aniket-cfd/Machine-Learning-CASP-Dataset/blob/master/Machine%20Learning%20for%20the%20prediction%20of%20Protein%20Structure.ipynb"><img src="https://nbviewer.jupyter.org/static/img/nav_logo.svg" width=100 height = 100/>Open with nbviewer</a>
  </td>
</table>


Steps followed in this work:
* Data Preprocessing:
    * Data visualization - Correlations plots, Bar charts etc.
    * Train test split - Stratified Sampling
    * Scaling - Standard scaling
    * Dimensionality Reduction - PCA with 99% explained variance 
* Model Selection:
    * Linear Model 
    * Random Forest Regressor
    * Artificial Neural Networks
    * GridSearch for better hyperparameters selection
 
Comparison of accuracy of the models that were fit:

|Model |Mean RMSE score|Wall Times|
|------|:---------:|-----------:|
|Linear Model| 5.1| 8 [ms]
|Random Forest Regressor | 3.8| 19 [s]
|Artificial Neural Network (ANN) | 4.2| 29 [s]

At this point, we can conclude the following:
* The Linear Regression model is very fast to compute but suffers from low accuracy
* Random Forest Regressor and Artifical Neural Network (ANN) both perform better than Linear Regression model and one of these should be chosen as a suitable model
* The specific model to be chosen for this is a tradeoff between:
     * Speed of prediction **vs** Accuracy
     * Computational resources available at prediction stage **vs** model complexity
     * Model updation considerations
     * Explainability of Random Forest Model **vs** black-box ANN model
* We need to adapt the decision based on more information about the deployment platform