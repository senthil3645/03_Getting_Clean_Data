## Getting and Cleaning Data Project

Repository for the submission of the course project for the Johns Hopkins Getting and Cleaning Data course.

### Overview:
This project serves to demonstrate the collection and cleaning of a tidy data set that can be used for subsequent
analysis. A full description of the data used in this project can be found at [The UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

[The source data for this project can be found here.](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)

### Project Requirements:
The following is a summary description of the project instructions as highlighted in the Project instruction page.

You should create one R script called run_analysis.R that does the following. 
1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement. 
3. Uses descriptive activity names to name the activities in the data set
4. Appropriately labels the data set with descriptive activity names. 
5. Creates a second, independent tidy data set with the average of each variable for each activity and each subject.

### CodeBook.md
The CodeBook.md file provides information about the variables, data and transformation involved in tidying up the data.

### run_analysis.R
The run_analysis.R contains the R Code which reads and merges the training and test sets to create one data set, applies transformation rules specified in the project requirement and produces a tiday data set with the average of each variable for each acitvity and each subject.


### Running the Project Assignment Script submitted with this assignment
1.Import the run_analyis.R to the folder which has the unzipped folder(UCI HAR Dataset) of the Source data 
2.Update line 24 of run_analysis.R, to reflect the working directory. The submitted code has path specific to my local computer which contains the R Script and the unzipped Source data.
3. Run the R Script. The below text is the ouput from the R Console.The Script runs with out any errors.
4. The tidyData.txt files is created in the UCI HAR Dataset folder. The same has been uploaded during the Project submission along with the gitHub links. 


#####################################################################################
>source('~Big data/Coursera/Getting Clean Data/Project Assignment/run_analysis.R', echo=TRUE)
 
>Coursera Getting and Cleaning Dat .... [TRUNCATED] 

>1. Merge the training and the test sets to create one data set.
> 
>setting the working directory to the location where the UCI HAR Dataset was  .... [TRUNCATED] 

>Reading features,activity labels, subject train, X train, Y train  from files
>features     = read.table('./features.txt',header=FALSE); #imports .... [TRUNCATED] 

>activityType = read.table('./activity_labels.txt',header=FALSE);

>subjectTrain = read.table('./train/subject_train.txt',header=FALSE); 

>xTrain       = read.table('./train/x_train.txt',header=FALSE); 

>yTrain       = read.table('./train/y_train.txt',header=FALSE); 
>Assigning the column names to the data imported above
>colnames(activityType)  = c('activityId','activityType');

>colnames(subjectTrain)  = "subjectId";

>colnames(xTrain)        = features[,2]; 

>colnames(yTrain)        = "activityId";

>Creating the final training set from yTrain, subjectTrain, and xTrain
>trainingData = cbind(yTrain,subjectTrain,xTrain);

>Reading Subject, x test and y test from the supplied test data files
>subjectTest = read.table('./test/subject_test.txt',header=FALSE);  [TRUNCATED] 

>xTest       = read.table('./test/x_test.txt',header=FALSE); 

>yTest       = read.table('./test/y_test.txt',header=FALSE);

>Assigning the column names to the test data imported above -Similar to training data
>colnames(subjectTest) = "subjectId";

>colnames(xTest)       = features[,2]; 

>colnames(yTest)       = "activityId";

>Creating the final test from  xTest, yTest and subjectTest data
>testData = cbind(yTest,subjectTest,xTest);

>Combining the training and test data to create a final data set
>finalData = rbind(trainingData,testData);

>Creating a vector for the column names from the finalData, which will be used
>to select the desired mean() & stddev() columns
>colNames  = co .... [TRUNCATED] 

>2. Extract only the measurements on the mean and standard deviation for each measurement. 
> 
>Creating a logicalVector that contains TRUE valu .... [TRUNCATED] 

>Subsetting the finalData table based on the logicalVector to keep only desired columns
>finalData = finalData[logicalVector==TRUE];

>3. Use descriptive activity names to name the activities in the data set
> 
>Merging the finalData set with the acitivityType table to include  .... [TRUNCATED] 

>Updating the colNames vector to include the new column names after merge
>colNames  = colnames(finalData); 

>4. Appropriately labeling the data set with descriptive activity names. 
> 
>Cleaning up the variable names
>for (i in 1:length(colNames)) 
+  .... [TRUNCATED] 

>Reassigning the new descriptive column names to the finalData set
>colnames(finalData) = colNames;

>5. Create a second, independent tidy data set with the average of each variable for each activity and each subject. 
> 
>Creating a new table,  .... [TRUNCATED] 

>Summarizing the finalDataNoActivityType table to include just the mean of each variable for each activity and each subject
>tidyData    = aggrega .... [TRUNCATED] 

>Merging the tidyData with activityType to include descriptive acitvity names
>tidyData    = merge(tidyData,activityType,by='activityId',all.x=TRU .... [TRUNCATED] 

>Export the tidyData set, row.names=FALSE
>write.table(tidyData, './tidyData.txt',row.names=FALSE,sep='\t');
#####################################################################################

 


