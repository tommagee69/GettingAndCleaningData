# run_analysis.R
# Q4 Assignment of the Data Science class
library(data.table)
library(dplyr)

path <- getwd()
## Getting the file  & then unzip'ing the file
##
url <- 'https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip'
f <- 'Dataset.zip'
if(!file.exists(f)) {
  download.file(url,f)
}
d <- 'UCI HAR Dataset'
if(!file.exists(d)) {
  unzip(f)
}

##  Next we read the data into R
dtSubjTrain <- data.table(read.table(file.path(path, d, 'train', 'subject_train.txt')))
dtSubjTest <- data.table(read.table(file.path(path, d, 'test', 'subject_test.txt')))
dtSubj <- rbind(dtSubjTrain, dtSubjTest)
names(dtSubj) <- c('Subject')
remove(dtSubjTrain,dtSubjTest)

## read activities continued, and a cleaning up of the 'Names'
dtActTrain <- data.table(read.table(file.path(path, d, 'train','Y_train.txt')))
dtActTest <- data.table(read.table(file.path(path,d,'test','Y_test.txt')))
dtAct <- rbind(dtActTrain,dtActTest)
names(dtAct) <- c('Activity')
remove(dtActTrain,dtActTest)
dtSubj <- cbind(dtSubj,dtAct)
remove(dtAct)

## read feature data
dtTrain <- data.table(read.table(file.path(path,d,'train','X_train.txt')))
dtTest <- data.table(read.table(file.path(path,d,'test','X_test.txt')))
dt <- rbind(dtTrain,dtTest)
remove(dtTrain,dtTest)

## Q1 Merging data (train + test) into one table
dt <- cbind(dtSubj,dt)
#set key to subject/activity
setkey(dt,Subject,Activity)
remove(dtSubj)

## Q2 Pulling out the standard deviation and the mean , pieces
dtFeats <- data.table(read.table(file.path(path,d,'features.txt'))) 
names(dtFeats) <- c('ftNum','ftName')
dtFeats <- dtFeats[grepl("mean\\(\\)|std\\(\\)",ftName)]
dtFeats$ftCode <- paste('V', dtFeats$ftNum, sep = "")

#select only the filtered features (with=FALSE to dynamically pick cols)
dt <- dt[,c(key(dt), dtFeats$ftCode),with=F]

## Changing the name of a column
setnames(dt, old=dtFeats$ftCode, new=as.character(dtFeats$ftName))

## Q3 Reaplacing/ ammending the activity names
dtActNames <- data.table(read.table(file.path(path, d, 'activity_labels.txt')))
names(dtActNames) <- c('Activity','ActivityName')
dt <- merge(dt,dtActNames,by='Activity')
remove(dtActNames)
#add activityname as a key

## merge in ftName
dtTidy <- dt %>% group_by(Subject, ActivityName) %>% summarise_each(funs(mean))
dtTidy$Activity <- NULL

## Q4 Labelling the datasets with more descriptive names : e.g., replacing anything beginning with t --> 'time' etc., 
names(dtTidy) <- gsub('^t', 'time', names(dtTidy))
names(dtTidy) <- gsub('^f', 'frequency', names(dtTidy))
names(dtTidy) <- gsub('Acc', 'Accelerometer', names(dtTidy))
names(dtTidy) <- gsub('Gyro','Gyroscope', names(dtTidy))
names(dtTidy) <- gsub('mean[(][)]','Mean',names(dtTidy))
names(dtTidy) <- gsub('std[(][)]','Std',names(dtTidy))
names(dtTidy) <- gsub('-','',names(dtTidy))

## Q5 reating a secondary dataset with the average of each variable for each activity and subject
write.table(dtTidy, file.path(path, 'tidy.txt'), row.names=FALSE)
