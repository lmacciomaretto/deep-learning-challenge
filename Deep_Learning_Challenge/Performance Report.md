**Performance Report**

**Overview of the Analysis:**
The nonprofit foundation, Alphabet Soup, aimed to enhance its funding allocation process by developing a binary classifier to predict the success of applicants' ventures. 
The analysis focused on creating a model capable of determining whether applicants would effectively utilize funds granted by Alphabet Soup. 
The dataset provided contained information from over 34,000 funded organizations, encompassing various metadata attributes, such as:

EIN and NAME: Identification columns
APPLICATION_TYPE: Alphabet Soup application type
AFFILIATION: Affiliated sector of industry
CLASSIFICATION: Government organization classification
USE_CASE: Intended use case for funding
ORGANIZATION: Type of organization
STATUS: Active status of the organization
INCOME_AMT: Classification of organization's income
SPECIAL_CONSIDERATIONS: Special considerations for the application
ASK_AMT: Funding amount requested
IS_SUCCESSFUL: Indicator of effective fund utilization


**Results: 
Data Preprocessing**
The target variable selected for the model was "IS_SUCCESSFUL," representing a binary outcome indicating whether the funds were effectively utilized. 
The features used for the model included:
"APPLICATION_TYPE"
"AFFILIATION" 
"CLASSIFICATION" 
"USE_CASE" 
"ORGANIZATION" 
"STATUS" 
"INCOME_AMT" 
"SPECIAL_CONSIDERATIONS"
"ASK_AMT"

Initially, "EIN" and "NAME" columns were excluded due to their perceived irrelevance. 
However, during model refinement, the "NAME" category was reintroduced to explore whether multiple applications from the same entity and prior funding influenced the chances of subsequent funding.


Key data preprocessing steps included:

* Grouping "APPLICATION_TYPE" into 9 categories, with the "Other" category for less frequent entries.
* Reducing "CLASSIFICATION" to 6 categories, with the "Other" category for less common classifications.
* Introducing new binned categories: "ASK_AMT_Bins" indicating amounts greater than or equal to $5000
                                     "TIMES_APPLIED" indicating the number of times an applicant had been funded.

Other preprocessing steps included converting columns into dummy variables, scaling, and splitting the dataset into training and testing sets.

Compiling, Training, and Evaluating the Model

> **First Attempt at Model Creation:**

> Neural Network Architecture: 
* Activation Layer with 8 neurons (ReLU activation)
* 1 Hidden Layer with 5 neurons (all using ReLU activation)
* Output Layer with 1 neuron (sigmoid activation).
> Initial accuracy after compiling, fitting, and training with 100 epochs was approximately 73.13%, dropping to 72.42% on test data evaluation.

![First_NN_result](https://github.com/lmacciomaretto/deep-learning-challenge/assets/126762600/4cbedb54-da1a-429d-b862-99fe4b9299ea)


> **Second Attempt:**
*The second model incorporated additional preprocessing steps introduced in the first attempt, such as binning "ASK_AMT" and reintroducing the "NAME" column.
*Architecture remained the same as the first attempt.
> Accuracy improved, reaching 74.80% after training, but decreased to 74.53% on test data.

![Second_NN_result](https://github.com/lmacciomaretto/deep-learning-challenge/assets/126762600/2b643c02-0109-489d-a154-d00501d5790f)


> **Third Attempt:**

The third model retained the preprocessing enhancements of the second attempt and introduced a more complex neural network architecture.

Neural Network Architecture:
Activation Layer with 10 neurons, 2 Hidden Layers with 10 neurons each (all using ReLU activation), and an Output Layer with 1 neuron (sigmoid activation).
Accuracy surpassed 75.27% after training, with only a slight improvement to 74.60% on test data.
![Third_NN_result](https://github.com/lmacciomaretto/deep-learning-challenge/assets/126762600/144f09c4-2171-4392-9acb-acc8b57bec1e)
![ThirdNN_Accuracy_Loss](https://github.com/lmacciomaretto/deep-learning-challenge/assets/126762600/c5be6906-45b8-432e-a9a4-2eeeede34a92)

> **Final Attempt - Keras-Tuner Experimentation:**
A Keras-Tuner was employed to identify an optimal model architecture. 
The final model configuration included:
* Activation Layer with 9 neurons (ReLU activation)
* 4 Hidden Layers with 1, 9, 3, and 7 neurons, respectively (all using ReLU activation)
* Output Layer with 1 neuron (sigmoid activation)
Accuracy was 73.94% after training, with the test data having 73.72%.

![Uploading Final_NN_result.png…]()
![Final_Accuracy_Loss](https://github.com/lmacciomaretto/deep-learning-challenge/assets/126762600/d1cc8b13-57de-48fa-b390-e058955fca0f)

**Summary:**

In summary, the analysis of neural network models revealed incremental improvements in accuracy through various preprocessing and architecture adjustments. 
Despite achieving the target accuracy of 75% on training data, performance degradation was observed on the test data. This suggests potential overfitting or limitations in the current approach.


> Recommendation for an alternative Model:

Given the observed limitations, a different approach could involve employing ensemble techniques, such as Random Forest, Gradient Boosting, or XGBoost. 
These methods have shown robust performance in classification tasks and are less prone to overfitting. 
Additionally, ensembling different models could leverage their individual strengths and mitigate their weaknesses, leading to enhanced predictive power.

By combining the predictions of several models, an ensemble approach can achieve better accuracy and reduce the risk of overfitting compared to single neural network models.

In conclusion, exploring ensemble techniques could offer a promising avenue for enhancing the predictive performance of the model and achieving the desired accuracy threshold on both training and test data.




