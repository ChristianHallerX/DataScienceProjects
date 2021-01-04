# BP Reservoir Permeability -- Measurements on rock samples for rock permeability

For a description of the data set used for this project, please read the introduction in the main file "BP_Reservoir_Permeability_WatsonStudio.ipynb"

For the project the following applications were used:
Processing in IBM Watson Studio Jupyter Notebook (Python 3) and on my home PC with 
the Anaconda JupyterLab Notebook (Python 3). The Machine Learning algorithms provided by SciKit-Learn are computed in-memory on Watson Studio are
quick enough on the 1 CPU instance provided with the free tier IBM Cloud. 
A simple Neural Network was trtrained on Keras on GPU and could also be trained on Apache 
Spark servers. Keras CPU training is not recommendable, since it can be very slow even with multiple CPU cores. A Linear 
Regression model was run on SystemML and Apache Spark in a separate notebook.
- An Architectural Design Document (ADD) outlining project decisions.
- An ETL notebook was created (ETL.ipynb) at start of the project and some initial dataset exploration. More detailed analyses are presented in the main file.
- A SystemML notebook
- A MS Power Point presentation with a brief summary is part of this project. 
- A Youtube video about the analysis can be seen here: https://youtu.be/KxkD8paGVYs

The following Python libraries were used:
1. NumPy (scientific data manipulation)
2. Pandas (MS Excel-like data frames)
3. MatPlotLib (graphing)
4. Seaborn (high-level graphing)
5. SciKit-learn (in-memory Machine Learning)
6. Keras (in-memory GPU/CPU Deep Learning)
7. SystemML (Distributed Machine Learning and Deep Learning with Apache Spark)


# Models:

### SystemML (LinearRegression):
SystemML framework demonstration on Watson Studio with Spark. No features were dropped and no feature scaling was applied.

| | Algorithm | R2 score |
|---|---|---|
| 1 | LinearRegression | 0.704 |




### SciKit-Learn (multiple algorithms):
No features were dropped to run this model. The target vector Permeability has a much larger maximum value than the input
features. The SciKit-Learn StandardScaler was used to bring all data means around 0, which improved results significantly.
Since the data set contains only 48 samples, no permanent train-test split was conducted. All Machine Learning algorithms were
run with a CrossValidation ("CV") that used multiple folds. The optimal CVfold number and some algorithm-specific parameters were
found with loops. The CV scores were determined by taking the arithmetic mean of all CV runs.The best scoring run was re-run
and the predicted Permeability values graphically compared with the actual Permeability.

| |Algorithm |	R2 mean_score |
|---|---|---|
| 1 |	Support Vector Regression |	0.525 |
| 2 |	Decision Tree Regressor |	0.428 |
| 3 |	K-Nearest Neighbor Regressor |	0.419 |
| 4 |	Linear Regression |	0.401 |
| 5 |	Random Forest Regressor |	0.262 |
| 6 |	Gradient Boosting Regressor |	0.242 |





### Keras (Deep Learning):
Regression model with single hidden layer and droput ran over 4 CV and the mean MSE was reported.
The best of the four CV models was used to make predictions. A scatter plot compares actual Permeability with modeled Permeability.
The best model was also saved as file and deployed on IBM Cloud ML. Predictions can be made with the API in the notebook.

| | Algorithm | CV MSE |
|---|---|---|
| 1 | Deep Learning | 15.13 (+/-3.37) |

