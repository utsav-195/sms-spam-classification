# Text Message Classification into Spam or Ham
How often have we come across messages saying we have won a trip to Hawai or won a million dollar or won a cash prize.
This form of scam through text messages which are genrally spam messages is called smishing.
A lot of times they ask us to fill in forms and ask our personal information or SSN number which is really fishy or bound to be a fraud.
The goal of this project is to use Data Science to accurately classify whether a message is spam or not.

## Data
The dataset we used to build our model is from the UIC repostiory. The link to the dataset is [here](https://archive.ics.uci.edu/ml/datasets/sms+spam+collection).
The dataset has 2 columns, the text messages and the label.
The dataset contains 5572 text messages which are appropriately labelled ham and spam.
The dataset is imbalanced in nature with 4825 instances of ham class and 747 instances of spam class.
The dataset contains words which are in a noisy form and colloquial in nature with respect to daily textual conversations between people.
Hence the dataset comprises data from the informal domain space and a significant amount of data pre-processing needs to be done for our modelling part.

## Data Preparation
The data is a bunch of text messages which are personal conversations as well as spam texts.
So, we pre-processed the data by by performing the following steps:
 - Converted the messages to lowercase to capture the unique tokens and not differentiate between alphabet cases.
 - The messages contained phone numbers, email addresses, http links, money symbols, and other numbers which were substituted by a fixed string. Eg. xyz@abc.com was replaced with “emailaddr” using regex.
 - Implemented regular expressions to remove punctuations and replace them with whitespace.
 - To correct typos, a spell corrector was implemented which basically decides the best word based on edit distance. Pyspellchecker library was used for the same.
 - Implemented stemming on words to bring them to their root form.
 - The important words are the tokens other than the stop words. So, we removed the stopwords from the messages as they do not act as the differentiating factor.
 - Finally, implemented CountVectorizer and TfIdf Vectorizer for the data modeling exercise.


## Data Exploration
We observed that the spam messages are generally longer than normal conversations. We also developed wordclouds for both the classes to observe which words occur more frequently in each class.
![screenshots/capture3.png](screenshots/plot_images.png?raw=true)
![screenshots/capture4.png](screenshots/plot_images.png?raw=true)
![screenshots/capture5.png](screenshots/plot_images.png?raw=true)
![screenshots/capture6.png](screenshots/plot_images.png?raw=true)

## Execution
The project has a jupyter notebook [sms_spam_ham_classification.ipynb](https://github.com/utsav-195/sms-spam-ham-classification/blob/main/sms_spam_ham_classification.ipynb) which is used for the implementation of this project.
Run each cell and you can observe the output of the commands.

## Results
The results of the TFIDF Vectorized data:

| Model | Accuracy | F1 score (ham) | F1 score (spam) |
| --- | --- | --- | --- |
| Naive Bayes | 84.03 | 91.10 | 58.73 |
| Decision Tree using entropy | 97.30 | 98.45 | 89.60 | 
| Decision Tree using gini | 97.36 | 98.48 | 90 | 
| SVM with linear | **98.74** | **99.27** | **95.10** |
The SVM classifier with linear kernel on TFIDF data gives the best results.

## Report
For detailed report go [here](https://github.com/utsav-195/sms-spam-ham-classification/blob/main/Final%20project%20report.pdf) and for presentation slides go [here](https://github.com/utsav-195/sms-spam-ham-classification/blob/main/IDS%20Presentation.pdf).

## Reference
https://github.com/mohitgupta-omg/Kaggle-SMS-Spam-Collection-Dataset-
