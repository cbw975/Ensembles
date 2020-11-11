# Ensembles
Uses k-fold cross-validation to compare the performance of at three classification models, defined with pipelines, and an ensemble that is composed of those models. Then trains all of the individual models and the ensemble on the full training set, and assesses the performance of the trained models and the ensemble on the testing set.

## Dataset Info
This is a dataset that consists of various features of NASA confirmed planets. The pertinent ones are:
* Orbital Period [days]
* Planet Mass or M*sin(i) [Jupiter mass]

#### Source
Data was produced by the NASA Exoplanet Archive: http://exoplanetarchive.ipac.caltech.edu
* Confirmed planets --> https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=planets
* Downloaded the table as a CSV file --> My file name: planets_2020.09.03_20.35.38.csv
* BUT, for ease of filename usage, I renamed to: planets090320.csv

## Purpose
The purpose in studying this dataset is to classify and compare planetary systems, specifically with regards to their quantitative properties. Plotting these properties can provide insight on the interactions and correlations between them. 

We do this by training an Support Vector Machine (SVM), Decision tree, and K-Nearest-Neighbors (KNN) model to classify between Jupiter-mass planets (class J) and Earth-mass planets (class E) based on mass and orbital period. Our ensemble method is majority voting. A (majority) voting ensemble is an ensemble ML model that combines predictions from multiple other models. For classification, the predictions for each label are summed and the label with majority vote is predicted.
- SVM: a set of supervised learning methods used for classification (here), regression and outliers detection
    - Feature Transformer(s): standard scaling - standardize features by removing the mean and scaling to unit variance
- Decision tree: non-parametric supervised learning method used for classification and regression. The goal is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the data features
- KNN: stores all available cases and classifies new cases based on a similarity measure (e.g., distance functions)
    - Feature Transformer(s): standard scaling - standardize features by removing the mean and scaling to unit variance

We will compare the performance of the different models in their classification of these planets. This can be an important task because of the different properties, compositions, behaviors, etc. of different classes of planets. This has effects on their motion, aging, reactions (chemical, atmospheric, etc), interactions with space and bodies around them, etc. Our very understanding of the universe can be based on our studies of the different celestial bodies. 

## Helpful Background Info / Assumptions
* (EXCLUDED) Super-Jupiters: planets of approx 2-13 M_J mass range
* Mid-Jupiters: planets of approx 0.5-2 M_J mass range
* (EXCLUDED) Sub-Jupiters: planets of approx 0.1-0.5 M_J mass range
* Super-/Mid-/Sub-Earths and Earthy-midplanets: 0.01-30 M_E = approx (3.14657534e-5)-0.100690411 M_J mass range

<!-- 0.0314657534 -->
#### Here, we exclude Super-Jupiters and Sub-Jupiters, to even out the proportion of data for Jupiter vs Earth class planets (deviating a bit from their exact definitions due to lower-mass sub-jupiters being terrestrial). We consider Jupiter class planets to have 0.5 < M < 2 and Earth class planets to have M < 0.25

Source: https://planetstar.fandom.com/wiki/Planetary_classification#:~:text=There%20are%20three%20broad%20types,in%20order%20of%20decreasing%20mass
