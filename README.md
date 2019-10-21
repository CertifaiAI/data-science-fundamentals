# Machine Learning Fundamentals Lab
This repository contains jupyter notebooks used for training during the hands-on session.
## Contents

- [1-0_Linear Algebra](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/01-0_Linear%20Algebra.ipynb):
  Create matrics and apply mathematical operations on it.
- [2-0_Data Exploration and Data Transformation](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/02-0_Data%20Exploration%20and%20Data%20Transformation.ipynb):
  Explore a dataset and perform data visualization and data transformation.
- [3-0 Feature Scaling](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/03-0_Feature%20Scaling.ipynb):
  Perform feature scaling.
- [4-0_Linear Regression 1](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/04-0_Linear%20Regression%201.ipynb):
  Predict the house price by using Linear Regression.
- [4-1_Linear Regression 2](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/04-1_Linear%20Regression%202.ipynb):
  Predict the stock price by using Linear Regression.  
- [5-0_Logistic Regression ](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/05-0_Logistic%20Regression.ipynb):
  Perform Binary Classification by using Logistic Regression.
- [6-0_Support Vector Machines (SVM) ](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/06-0_Support%20Vector%20Machines(SVM).ipynb):
  Perform Multiclass Classification by using Support Vector Machines (SVM).
- [7-0_Decision Tree and Random Forest ](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/07-0_Decision%20Tree%20and%20Random%20Forest.ipynb):
  Perform Multiclass Classification by using Decision Tree and Random Forest.
- [8-0_K Nearest Neighbour (KNN) ](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/08-0_K%20Nearest%20Neighbour(KNN).ipynb):
  Perform Multiclass Classification by using K Nearest Neighbour.
- [9-0_K Means Clustering 1](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/09-0_K%20Means%20Clustering%201.ipynb):
  Perform Unsupervised Clustering by using K Means Clustering.
- [9-1_K Means Clustering 2](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/09-1_K%20Means%20Clustering%202%20.ipynb):
  Use K Means Clustering to reduce colour space of an image.
- [10-0_Principal Component Analysis (PCA)](https://github.com/skymindglobal/machine-learning-fundamentals/blob/master/solution/10-0_Principal%20Component%20Analysis%20(PCA).ipynb):
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

Go out by 
```sh
conda deactivate
```

### Installation on Windows 10
If you do not have python on your machine, download <b>miniconda</b> from [here](https://docs.conda.io/en/latest/miniconda.html).

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
At Windows command prompt or Anaconda Prompt, launch jupyter notebook by 
```sh
jupyter notebook
```

and go to the directory where you have downloaded this repository.


OR directly open Jupyter notebook server at the PATH with the downloaded repository by 
```sh
jupyter notebook <YOUR-PATH-DOWNLOADED-REPOSITORY>
```
