# CodeBook

## Data source

The dataset was provided by the assignment and can be download it here: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
Upon inspection the zip file contained several folders and files related to the experiments ran on different subjects to collect metrics when performing the following activities:

1. WALKING
1. WALKING_UPSTAIRS
1. WALKING_DOWNSTAIRS
1. SITTING
1. STANDING
1. LAYING


## Files 

The following files below contain the train and test data collected for each of the subjects for all activities:

* '/train/X_train.txt'
* '/train/y_train.txt'
* '/train/subject_train.txt' 
* '/test/X_test.txt'
* '/test/y_test.txt'
* '/test/subject_test.txt'

The script will import each file into its own variable and also read the file with all 6 activities found in the root directory of the extracted zip file.

## Features 

The features included in these files come from accelerometer and gyroscope sensors, includes 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz

For this assignment we were asked to only select measurements which included Mean or STD (lower or upper case) within the variable name.

Resulting in the following 86 features below:

1. tBodyAcc.mean...X
1. tBodyAcc.mean...Y
1. tBodyAcc.mean...Z
1. tGravityAcc.mean...X
1. tGravityAcc.mean...Y
1. tGravityAcc.mean...Z
1. tBodyAccJerk.mean...X
1. tBodyAccJerk.mean...Y
1. tBodyAccJerk.mean...Z
1. tBodyGyro.mean...X
1. tBodyGyro.mean...Y
1. tBodyGyro.mean...Z
1. tBodyGyroJerk.mean...X
1. tBodyGyroJerk.mean...Y
1. tBodyGyroJerk.mean...Z
1. tBodyAccMag.mean..
1. tGravityAccMag.mean..
1. tBodyAccJerkMag.mean..
1. tBodyGyroMag.mean..
1. tBodyGyroJerkMag.mean..
1. fBodyAcc.mean...X
1. fBodyAcc.mean...Y
1. fBodyAcc.mean...Z
1. fBodyAcc.meanFreq...X
1. fBodyAcc.meanFreq...Y
1. fBodyAcc.meanFreq...Z
1. fBodyAccJerk.mean...X
1. fBodyAccJerk.mean...Y
1. fBodyAccJerk.mean...Z
1. fBodyAccJerk.meanFreq...X
1. fBodyAccJerk.meanFreq...Y
1. fBodyAccJerk.meanFreq...Z
1. fBodyGyro.mean...X
1. fBodyGyro.mean...Y
1. fBodyGyro.mean...Z
1. fBodyGyro.meanFreq...X
1. fBodyGyro.meanFreq...Y
1. fBodyGyro.meanFreq...Z
1. fBodyAccMag.mean..
1. fBodyAccMag.meanFreq..
1. fBodyBodyAccJerkMag.mean..
1. fBodyBodyAccJerkMag.meanFreq..
1. fBodyBodyGyroMag.mean..
1. fBodyBodyGyroMag.meanFreq..
1. fBodyBodyGyroJerkMag.mean..
1. fBodyBodyGyroJerkMag.meanFreq..
1. angle.tBodyAccMean.gravity.
1. angle.tBodyAccJerkMean..gravityMean.
1. angle.tBodyGyroMean.gravityMean.
1. angle.tBodyGyroJerkMean.gravityMean.
1. angle.X.gravityMean.
1. angle.Y.gravityMean.
1. angle.Z.gravityMean.
1. tBodyAcc.std...X
1. tBodyAcc.std...Y
1. tBodyAcc.std...Z
1. tGravityAcc.std...X
1. tGravityAcc.std...Y
1. tGravityAcc.std...Z
1. tBodyAccJerk.std...X
1. tBodyAccJerk.std...Y
1. tBodyAccJerk.std...Z
1. tBodyGyro.std...X
1. tBodyGyro.std...Y
1. tBodyGyro.std...Z
1. tBodyGyroJerk.std...X
1. tBodyGyroJerk.std...Y
1. tBodyGyroJerk.std...Z
1. tBodyAccMag.std..
1. tGravityAccMag.std..
1. tBodyAccJerkMag.std..
1. tBodyGyroMag.std..
1. tBodyGyroJerkMag.std..
1. fBodyAcc.std...X
1. fBodyAcc.std...Y
1. fBodyAcc.std...Z
1. fBodyAccJerk.std...X
1. fBodyAccJerk.std...Y
1. fBodyAccJerk.std...Z
1. fBodyGyro.std...X
1. fBodyGyro.std...Y
1. fBodyGyro.std...Z
1. fBodyAccMag.std..
1. fBodyBodyAccJerkMag.std..
1. fBodyBodyGyroMag.std..
1. fBodyBodyGyroJerkMag.std..

## Transforrmations

The run_analysis.R script performsn the following task/transformations:

1. Merges the training and the test sets to create one data set.
    Variable final_data_merge is the result of performing a cbind() between subjects,y_data, and x_data 
1. Extracts only the measurements on the mean and standard deviation for each measurement.
    Select only columns needed by picking subject_id, activity_name and any columns that contain "mean" and "std".  Used the dyplr function select() function to achieve this.
1. Uses descriptive activity names to name the activities in the data set by merging the activity list with the test and train data
    Use the dyplr function merge() to join the final_data_merge data table with the activity data table through the activity_id
1. Appropriately labels the data set with descriptive variable names.
    Made the names of the variables readable by translating acronyms to full words
1. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
    Grouped and summarized the data with dyplr functions group_by and summarise_all
