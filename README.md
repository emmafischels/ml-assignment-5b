# ML Assignment 5B: Machine Learning in R 

Author: Emma Fischels 
Tutorial Followed: https://machinelearningmastery.com/machine-learning-in-r-step-by-step/

## Project Overview 

This project implements a complete machine learning workflow in R using the Iris.csv dataset. This project follows Jason Brownlee's Your First Machine Learning Project in R Step-by-Step tutorial while accounting for updates for current versions of R and the caret package. 

## Repository Components 
.
├── README.md
├── environment.yml
├── ml_assignment_5b.ipynb
└── .gitignore

## Methods 

1. Installing the R platform.
2. Loading the dataset.
3. Summarizing the dataset.
4. Visualizing the dataset.
5. Evaluating some algorithms.
6. Making some predictions.

## Software Requirements 

This project uses a Conda environment defined in environment.yml 

1. Create the environment: conda env create -f environment.yml
2. Activate the environment: conda activate ml-assignment-5b
3. Register the R kernel (first-time setup only): R -e "IRkernel::installspec(name='ml-assignment-5', displayname='R (ML Assignment 5B)')"
4. Launch Jupyter: jupyter lab

## Dataset 
The dataset contains 150 observations from three Iris species:

* Iris setosa
* Iris versicolor
* Iris virginica

Each observation includes four predictor variables:

* Sepal Length
* Sepal Width
* Petal Length
* Petal Width

## Results 
Several supervised learning algorithms were trained and compared using 10-fold cross-validation. The best-performing model was then evaluated on a held-out testing dataset using standard classification metrics to assess predictive performance.
