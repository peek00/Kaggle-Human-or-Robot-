# [Project 1 - Kaggle: Facebook Human or Bots? [Late Submission]](https://github.com/peek00/Kaggle-Human-or-Robot-)
* Attained a private AUC score of 0.90595 and public AUC score of 0.86288
* Tried several machine learning methods and features creation
* Final submission used StratifiedShuffleSplit and RandomForestClassifier

## Overview ##
My first experiences with machine learning was via AI200 by Heicoders which used a subset of data from this competition as our capstone project. Following the end of the course, I decided to follow up and attempt to improve on the actual data set used here. As this was a late submission, my private AUC score placed me at approximiately 400 place in the leaderboard created at the time of the competition.

##Exploratory Data Sets ##

The competition provided three separate data sets, a "train_df", "test_df" and a "bids_df" which contained more details of the bids. Doing a groupby('bidder_id'), I found out that "bids_df" only contained the history of 6614 unique IDs while combined, "train_df" and "test_df" had 6713 unique IDs. 
