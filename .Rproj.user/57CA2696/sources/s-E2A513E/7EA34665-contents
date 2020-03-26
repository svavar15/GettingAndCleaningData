library(dplyr)

#Reading in the dataset
features <- read.table("UCI HAR Dataset/features.txt", col.names = c("n","functions"))
activities <- read.table("UCI HAR Dataset/activity_labels.txt", col.names = c("code", "activity"))
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "subject")
x_test <- read.table("UCI HAR Dataset/test/X_test.txt", col.names = features$functions)
y_test <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "code")
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "subject")
x_train <- read.table("UCI HAR Dataset/train/X_train.txt", col.names = features$functions)
y_train <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "code")

#Merging training, test and subjct sets
train <- cbind(y_train, subject_train, x_train)
test <- cbind(y_test, subject_test, x_test)
merged_data <- rbind(train, test)


#Getting measurements on the mean and std
tidy_data <- merged_data %>% select(subject, code, contains("mean"), contains("std"))


# Change "code" column to the names from activites
tidy_data$code <- activities[tidy_data$code, 2]


#Appropriately label the data set
names(tidy_data)<-gsub("^t", "time", names(tidy_data))
names(tidy_data)<-gsub("^f", "frequency", names(tidy_data))
names(tidy_data)<-gsub("Acc", "Accelerometer", names(tidy_data))
names(tidy_data)<-gsub("BodyBody", "Body", names(tidy_data))
names(tidy_data)<-gsub("Gyro", "Gyroscope", names(tidy_data))
names(tidy_data)<-gsub("Mag", "Magnitude", names(tidy_data))


#Create second dataset, independent tidy data set with the average of each variable for each activity and each subject
library(plyr)

data<-aggregate(. ~subject + code, tidy_data, mean)
data<-data[order(data$subject,data$code),]

#Writing second to txt file
write.table(data, "new_tidy_data.txt", row.names = FALSE)

