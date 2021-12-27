# [Project 1 - Kaggle: Facebook Human or Bots? [Late Submission]](https://github.com/peek00/Kaggle-Human-or-Robot-)
* Attained a private AUC score of 0.90595 and public AUC score of 0.86288
* Tried several machine learning methods and features creation
* Final submission used StratifiedShuffleSplit and RandomForestClassifier
![Kaggle](https://user-images.githubusercontent.com/95530032/147438128-44dc819e-f977-4d68-b09a-f56024c2c242.PNG)


## Overview 
My first experiences with machine learning was via AI200 by Heicoders which used a subset of data from this competition as our capstone project. Following the end of the course, I decided to follow up and attempt to improve on the actual data set used here. As this was a late submission, my score was not updated on the leaderboard but my private AUC score placed me at approximiately 400 place.

## Exploratory Data Sets
The data was relatively clean. The main step I took was to remove the unique IDs who did not have a bidding history as without any bids, there was no way to tell if they were bots or humans and they would further dilute the data set. Afterwards, there was minimal joining to be done.

The train set provided had only 103 bots and 1881 humans, making this an imbalanced dataset. This prompted me to use StratifiedKFold to generate the train-test splits to account for the imbalance.

Looking at the available features and their correlation to the outcome, I decided to do some feature engineering. 

## What makes a bot a bot?
Referencing some of the other past competitors' approach, I deduced that a bot might
 
* Used a higher than average number of devices
* Accessed via multiple different IP addresses
* Be submitting bids from multiple countries
* Bid at regular intervals
* Having more bids than average of a human user

## Feature Engineering
In total, the features I managed to generate from the information provided were 
1. Median Time (in relationship to the time the bids were placed)
2. Standard Deviation (of each unique bidder)
3. Mean Time (of each unique bidder)
4. Total Bids Placed (of each unique bidder)
5. Unique Auctions Entered (of each unique bidder)
6. Mean Bids per Auction (of each unique bidder)

![Corr Barchart](https://user-images.githubusercontent.com/95530032/147429417-528b9af3-c073-4a3f-9f92-77c500bfb28e.png)

I then did another correlation check, and there were no particular features that stood out predominantly. I experimented with subsets of features. Using 9 ['auction','unique_auctions','country','mean_bids_per_auction','device','ip','time','std'] features, 3 of which were engineered provided the best results in terms of AUC.


## Machine Learning Model
The models I tried using on this were XGBoost RandomForestClassifier, sklearn's RandomForestClassifier, CatBoostClassifier, SVM and for the train test split I tried sklearn's KFold and StratifiedShuffleSplit. The combination that provided the best results were sklearn's RandomForestClassifier(criterion = 'entropy') with StratifiedShuffleSplit. 

## Takeaways
As these was my first machine learning project, the EDA portion was guided by instructors and the selection of models and feature engineering was left to us. I looked up the methodology of several of the previous competitors and tried to implement what I could from there. While the selection of the models and train test split method was guided by trial and error, I hope to better understand the intricies of each of them and better implement them in the future.

