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
