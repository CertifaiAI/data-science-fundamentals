# Machine Learning Fundamentals Lab
This repository contains Jupyter notebooks used for training during the hands-on session.
## Contents

- [01-0_NumPy Quickstart.ipynb](solution/01-0_NumPy%20Quickstart.ipynb):
  Create matrics and apply mathematical operations on it.
- [01-1_Linear Algebra with NumPy.ipynb](solution/01-1_Linear%20Algebra%20with%20NumPy.ipynb)
  Discussion of basic matrix operations and Gaussian elimination. 
- [01-2_Statistics and Probability.ipynb](solution/01-2_Statistics%20and%20Probability.ipynb)
  Fundamentals of probability, probability distributions, Bayes' theorem and the Central Limit Theorem.
- [02-0_Data Exploration and Data Transformation](solution/02-0_Data%20Exploration%20and%20Data%20Transformation.ipynb):
  Explore a dataset and perform data visualization and data transformation.
- [03-0 Feature Scaling](solution/03-0_Feature%20Scaling.ipynb):
  Perform feature scaling.
- [04-0_Linear Regression 1](solution/04-0_Linear%20Regression%201.ipynb):
  Predict the house price by using Linear Regression.
- [04-1_Linear Regression 2](solution/04-1_Linear%20Regression%202.ipynb):
  Predict the stock price by using Linear Regression.  
- [05-0_Logistic Regression ](solution/05-0_Logistic%20Regression.ipynb):
  Perform Binary Classification by using Logistic Regression.
- [06-0_Support Vector Machines (SVM) ](solution/06-0_Support%20Vector%20Machines(SVM).ipynb):
  Perform Multiclass Classification by using Support Vector Machines (SVM).
- [07-0_Decision Tree and Random Forest ](solution/07-0_Decision%20Tree%20and%20Random%20Forest.ipynb):
  Perform Multiclass Classification by using Decision Tree and Random Forest.
- [08-0_K Nearest Neighbour (KNN) ](solution/08-0_K%20Nearest%20Neighbour(KNN).ipynb):
  Perform Multiclass Classification by using K-Nearest Neighbours.
- [09-0_K Means Clustering 1](solution/09-0_K%20Means%20Clustering%201.ipynb):
  Perform Unsupervised Clustering by using K-Means Clustering.
- [09-1_K Means Clustering 2](solution/09-1_K%20Means%20Clustering%202%20.ipynb):
  Use K Means Clustering to reduce colour space of an image.
- [10-0_Principal Component Analysis (PCA)](solution/10-0_Principal%20Component%20Analysis%20(PCA).ipynb):
  Perform Dimension Reduction and Data visualization by using Principal Component Analysis (PCA).

## Dependencies
### Preferred kernel and IDE
<b>Python 3.7.3</b> or newer and <b>Jupyter Notebook</b>

If you already have Anaconda, you can create a new virtual environment with Python 3.7.3 by and name your environment name
```sh
conda create --name <REPLACE-NAME> -y
```

Go into your newly created python3.7.3 environment by
```sh
conda activate <REPLACE-NAME>
```

Deactivate the newly created environment using 
```sh
conda deactivate
```

### Installation on Windows 10
If you do not have Python on your machine, download <b>miniconda</b> from [here](https://docs.conda.io/en/latest/miniconda.html).

After installing miniconda, install the required python modules required for this hands-on session.
```sh
conda install --file requirements.txt -y
```

If you already have python on your machine, try installing the python modules and proceed only if all modules are installed successfully.
```sh
python -m pip install --r requirements.txt
```

All modules will be installed successfully except OpenCV installation will fail. Install manually using
```sh
python -m pip install opencv-python==3.4.2.16
```

### Getting started
In Anaconda Prompt (Windows systems) or your system terminal (non-Windows systems), launch Jupyter Notebook by 
```sh
jupyter notebook
```

and go to the directory where you have downloaded this repository.


OR directly open Jupyter notebook server at the PATH with the downloaded repository by 
```sh
jupyter notebook <YOUR-PATH-DOWNLOADED-REPOSITORY>
```
