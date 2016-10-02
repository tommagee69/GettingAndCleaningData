Codebook
--------
Variables
=========
dtTidy

Variable                                   | Comments
-------------------------------------------|-----------
Subject                                    |  subject identifier of volunteer (1-30)
ActivityName                               |  name ofactivity subject performed (LAYING,SITTING,STANDING,WALKING,WALKING_DOWNSTAIRS,WALKING_UPSTAIRS)
timeBodyAccelerometerMeanX                 |  mean of tBodyAcc-mean()-X
timeBodyAccelerometerMeanY                 |  mean of tBodyAcc-mean()-Y
timeBodyAccelerometerMeanZ                 |  mean of tBodyAcc-mean()-Z
timeBodyAccelerometerStdX                  |  mean of tBodyAcc-std()-X
timeBodyAccelerometerStdY                  |  mean of tBodyAcc-std()-Y
timeBodyAccelerometerStdZ                  |  mean of tBodyAcc-std()-Z
timeGravityAccelerometerMeanX              |  mean of tGravityAcc-mean()-X
timeGravityAccelerometerMeanY              |  mean of tGravityAcc-mean()-Y
timeGravityAccelerometerMeanZ              |  mean of tGravityAcc-mean()-Z
timeGravityAccelerometerStdX               |  mean of tGravityAcc-std()-X
timeGravityAccelerometerStdY               |  mean of tGravityAcc-std()-Y
timeGravityAccelerometerStdZ               |  mean of tGravityAcc-std()-Z
timeBodyAccelerometerJerkMeanX             |  mean of tBodyAccJerk-mean()-X
timeBodyAccelerometerJerkMeanY             |  mean of tBodyAccJerk-mean()-Y
timeBodyAccelerometerJerkMeanZ             |  mean of tBodyAccJerk-mean()-Z
timeBodyAccelerometerJerkStdX              |  mean of tBodyAccJerk-std()-X
timeBodyAccelerometerJerkStdY              |  mean of tBodyAccJerk-std()-Y
timeBodyAccelerometerJerkStdZ              |  mean of tBodyAccJerk-std()-Z
timeBodyGyroscopeMeanX                     |  mean of tBodyGyro-mean()-X
timeBodyGyroscopeMeanY                     |  mean of tBodyGyro-mean()-Y
timeBodyGyroscopeMeanZ                     |  mean of tBodyGyro-mean()-Z
timeBodyGyroscopeStdX                      |  mean of tBodyGyro-std()-X
timeBodyGyroscopeStdY                      |  mean of tBodyGyro-std()-Y
timeBodyGyroscopeStdZ                      |  mean of tBodyGyro-std()-Z
timeBodyGyroscopeJerkMeanX                 |  mean of tBodyGyroJerk-mean()-X
timeBodyGyroscopeJerkMeanY                 |  mean of tBodyGyroJerk-mean()-Y
timeBodyGyroscopeJerkMeanZ                 |  mean of tBodyGyroJerk-mean()-Z
timeBodyGyroscopeJerkStdX                  |  mean of tBodyGyroJerk-std()-X
timeBodyGyroscopeJerkStdY                  |  mean of tBodyGyroJerk-std()-Y
timeBodyGyroscopeJerkStdZ                  |  mean of tBodyGyroJerk-std()-Z
timeBodyAccelerometerMagMean               |  mean of tBodyAccMag-mean()
timeBodyAccelerometerMagStd                |  mean of tBodyAccMag-std()
timeGravityAccelerometerMagMean            |  mean of tGravityAccMag-mean()
timeGravityAccelerometerMagStd             |  mean of tGravityAccMag-std()
timeBodyAccelerometerJerkMagMean           |  mean of tBodyAccJerkMag-mean()
timeBodyAccelerometerJerkMagStd            |  mean of tBodyAccJerkMag-std()
timeBodyGyroscopeMagMean                   |  mean of tBodyGyroMag-mean()
timeBodyGyroscopeMagStd                    |  mean of tBodyGyroMag-std()
timeBodyGyroscopeJerkMagMean               |  mean of tBodyGyroJerkMag-mean()
timeBodyGyroscopeJerkMagStd                |  mean of tBodyGyroJerkMag-std()
frequencyBodyAccelerometerMeanX            |  mean of fBodyAcc-mean()-X
frequencyBodyAccelerometerMeanY            |  mean of fBodyAcc-mean()-Y
frequencyBodyAccelerometerMeanZ            |  mean of fBodyAcc-mean()-Z
frequencyBodyAccelerometerStdX             |  mean of fBodyAcc-std()-X
frequencyBodyAccelerometerStdY             |  mean of fBodyAcc-std()-Y
frequencyBodyAccelerometerStdZ             |  mean of fBodyAcc-std()-Z
frequencyBodyAccelerometerJerkMeanX        |  mean of fBodyAccJerk-mean()-X
frequencyBodyAccelerometerJerkMeanY        |  mean of fBodyAccJerk-mean()-Y
frequencyBodyAccelerometerJerkMeanZ        |  mean of fBodyAccJerk-mean()-Z
frequencyBodyAccelerometerJerkStdX         |  mean of fBodyAccJerk-std()-X
frequencyBodyAccelerometerJerkStdY         |  mean of fBodyAccJerk-std()-Y
frequencyBodyAccelerometerJerkStdZ         |  mean of fBodyAccJerk-std()-Z
frequencyBodyGyroscopeMeanX                |  mean of fBodyGyro-mean()-X
frequencyBodyGyroscopeMeanY                |  mean of fBodyGyro-mean()-Y
frequencyBodyGyroscopeMeanZ                |  mean of fBodyGyro-mean()-Z
frequencyBodyGyroscopeStdX                 |  mean of fBodyGyro-std()-X
frequencyBodyGyroscopeStdY                 |  mean of fBodyGyro-std()-Y
frequencyBodyGyroscopeStdZ                 |  mean of fBodyGyro-std()-Z
frequencyBodyAccelerometerMagMean          |  mean of fBodyAccMag-mean()
frequencyBodyAccelerometerMagStd           |  mean of fBodyAccMag-std()
frequencyBodyBodyAccelerometerJerkMagMean  |  mean of fBodyBodyAccJerkMag-mean()
frequencyBodyBodyAccelerometerJerkMagStd   |  mean of fBodyBodyAccJerkMag-std()
frequencyBodyBodyGyroscopeMagMean          |  mean of fBodyBodyGyroMag-mean()
frequencyBodyBodyGyroscopeMagStd           |  mean of fBodyBodyGyroMag-std()
frequencyBodyBodyGyroscopeJerkMagMean      |  mean of fBodyBodyGyroJerkMag-mean()
frequencyBodyBodyGyroscopeJerkMagStd       |  mean of fBodyBodyGyroJerkMag-std()

Transformations
===============
1. Data pulled in was split : subject, activity, and features (for both test, and trainn datasets) 
   Putting all of this into a single dataset was acheived by merging.
2. Dataset activity variable was merged with the activity lookup table to yield descriptive activity name.
3. Features were filtered to only show those matching xbar and std 
4. An average was added per group of subject, activity, and feature
6. Columsn were renamed, with a grepl funciton 
7. Dataset pushed to the "tidy.txt" file

Data
====
Copied from readme.txt
