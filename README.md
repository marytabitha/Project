# Project
Project for Getting and Cleaning Data course
project <- unzip("C:/Users/Dorcas/Documents/Getting and Cleaning Data/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip")unzip("C:/Users/Dorcas/Documents/Getting and Cleaning Data/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip")
assign1 <- read.table("./UCI HAR Dataset/activity_labels.txt")
head(assign1)
print(assign1)

assign2 <- read.table("./UCI HAR Dataset/features.txt")
print(assign2)
head(assign2)

assign3 <- read.table("./UCI HAR Dataset/features_info.txt", sep = ",", quote = "", row.names = TRUE)
assign3 <- read.csv("./UCI HAR Dataset/features_info.txt")
head(assign3)#failed

assign4 <-read.table("./UCI HAR Dataset/README.txt")
head(assign4)#failed

assign5 <-read.table("./UCI HAR Dataset/test/Inertial Signals/body_acc_x_test.txt")
head(assign5)

assign6 <-read.table("./UCI HAR Dataset/test/Inertial Signals/body_acc_x_test.txt")
head(assign6)
#Reading the data
test <- get.data("C:/Users/Dorcas/Documents/Getting and Cleaning Data/UCI HAR Dataset", "test") 
train <- get.data("C:/Users/Dorcas/Documents/Getting and Cleaning Data/UCI HAR Dataset", "train") 

#join the data
alldata <- rbind(test, train)
print(alldata)

#Reshape the data via melting
alldatalong <- melt(alldata, id = c("subject", "activity"))
alldatalong

#Decasting
alldatawide <- dcast(alldatalong, subject + activity ~ variable, mean)
alldatawide

#clean data
alldataclean <- alldatawide 
alldataclean

#save clean data
cleandata <- file.path("C:/Users/Dorcas/Documents/Getting and Cleaning Data/UCI HAR Dataset", clean.file) 
write.table(alldataclean, cleandata, row.names = FALSE, quote = FALSE) 
run.analysis("C:/Users/Dorcas/Documents/Getting and Cleaning Data/Project/UCI HAR Dataset/test/X_test.txt")
