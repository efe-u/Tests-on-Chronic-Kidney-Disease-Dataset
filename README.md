# An Overview of Techniques to Detect Chronic Kidney Disease 
#1. Introduction#

This text is an overview of the compilation of my works on the Chronic Kidney Disease dataset. The CKD dataset consists of 400 patient entries from which 200 of them are victims of chronic kidney disease (ckd), and the other half is not. Using the data given, my aim is to test different alternatives of classification techniques. This will provide an overview of the chosen techniques results and an output open for comparison of the results. 


#2. Data Extraction & Processing#

In this project, the only dataset that was used was the Chronic Kidney Disease dataset. This dataset includes 400 patients’ entries and their 25 attributes which may help diagnose the patient with CKD. 

2.1. Data Cleaning

The CKD dataset is overall utilizable; although, for my own purposes, it still needs to be altered. The first attribute of each patient entry is their “ID”. This id distinguishes every patient and contrasts with my intended usage of model training as the dataset will be used for training and testing the model. In the case that the id column attribute isn’t dropped, the model may utilize the id to directly present a diagnosis with pinpoint accuracy; although, given a new patient to diagnose outside the dataset, the model will then fail. Therefore, the “ID” column is dropped, and the remaining 24 attributes are utilized. 

2.2. Data Scaling

From all 24 attributes, not all are utilizable in a matrix. Though still a binary indicator, most attributes are expressed in a consistent but differing string format. To utilize the data for my own purposes, which requires the data to be expressed as a matrix input, all string binary indicators are converted to binary. After this process, all 24 attributes per patient are expressed with a numeric value. To further ensure that the data is utilizable, all non-binary attributes values are min-max scaled between 0 and 1. The resulting dataset thereby has a range between 0 and 1; thereby, applicable for training.

2.3. Handling Missing Values

From all 400 patients, ~250 of them had “NaN” (missing) values. Sometimes also expressed as “?” in the dataset, all these values were filled as the amount of data was already scarce. To fill the missing values, KNN imputer was used due to observed consistencies and patterns in the missing values. Patterns in a multi-dimensional dataset were handled in accordance with the 5 nearest neighbors given a plane. 

2.4. Principal Component Analysis (PCA)

Given 24 attributes, the dataset is overall complex. As all attributes are features of patients there is no guarantee that all attributes include a pattern for diagnosis and classification. There may be irrelevant attributes which may hinder the performance of all classification techniques. Therefore, given a dataset of 24 attributes, all dimensionalities from 24 to 2 are tested using principal component analysis. PCA allows to reduce dimensionalities and all dimensionality reduced data is utilized in classification to compare dimensionality performances.


#3. Classification Techniques#

3.1. Already Existing Classification Models

First, 5 already existing classification models were used to utilize the preprocessed data. The following 5 classification models: support vector machine, logistic regression, K-Nearest Neighbor (nearest 1 and 5 neighbors tested separately), decision tree (”gini” and “entropy” tested separately), random forest; were used and evaluated for CKD diagnosis. For all of these classification models, a 80/20 train-test split was used given the 400 patient large dataset. Therefore, all classification models had 320 train, 80 test patient entries. All classification models are evaluated on all reduced dimensionalities.

3.2. Creating Classification Neural Network Models

Apart from the 5 already existing models of classification, I created 3 different neural network models. These models are named as “Type1”, “Type2”, and “Type3”. All neural network models consist of an equal size input layer, a differing hidden layer, and a singular size output layer. The types of neural network models differ in the size of their hidden layers. All three variants were trained over 10 epochs with the batch size of an epoch. Mean squared error was chosen as the loss function for the “adam” optimizer, which is an extended version of stochastic gradient descent. All three types of neural network models are evaluated on all reduced dimensionalities. Thereby, 5 already existing classification models and 3 newly created neural network models are evaluated over all reduced dimensionalities.


#4. Evaluation#

4.1. Evaluation of Already Existing Classification Models

All 5 existing classification models are evaluated by the same criteria. The criteria consists of the accuracy score, F1 score, and the recall score of the evaluated model. Cross validation score is used to evaluate all 5 types on the given criteria. Dimensionality wise, as dimensionality increases, the average CVS score increases across all models. This is an indicator that all parameters are highly correlated with and are indicators of CKD. On the other hand, the only slight increase on all scoring criteria also indicates that not every parameter is a crucial indicator as all scores remain very high and near even in high dimensionality differences. From all 5 models, all 4 other than the SVM classification model performed effectively whereas the SVM classification model lacked the same performance. The other 4 had very similar score on all 3 criteria, thereby having no definite outperformer between the 4.

4.2. Evaluation of Classification Neural Network Models

All 3 created variants of neural network models were evaluated by the same criteria. The criteria consisted of solely accuracy. The accuracy of NN models were tested on all dimensionalities. Unlike already existing classification models, the accuracy of NN models didn’t show such a visible trend across dimensionalities. For all variants, the highest scoring dimensionality differed. For “Type1” the highest scoring dimension was 18, for “Type2” 13, and for “Type3” 23. As there was only 1 hidden layer with a decreasing size among variants, the accuracy of the NN classification models were mostly incompetent compared to the already existing classification models; although, with a smaller batch size, increased size of the hidden layer, and other features that increase accuracy NN models are able to perform as accurate.  


#5. Possible Improvements#

This is a mere overview experimenting on the CKD dataset. The results provided are worthy reference points; although, they lack accuracy in comparison. The NN model can be improved greatly; although, it is warned that testing all 24 dimensionalities is already a computationally heavy task and if tried on a much more computationally demanding model training, time required to provide results will lengthen heavily. Another point to improve is the evaluation of the results of NN models and variants as I was unable to identify any visible trend among the highest scoring dimensionalities; although, that may be related to the simplicity of the NN as indicated in the first possible improvement. Related to this last possible improvement, even though the project yields results, it is hardly a user friendly comparison. It will suit the needs to compare already existing classification models, but will potentially lack in other sections.


#6. Conclusion#

This text has explained all sections and machinations of my work on the CKD dataset. The yielded results provide a comparison on many levels of complexity such as dimensionality performance comparison, model performance comparison, types of performance comparison, and more. This work provides utilizable results and a reference point for further similar work. Trends observed in the CKD dataset may be referenced in further works to determine to what degree to use PCA, or which classification model. Overall, this work on the CKD dataset is a compilation of the techniques to detect CKD which is comparable on multiple levels within its results.
