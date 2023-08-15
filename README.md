# deep-learning-challenge
This is the repo for Assignment #21 Deep Learning Challenge

Performance Report

Overview of the analysis:
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. The purpose of this analysis is to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup. The CSV file provided contains data from more than 34,000 organizations that have received funding from Alphabet Soup over the years and captures metadata about each organization, such as:

EIN and NAME—Identification columns
APPLICATION_TYPE—Alphabet Soup application type
AFFILIATION—Affiliated sector of industry
CLASSIFICATION—Government organization classification
USE_CASE—Use case for funding
ORGANIZATION—Organization type
STATUS—Active status
INCOME_AMT—Income classification
SPECIAL_CONSIDERATIONS—Special considerations for application
ASK_AMT—Funding amount requested
IS_SUCCESSFUL—Was the money used effectively

Results: 
Data Preprocessing

The variable chosen as the target for the model is the columns "IS_SUCCESSFUL". It is a binary variable that, based on the features, would be able to predict if the applicant will make effective use of the money received.

The feature variable for the model were:
"APPLICATION_TYPE", "AFFILIATION", "CLASSIFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS" and "ASK_AMT".

Initially, both "EIN" and "NAME" columns were removed since those were considered innecesary identification variables. However, after the first attempts at improving the model, the category "NAME" was considered again, to understand if applicants had filed several applications, and if being granted funding before increases the chances of being funded again.

As per data pre-processing steps:
* The "APPLICATION_TYPE" column was reduced to 9 categories (T3, T4, T5, T6, T7, T8, T10, T19 and Other). 'Other' compiles the application types that have less than 200 entries.
* The "CLASSIFICATION" column was was reduced to 6 categories (C1000, C1200, C2000, C2100, C3000 and Other). 'Other' compiles the classification categories that have less than 1000 entries.
* For the late attempts, category "NAME" and "ASK_AMT" were replaced by a new binning category:
> "ASK_AMT" was replaced by "ASK_AMT_Bins", that indicates whether the money amount was 5000 or over 5000.
> "NAME" was replaced by "TIMES_APPLIED", that indicates how many times the applicant has been granted funding: "First time", "2-4" (times), "5-9" (times), "10-99" (times), "Over 100" (times).

* All columns were transformed into dummy variables and scaled.
* Dataset was split into training and testing sets.

Compiling, Training, and Evaluating the Model
First attempt at creating the model: 
* Neural Networks with an Activation Layer of 8 neurons
* 1 Hidden Layer with 5 neurons. All 13 neurons used ReLU as activation function.
* 1 Output Layer with 1 neuron and sigmoid activation function.

This first attempt was arbitrarily selected to have an approximate idea of how the model does without too much intervention other than pre-processing.
For this attemp, "EIN" and "NAME" were dropped, and "ASK_AMT" was not binned.
After compiling, fitting and training with 100 epochs, accuracy was above 73%. When evaluated with the test data, accuracy went down to 72%.

(Paste first NN)

Since our target performance was 75%, several steps were taken to improve the model:
* Binned "ASK_AMT" into "5000" and "Over 5000"
* Incorporated the column "NAME", and binned it according to the times that same applicant filed applications. 

This second attempt used the same schema than the first attemp, to evaluate if this further pre-processing improved the model.
* Neural Networks with an Activation Layer of 8 neurons
* 1 Hidden Layer with 5 neurons. All 13 neurons used ReLU as activation function.
* 1 Output Layer with 1 neuron and sigmoid activation function.
After compiling, fitting and training with 100 epochs, accuracy was above 75%. When evaluated with the test data, accuracy went down to 74%.

(Paste second NN)

For the third attempt, same pre-processing as second attempt was used, but more layers and neurons were added:
* Neural Networks with an Activation Layer of 10 neurons
* 2 Hidden Layer with 10 neurons each. All 30 neurons used ReLU as activation function.
* 1 Output Layer with 1 neuron and sigmoid activation function.
After complling, fitting and training with 100 epochs, accuracy was above 75%. When evaluated with the test data, accuracy went down to 74%, slightly improving from the second attempt.

(Paste third NN)

Finally, a Keras-tuner was run to determine the best model for this data set:
(Paste Keras tuner)

For this last attempt, the layers and neurons were modified as follows:
* Neural Networks with an Activation Layer of 9 neurons
* 4 Hidden Layers with 1, 9, 3 an 7 neurons, respectively. All 29 neurons used ReLU as activation function.
* 1 Output Layer with 1 neuron and sigmoid activation function.


Summary: 
Overall, the evaluation of the neural networks model shows that ... However, the algorithm had some trouoble learning Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.