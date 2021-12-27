# [Project 1 - Kaggle: Facebook Human or Bots? [Late Submission]](https://github.com/peek00/Kaggle-Human-or-Robot-)
* Attained a private AUC score of 0.90595 and public AUC score of 0.86288
* Tried several machine learning methods and features creation
* Final submission used StratifiedShuffleSplit and RandomForestClassifier

## Overview 
My first experiences with machine learning was via AI200 by Heicoders which used a subset of data from this competition as our capstone project. Following the end of the course, I decided to follow up and attempt to improve on the actual data set used here. As this was a late submission, my private AUC score placed me at approximiately 400 place in the leaderboard created at the time of the competition.

#Exploratory Data Sets
The competition provided three separate data sets, a "train_df", "test_df" and a "bids_df" which contained more details of the bids. Doing a groupby('bidder_id'), I found out that "bids_df" only contained the history of 6614 unique IDs while combined, "train_df" and "test_df" had 6713 unique IDs. I realised that there were accounts created that had not bidded before hence their details were not present in "bids_df" and decided to drop them as without any bids, there was no way to tell if they were bots or humans and they would further dilute the data set.

#What makes a bot a bot?
Looking at the limited features provided at first, I tried to think of behaviours or reasons that a bot would be used. Referencing some of the other past competitors' approach, I deduced that a bot might
* Used a higher than average number of devices
* Accessed via multiple different IP addresses
* Be submitting bids from multiple countries
* Bid at regular intervals
* Having more bids than average of a human user

#Feature Engineering
As this was my first time doing feature engineer, the features engineered were arguably quite basic but made sense to me. In total, the features I managed to generate from the information provided were 
1. Median Time (in relationship to the time the bids were placed)
2. Standard Deviation (of each unique bidder)
3. Mean Time (of each unique bidder)
4. Total Bids Placed (of each unique bidder)
5. Unique Auctions Entered (of each unique bidder)
6. Mean Bids per Auction (of each unique bidder)
![Corr Heatmap](https://user-images.githubusercontent.com/95530032/147402346-1056bfd8-d207-4790-b341-5c6ec97d668c.PNG)
Looking at the heatmap, there were no real features that stood out particularly so it took a bit of trail and error latter on to figure out which features gave the highest AUC. Using 9 ['auction','unique_auctions','country','mean_bids_per_auction','device','ip','time','std'] features, 3 of which were engineered provided the best results.

#Machine Learning Model
The models I tried using on this were XGBoost RandomForestClassifier, sklearn's RandomForestClassifier, CatBoostClassifier, SVM and for the train test split I tried sklearn's KFold and StratifiedShuffleSplit. The combination that provided the best results were sklearn's RandomForestClassifier(criterion = 'entropy') with StratifiedShuffleSplit. 

#Takeaways
As these was my first machine learning project, the EDA portion was guided by instructors and the selection of models and feature engineering was left to us. I looked up the methodology of several of the previous competitors and tried to implement what I could from there. While the selection of the models and train test split method was guided by trial and error, I hope to better understand the intricies of each of them and better implement them in the future.

