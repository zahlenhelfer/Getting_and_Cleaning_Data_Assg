codebook
========================
You can find the original data under: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

The Original description of the data is under: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

The run_analysis.R script in this repo does the following steps to clean up the data:
* it merges the training and test sets to  one data set, this namely train/X_train.txt with test/X_test.txt. Results in a 10299 by 561 data frame. The same like in the original description, "Number of Instances: 10299" and "Number of Attributes: 561". The train/subject_train.txt with test/subject_test.txt is the result of which a 10299 by 1 dataframe with IDs. The train/y_train.txt with test/y_test.txt is the result of which is a 10299 by 1 data frame with activity IDs.

* It will read the features.txt and extracts the measurements on the mean and standard deviation. It results in a 10299 by 66 data frame, because only 66 out of 561 attributes are measurements on the mean and standard deviation. All measurements appear to be floating point numbers in the range from -1 to +1.

* It reads the activity_labels.txt and applies descriptive activity names to name the activities in the data set:
        walking
        walkingupstairs
        walkingdownstairs
        sitting
        standing
        laying

* The script also labels the data set with descriptive names. Every feature name , Attributes and activity names are converted to lower case. All underscores and brackets  are removed. Then it merges the 10299 by 66 data frame containing features with 10299 by 1 data frames containing activity labels and subject IDs. The result is saved as merged_clean_data.txt. A 10299 by 68 data frame where the first column contains subject IDs, the second column activity names, and the last 66 columns are measurements. Subject IDs are integers between 1 and 30 inclusive. The names of the attributes are similar to the following:
        tbodyacc-mean-x 
        tbodyacc-mean-y 
        tbodyacc-mean-z 
        tbodyacc-std-x 
        tbodyacc-std-y 
        tbodyacc-std-z 
        tgravityacc-mean-x 
        tgravityacc-mean-y

* At the end, the script create a second fully independent data set that is tidy. It has the average of each measurement for each activity and each subject. The result is saved as ds_with_the_averages.txt. A 180 by 68 data frame, where as before, the first column contains the subject IDs. A second column contains activity names. Plus the averages for each of the 66 attributes are in columns 3...68. There are 30 subjects and 6 activities = 180 rows in this data set with averages.
