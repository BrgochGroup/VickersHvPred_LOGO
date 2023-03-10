# Vickers Hardness Prediction LOGO (Leave One Group Out)

The code is packaged for a general user (requires Jupyter Notebook). The Jupyter Notebook (Pred_Hv_LOGO.ipynb) is designed to to predict load dependent Vickers hardness. 

The trained model will predict the hardness of materials based on 141 composition-only descriptors. To optimize the model, the user should tune the hyperparameters and prune less important features (see below). This will allow the user to optimize the trained model based on their specific training dataset. 

- [GridSeachCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)
- [RFE](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFE.html)


*IMPORTANT* To use the code, the entire repo (with all files) should be in your working folder. 


## Model Overview

To train the model and predict hardness, follow these steps:

### 1. Generate descriptors

First, prepare your compositions in an excel file, and name it `pred_hv_comp.xlsx`. The first column of the `pred_hv_comp.xlsx` file should be named as `Composition`.


The code will generate an output file named `pred_hv_descriptors.xlsx` containing all compositional descriptors.


*IMPORTANT STEP:* manually add a new column at the end of the descriptor file you just generated with the desired load value (unit: N). Predicting the hardness of the same material at different loads (i.e. 0.49 N and 4.9 N) would require two instances in `pred_hv_comp.xlsx` 


### 2. Train the model and make prediction of your compounds

The training dataset is provided in the file `hv_comp_load.xlsx` where you will find chemical compositions, hardness values, and corresponding load values. The training process of our model will be automatically done when you run the prediction script

Results will be stored in a file named `predicted_hv.xlsx`. Basically the script will first train the model using the dataset we constructed, then read the `pred_hv_descriptors.xlsx` file you just generated and give you the predicted hardness at any load value you would be interested in.


## Citations

To cite, please reference the following work:

Hickey, J. C. and Brgoch. J, The Limits of Proxy-Guided Superhard Materials Screening, Chem. Mater. 2022, 34, 10003-10010.

##  Prerequisites

- [pymatgen](http://pymatgen.org)
- [XGBoost](https://xgboost.readthedocs.io/en/latest/#)
- [scikit-learn](http://scikit-learn.org/stable/)
- [pandas](https://pandas.pydata.org/pandas-docs/stable/index.html)
- [NumPy](https://docs.scipy.org/doc/numpy/index.html)
- [xlrd](https://xlrd.readthedocs.io/en/latest/index.html)
- [LeaveOneGroupOut](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.LeaveOneGroupOut.html)


For any questions or comments on this work, please contact the Brgoch Group at the University of Houston (jbrgoch@central.uh.edu).
