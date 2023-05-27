# Deep Learning Challenge

## Background
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special considerations for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

### Step 1: Preprocessing the Data
Starting with Google Colab, I read in the charity_data.csv and converted to a Pandas Dataframe. As directed I began by dropping the 'EIN' and 'NAME' columns. Once dropped I determined "IS_SUCCESSFUL" as our target variable, the depedent variable, and all other columns for our features, the independent variables.
<img width="713" alt="Screenshot 2023-05-27 at 10 54 19 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/c2add8bf-5600-4acd-a504-d07d071020e4">

Once removed, I reviewed the resulting dataframe and determined the number of unique values in each column.
<img width="476" alt="Screenshot 2023-05-27 at 10 56 18 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/06e336d2-1ee7-4227-af82-7eb1d54b8fef">

To further analyze I binned the data of the 'APPLICATION_TYPE' and 'CLASSIFICATION' through the following steps:
- Determined the count of different application types and classification types
- Choose a cutoff value for each instance, 'APPLICATION_TYPE' cutoff at 750 and 'CLASSIFICATION' cutoff at 1500
- Values outside of the cutoff are 'rare' and were binned in their respective columns as 'OTHER'
<img width="881" alt="Screenshot 2023-05-27 at 11 05 28 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/a2a38eed-f779-422a-8994-c492e13e1d78">
<img width="850" alt="Screenshot 2023-05-27 at 11 05 45 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/52ca6893-9b9f-4427-98e5-918e307d9828">

Once cleaned to our specifications, I used pd.get_dummies() to change our categorical variables and split the data into our features array, X, and a target array, y. Using train_test_split, I created the training and testing datasets for modeling. 
<img width="683" alt="Screenshot 2023-05-27 at 11 09 57 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/b43458a6-087a-4f7b-877a-a8f26a80f1b4">

Now split, I scaled the data using StandardScalar, fitting to the training data, and tranforming.
<img width="561" alt="Screenshot 2023-05-27 at 11 11 30 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/d369bebf-3a51-4f1c-9ed6-a6646baef0b5">

### Step 2: Compile, Train, and Evaluate the Model
I can now ceate a neural network model using our preprocessed data. To begin, I define the number of input features and nodes for each layer using keras.model with TensorFlow.
<img width="852" alt="Screenshot 2023-05-27 at 11 15 37 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/7ff0f5d0-2713-4f59-9422-81130a618d38">
I then compiled and trained the model and evaluted the model's functionality using the test data:
<img width="662" alt="Screenshot 2023-05-27 at 11 16 56 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/89de3f7a-667d-4506-82b8-bbcdd18623f0">

### Step 3: Optimize the Model
The ask is a 75% accuracy for our neural network model in this challenge in approaching this I made 3 attempts and was unable to achieve this result.
## Optimization 1
  - I made edits to my binning for 'APPLICATION_TYPE' in exploration to see if changes at this level effected results, minimal loss in accuracy was observed
  <img width="861" alt="Screenshot 2023-05-27 at 11 21 51 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/8b7ef5c0-fc01-4114-8e7f-2accfaf39b34">
  <img width="609" alt="Screenshot 2023-05-27 at 11 22 09 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/20b894a0-d524-4784-bd61-2f5fe96ee9ee">
 
## Optimization 2
  - I left my binning for 'APPLICATION_TYPE' & 'CLASSIFICATION' the same as Optimization attempt 1. I added a third hidden layer node whilde decreasing       nuerons from each node and changed my activation models for non-linear results
  <img width="793" alt="Screenshot 2023-05-27 at 11 25 30 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/335675d6-b7ea-403b-8650-e87f8ebaf2d3">
  <img width="543" alt="Screenshot 2023-05-27 at 11 30 34 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/1b3c3ac3-0bc2-41cf-9fd3-f4455c2c5b25">

## Optimization 3
  - Building off the framework of Optimization 2, in my final attempt I added a 4th hidden layer node and decreased the neurons sequentially
  <img width="646" alt="Screenshot 2023-05-27 at 11 33 59 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/4ee8d824-eeef-4514-925c-acc153b5e433">
  <img width="673" alt="Screenshot 2023-05-27 at 11 34 32 AM" src="https://github.com/Erink8/deep-learning-challenge/assets/119360371/071fc229-5df5-421f-87f4-58c6e0cec227">

