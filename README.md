# Binary-Classification
developing a machine learning model using the training set that performs well on the validation set.

----

## Thoughts on dataset

the training dataset was imbalanced and had 3210 duplicated rows (all of them class labeled "yes."). there are also duplicated columns (but different in [scale - data type]) such as ["variable 14" and "variable 17"] , ["variable 4" and "variable 5"] and ["variable 19" and "classLabel"]. some categorical columns such as "variable 5", "variable 6" and "variable 7" have more categories in the training set than in the validation set.""there is no "variable 16" ?!"". at first i was inclined to drop columns with high "NAN" precentage such as "variable 18" and high cordinality columns such as "variable 6" but keeping them helps the preformance of the model. 

----

## Approach

using columntransformer and pipeline to handle missing data and onehotencode categorical columns. I droped all the rows with the additional category in "variable 6", "variable 7" and "variable 5". and i also droped columns "variable 17" , "variable 4" and "variable 19". I've tried using dimensionality reduction algorithm like Principal Component Analysis (PCA) and an undersampling algorithm (Tomek Links).

----

## Algorithms Comparison

| model                  	| parameters                                	| accuracy 	| precision | f1_score 	|
|------------------------	|-------------------------------------------	|----------	|-------|-------------	|
| KNeighborsClassifier   	| Apply PCA(n_components = 11)              	| 0.865    	| 0.82 	| 0.85 	|
| XGBClassifier          	| learning_rate = 0.02,booster = "gblinear" 	| 0.89     	| 0.88 	| 0.88 	|
| RandomForestClassifier 	| n_estimators = 10                         	| 0.88     	| 0.85  | 0.87 	| 
| SVC                    	| -                                         	| 0.86     	| 0.80  | 0.86 	|
| LogisticRegression     	| Applying PCA(n_components = 14)           	| 0.875    	| 0.80  | 0.87	|
| DecisionTreeClassifier 	| Applying PCA(n_components = 7)            	| 0.81     	| 0.81  | 0.80 	| 
| LGBMClassifier         	| learning_rate = 0.11, class_weight={0:4,1:1}                      	| 0.90    	| 0.87  | 0.89 	| 
