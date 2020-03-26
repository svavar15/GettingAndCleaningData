# Getting and Cleaning Data assignment

This file covers how the data was transformed into a tidy data set.

We have run_analysis.R

By running the script we are reading a data set.

Next we are merging the data sets together. 
    1. We are using cbind to merge all train data sets together 
    2. We are using cbind to merge all test data sets together
    3. Then we use rbind to merge the two sets together.

Next we are getting mean and std measurements
    1. There we are using select to select columns that contain mean and std

Then we changing the second column and adding the right activity in the all rows of that column (column[2])

Next we are fixing some of the typos. 
    1. We use ^t and ^f to check if column start with t or f and we replace them with time and frequency.
    2. The same we do for some of the words in the columns.

Creating another data set
We use the plyr library
    We use aggregate to for this data set.
    
Last, we write the new dataset to .txt file


