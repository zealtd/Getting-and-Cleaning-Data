### Introduction

The purpose of this project is to demonstrate my skills to collect, work with, and clean a data set. The goal is to prepare a tidy data that can be used for later analysis. In this project, the following information are submitted. 
1) a tidy data to the Coursera website, 
2) a link to a Github repository with my script for performing the analysis, 
3) a code book called CodeBook.md that describes the variables, the data, and any transformations or work that I have
   performed to clean up the data, 
4) a README.md in the repo with my scripts which is this document. 

This document will explain how all of the scripts work and how they are connected.  

The data that we are using for this project represents data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained: 

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 

Here are the data for the project: 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

From this link, we downloaded 7 datasets which are:

1) X_train.txt
2) y_train.txt
3) X_test.txt
4) y_test.txt
5) subject_train.txt
6) subject_test.txt
7) features.txt


We have created one R script called run_analysis.R that does the following steps.  

(1) Merges the training and the test sets to create one data set.

x_test<-read.table("X_test.txt")            
y_test<-read.table("y_test.txt")            
x_train<-read.table("X_train.txt")          
y_train<-read.table("y_train.txt")          
trainsub<-read.table("subject_train.txt")   
testsub<-read.table("subject_test.txt")     
features<-read.table("features.txt")        
names(x_test)<-as.character(features[,-1])
names(y_test)<-c("activity")
names(x_train)<-as.character(features[,-1])
names(y_train)<-c("activity")
names(trainsub)<-c("subject")
names(testsub)<-c("subject")
train <- cbind(y_train,trainsub,x_train)
test <- cbind(y_test,testsub,x_test)
dat<- rbind(train,test)

(2) Extracts only the measurements on the mean and standard deviation for each measurement. 

yy<- rbind(y_train,y_test)
subb<- rbind(trainsub,testsub)
xx<- rbind(x_train,x_test)
name1<-grep("mean",as.character(features[,-1]))
name2<-grep("std",as.character(features[,-1]))
x3<-xx[,name1]
x4<-xx[,name2]
xxx<-cbind(x3,x4)
dat2<-cbind(yy,subb,xxx)

(3) Uses descriptive activity names to name the activities in the data set.

dat2$activity[dat2$activity == 6] <- "LAYING"
dat2$activity[dat2$activity == 5] <- "STANDING"
dat2$activity[dat2$activity == 4] <- "SITTING"
dat2$activity[dat2$activity == 3] <- "WALKING_DOWNSTAIRS"
dat2$activity[dat2$activity == 2] <- "WALKING_UPSTAIRS"
dat2$activity[dat2$activity == 1] <- "WALKING"

(4) Appropriately labels the data set with descriptive variable names. 

names(dat2)<-tolower(names(dat2))
names(dat2)<-gsub("\\(","",names(dat2))
names(dat2)<-gsub("\\)","",names(dat2))
names(dat2)<-gsub("-"," ",names(dat2))
names(dat2)<-gsub("bodybody","body",names(dat2))
names(dat2)<-gsub("tbody","time body",names(dat2))
names(dat2)<-gsub("tgrav","time grav",names(dat2))
names(dat2)<-gsub("fbody","frequency body",names(dat2))


(5) From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each     activity and each subject.

require(plyr)
library(reshape2)
dat3<-ddply(dat2, .(activity,subject), numcolwise(mean))
write.table(dat3,file="tidydata.txt",row.name=FALSE)
data <- read.table("tidydata.txt", header = TRUE)
View(data)




A tidy data set created in step 5 was uploaded as a txt file created with write.table() using row.name=FALSE 
to the Coursera web site.

A code book called CodeBook.md that describes the variables, the data, and any transformations or work that I have
performed to clean up the data has been included in this repo as well.

One R script called run_analysis.R which was used to create the final tidy dataset has been included in this repo.
