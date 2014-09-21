### Introduction

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.


### Data Set Information:

The data were collected from the accelerometers from the Samsung Galaxy S smartphone. 

Here are the data for the project: 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

From this link, we downloaded 7 datasets which are:

1) X_train.txt             dimension = 7352x561
2) y_train.txt             dimension = 7352x1
3) X_test.txt              dimension = 2947x561
4) y_test.txt              dimension = 2947x1
5) subject_train.txt       dimension = 7352x1
6) subject_test.txt        dimension = 2947x1
7) features.txt            dimension = 561x2


The final tidy dataset was created following these 5 steps.
(1) Merges the training and the test sets to create one data set.
(2) Extracts only the measurements on the mean and standard deviation for each measurement. 
(3) Uses descriptive activity names to name the activities in the data set
(4) Appropriately labels the data set with descriptive variable names. 
(5) From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.


### Feature Selection

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean
tBodyAccMean
tBodyAccJerkMean
tBodyGyroMean
tBodyGyroJerkMean

The set of variables that were estimated from these signals are: 

mean(): Mean value
std(): Standard deviation
meanFreq(): Weighted average of the frequency components to obtain a mean frequency




### Transformation Summary

We have transformed the activity field to have descriptive names such as "walking" and "sitting".
We have changed the feature variables to lower case.
We have removed the parentheses "(" ")" within the feature variables.
We have replaced the hyphen "-" by a blank space within the feature variables.
We have corrected some misspellings, "bodybody", within the feature variables.
We have changed the short symbol "t" to "time" within the feature variables.
We have changed the short symbol "f" to "frequency" within the feature variables.
All these are performed in order to have more descriptive variable names.

We extracts only the measurements on the mean and standard deviation for each measurement. 
Thus, there are only 81 variables in the final tidy dataset.

 [1] "activity"                           "subject"                           
 [3] "time bodyacc mean x"                "time bodyacc mean y"               
 [5] "time bodyacc mean z"                "time gravityacc mean x"            
 [7] "time gravityacc mean y"             "time gravityacc mean z"            
 [9] "time bodyaccjerk mean x"            "time bodyaccjerk mean y"           
[11] "time bodyaccjerk mean z"            "time bodygyro mean x"              
[13] "time bodygyro mean y"               "time bodygyro mean z"              
[15] "time bodygyrojerk mean x"           "time bodygyrojerk mean y"          
[17] "time bodygyrojerk mean z"           "time bodyaccmag mean"              
[19] "time gravityaccmag mean"            "time bodyaccjerkmag mean"          
[21] "time bodygyromag mean"              "time bodygyrojerkmag mean"         
[23] "frequency bodyacc mean x"           "frequency bodyacc mean y"          
[25] "frequency bodyacc mean z"           "frequency bodyacc meanfreq x"      
[27] "frequency bodyacc meanfreq y"       "frequency bodyacc meanfreq z"      
[29] "frequency bodyaccjerk mean x"       "frequency bodyaccjerk mean y"      
[31] "frequency bodyaccjerk mean z"       "frequency bodyaccjerk meanfreq x"  
[33] "frequency bodyaccjerk meanfreq y"   "frequency bodyaccjerk meanfreq z"  
[35] "frequency bodygyro mean x"          "frequency bodygyro mean y"         
[37] "frequency bodygyro mean z"          "frequency bodygyro meanfreq x"     
[39] "frequency bodygyro meanfreq y"      "frequency bodygyro meanfreq z"     
[41] "frequency bodyaccmag mean"          "frequency bodyaccmag meanfreq"     
[43] "frequency bodyaccjerkmag mean"      "frequency bodyaccjerkmag meanfreq" 
[45] "frequency bodygyromag mean"         "frequency bodygyromag meanfreq"    
[47] "frequency bodygyrojerkmag mean"     "frequency bodygyrojerkmag meanfreq"
[49] "time bodyacc std x"                 "time bodyacc std y"                
[51] "time bodyacc std z"                 "time gravityacc std x"             
[53] "time gravityacc std y"              "time gravityacc std z"             
[55] "time bodyaccjerk std x"             "time bodyaccjerk std y"            
[57] "time bodyaccjerk std z"             "time bodygyro std x"               
[59] "time bodygyro std y"                "time bodygyro std z"               
[61] "time bodygyrojerk std x"            "time bodygyrojerk std y"           
[63] "time bodygyrojerk std z"            "time bodyaccmag std"               
[65] "time gravityaccmag std"             "time bodyaccjerkmag std"           
[67] "time bodygyromag std"               "time bodygyrojerkmag std"          
[69] "frequency bodyacc std x"            "frequency bodyacc std y"           
[71] "frequency bodyacc std z"            "frequency bodyaccjerk std x"       
[73] "frequency bodyaccjerk std y"        "frequency bodyaccjerk std z"       
[75] "frequency bodygyro std x"           "frequency bodygyro std y"          
[77] "frequency bodygyro std z"           "frequency bodyaccmag std"          
[79] "frequency bodyaccjerkmag std"       "frequency bodygyromag std"         
[81] "frequency bodygyrojerkmag std"    




